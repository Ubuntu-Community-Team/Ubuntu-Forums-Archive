---
title: "Tls/peep stuff impossible?"
date: 2014-07-10
forum: Networking &amp; Wireless
---

### Post by jeehyun on 2014-07-10
After 12.10(maybe) version, I can't use public/enterprise wifi service anymore.
It is tls/peep stuff and requires authentification but I can't bypass it even if I enter id and password.
Windows, osx and android phone can do it well. But all linux distros I tried and windows phone can not.
Is it system bug or support problem?

---

### Post by jeehyun on 2014-07-11
I found anwser.
-------------
I noticed that there aren't any lines like system-ca-certs=true in /etc/NetworkManager/system-connections/<SSID>, so I resolved in this way:

    Turn off WiFi
    Add on a new line system-ca-certs=false
    Turn on WiFi (the line will be deleted automatically)

---

