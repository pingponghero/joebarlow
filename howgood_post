"""
Submit application to HowGood API
Instructions: https://howgood-apply-api.howgood.workers.dev/how-to/
"""

import hashlib, hmac, json, requests

secret = "hg2026_python_engineer@!"
endpoint = "https://howgood-apply-api.howgood.workers.dev/apply"

payload = {
    "name": "Joe Barlow",
    "email": "joebarlow222@gmail.com",
    "resume": "https://pingponghero.github.io/joebarlow/resume.pdf",
    "location": "Asheville, NC",
    "linkedin": "https://www.linkedin.com/in/joe-barlow",
    "codeLink": "CODE_URL",  # TODO: replace with url
    "yearsPython": 5,
    "yearsDjango": 5,
    "repos": "https://github.com/pingponghero",
}

body = json.dumps(payload)  # serialize up front so we can sign it and send as is
signature = hmac.new(secret.encode(), body.encode(), hashlib.sha256).hexdigest()

resp = requests.post(
    endpoint,
    data=body,
    headers={
        "Content-Type": "application/json",
        "X-HMAC-Signature": signature,
    },
    timeout=15,
)
print(resp.status_code, resp.text)  # use text in case we get an error body that isn't JSON
