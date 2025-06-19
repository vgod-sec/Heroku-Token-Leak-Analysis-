#  Heroku API Token Exposure from JavaScript File (Educational Write-Up)

> ⚠️ **Disclaimer**  
> This research is shared for educational purposes only. The domain where this was discovered was **not part of a public bug bounty program**, and no exploitation was performed. All sensitive information is **redacted or simulated** in accordance with ethical guidelines.

## Summary

While performing passive recon on a public domain, I discovered a **Heroku API Bearer Token** exposed in a JavaScript file. This token was tested safely using a read-only Heroku API endpoint and returned valid metadata — indicating an active credential.


## 🛠️ Tools Used

- `SecretFinder` – JS secret scanning tool  
- `curl` – For sending safe API test requests  
- `jq` – Optional tool to pretty-print JSON


## 🔍 Discovery Walkthrough

### 1. Scan JS File for Secrets
```bash
python3 SecretFinder.py -i https://target-domain.com/js/app.js -o cli

2 Simulate api validation (Reducted)
curl -X GET https://api.heroku.com/account \
  -H "Accept: application/vnd.heroku+json; version=3" \
  -H "Authorization: Bearer HRKU_xxxxxxxxxxxxxx"



## 🧯 Mitigation (Short)

- ❌ Never hard-code secrets in JavaScript or frontend code
- ✅ Use environment variables and server-side token handling
- 🔁 Regularly rotate and revoke API tokens
- 🧪 Scan code with tools like `gitleaks`, `truffleHog`, or `SecretFinder`
- 🔐 Store secrets using vaults (e.g., AWS Secrets Manager, HashiCorp Vault)
- 📉 Minify and obfuscate production JS files
- 🔍 Monitor logs and APIs for suspicious access
- 🛡️ Enforce 2FA and least privilege for developer accounts







## 🚫 License

This project is licensed under **All Rights Reserved**.

No part of this repository (code, content, or images) may be copied, reproduced, distributed, or modified without the author's explicit written permission.
