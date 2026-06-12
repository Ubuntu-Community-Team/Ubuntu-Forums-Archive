---
title: "gdm3 doesn't work with pam_mount in 20.04."
date: 2020-05-03
forum: Networking &amp; Wireless
---

### Post by rabbit83 on 2020-05-03
Hi,

I have updated my Ubuntu 18.04.4. to 20.04. I'm authenticating against a Samba Server running on Ubuntu Server 18.04. I'm using pam_mount to mount three network shares. After the update of the client to 20.04. only one share is mounted when using gdm3. When I switch to LightDM or log in via console all three drives are mounted correctly. With gdm3 the mountpoints are created but the share isn't mounted. Logs claim ```
mount error: could not resolve address for MY.SECRET.DOMAIN: Unknown error
```. However, DNS works correctly and the error occurs only when using gdm3. Any ideas?

---

### Post by rabbit83 on 2020-05-04
I found a solution. You have to define a user or group in /etc/security/pam_mount.conf.xml to get it work with gdm3.

---

