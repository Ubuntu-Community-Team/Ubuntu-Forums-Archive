---
title: "ZENMAP Scan of 14.04"
date: 2015-07-30
forum: Networking &amp; Wireless
---

### Post by SonorDrummer on 2015-07-30
When scanning a 14.04.2 server for, "Intense scan, all TCP ports," the scan returns the following lines:

| http-title: Apache2 Ubuntu Default Page: It Works
| ssl-cert: Subject: commonName=*.x.y.z.com

(Obviously the xyz is not what the domain name entails)

My question is from where does it read this information?  Which file do I need to edit to find this?

---

### Post by SonorDrummer on 2015-07-30
I believe I found it.  When you perform:
sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/apache2/ssl/apache.key -out /etc/apache2/ssl/apache.crt

there are a number of questions that get encoded into the files, one of those questions shows as commonName.

---

