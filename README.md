# Sample Pure Vanilla JS with Okta AuthJS SDK

Very simple pure vanilla javascript example of using the Okta AuthJS SDK.

## Pre-requirements

* [npx](https://www.npmjs.com/package/npx)
* [serve](https://www.npmjs.com/package/serve) via npx
* Okta Org - if you don't have an existing org, register for [Okta Developer Editions](https://developer.okta.com/signup/)

## Quick-start

An OpenID Connect application was create on your Okta org. Using the following instructions:

* Instructions for creating an application, instructions [here](https://help.okta.com/en/prod/okta_help_CSH.htm#ext_Apps_App_Integration_Wizard-oidc)
* Assigned one user to the application, instructions [here](https://help.okta.com/en/prod/okta_help_CSH.htm#ext-apps-page-show-application-embed-links)
* Update your Okta's `Trusted Origins` for your application. To do this, follow the steps found under the "Trusted Origins tab" section in our [API Security help page](https://help.okta.com/en/prod/okta_help_CSH.htm#Security_API)

Update the `index.html` file with your `Okta Org URL`, `CLIENT_ID`, `REDIRECT_URI`, and `ISSUER` from the above instructions.

```javascript
    // Bootstrap the AuthJS Client
    const authClient = new OktaAuth({
        // Org URL
        url: 'https://{OKTA_ORG_URL}',
        // OpenID Connect APP Client ID
        clientId: '{OKTA_OIDC_CLIENT_ID}',
        // Trusted Origin Redirect URI
        redirectUri: 'http://localhost:8080/login/callback',
        // Issuer
        issuer: 'https://{OKTA_ORG_URL}/oauth2/default',
    });
```

Run it, using the `serve` and custom properties defined in `serve.json` file.

```bash
npx serve -l 8080 -c serve.json
```

Navigate to `http://localhost:8080` with your prefer Browser. You will prompted for Username and then Password. Use an user that exist in that Okta Org that you have configured. Using Browser dev tool, ie (`Inspect`) after a successful sign in, the console should identify the `id_token` that was minted by Okta Authorization Server.

## Author

* [@Noi Narisak](https://github.com/noinarisak)

## Inspiration

* [Okta AuthJS SDK Guide](https://developer.okta.com/code/javascript/okta_auth_sdk/)
