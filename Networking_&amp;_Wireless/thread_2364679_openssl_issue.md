---
title: "openssl issue"
date: 2017-06-26
forum: Networking &amp; Wireless
---

### Post by tgreerboozin on 2017-06-26
I am attempting to create a simple socket server that implements openssl. I generate the RSA key and certificate using:
openssl req  -new -x509 -sha256 -newkey rsa:2048 -nodes -keyout key.pem -out cert.pem -days 365

When my server code is executed, it seg faults on  if (SSL_CTX_use_certificate_file(ctx, "cert.pem", SSL_FILETYPE_PEM) <= 0).

Does anyone have any idea why?

---

### Post by tgreerboozin on 2017-06-26
UPDATE: I missed the create_ctx function call. It is now working.

---

