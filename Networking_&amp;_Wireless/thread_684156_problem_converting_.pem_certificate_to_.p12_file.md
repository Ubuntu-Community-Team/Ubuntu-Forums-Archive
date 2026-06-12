---
title: "problem converting .pem certificate to .p12 file"
date: 2008-01-31
forum: Networking &amp; Wireless
---

### Post by CamranKhan on 2008-01-31
Well I am using OpenSSL and trying to convert a .pem certificate(s) to a .p12 file so I can use it in Windows XP (client). I am using the following command:

openssl pkcs12 -export -in winxp.com.pem -inkey winxp.com.key -certfile demoCA/cacert.pem -out winxp.p12

I am getting an error, which is as follows:

unable to load private key

Any suggestions as I am having this problem for the past few days trying to resolve it. I am using Ubuntu 7.10 and I have generated the Certificates in a directory called /var/sslca and I am running the above command from this directory.

Hope to hear from you all soon please urgent attention required!!!!!!!!!

Thanks

Cam

---

