---
title: "Citrix SSL Error 61 &quot;thawte ssl ca&quot;"
date: 2014-06-10
forum: Networking &amp; Wireless
---

### Post by lp.descamps on 2014-06-10
Hi,

here is how I managed to get access to my remote office

1. install citrix 12 deb
[http://www.citrix.com/downloads/citrix-receiver/legacy-client-software/receiver-for-linux-121.html](http://www.citrix.com/downloads/citrix-receiver/legacy-client-software/receiver-for-linux-121.html)
2. go to [https://ssltools.thawte.com/checker/views/certCheck.jsp](https://ssltools.thawte.com/checker/views/certCheck.jsp)
3. search for "your office website"
4. download the 2 certificates to /opt/Citrix/ICAClient/keystore/cacerts
5. copy all certificates from /usr/share/ca-certificates/mozilla/* to /opt/Citrix/ICAClient/keystore/cacerts

hope that help few of you

---

### Post by lp.descamps on 2014-11-16
hi. just installed lubuntu 14.10 on a new laptop and couldnt get citrix working again until i realised the permission on these 2 cert i have downloaded were set  to 640.... i ve changed them to 644 so other (firefox) could read them by running sudo chmod 644 "certificate file"

---

