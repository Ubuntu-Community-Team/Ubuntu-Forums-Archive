---
title: "VPN to office"
date: 2007-01-19
forum: Networking &amp; Wireless
---

### Post by theh0g on 2007-01-19
I've tried to connect to office's VPN on all the ways people have suggested here and other forums. I've tried VPN with nm-applet, pptpconfig and vpnc. There is always 238756 options everywhere, where in Windows I simply type in:
IP/host
domain (group)
username
password

That's it, I don't know jack about encryption, compression nor I care, I just need to connect. Is all autodetectable in Windows or how come it simply works there while I can't connect from my Ubuntu? pptpconfig somehow seems to connect, but something must be wrong with DNS or something, since I can't ping or connect to any machine. Can someone please help me, I only have Windows installed because of VPN. Thanks.

---

### Post by scrooge_74 on 2007-01-19
Can't help unless you give more specifis on the setup on your side and on the office side.

I once tried that, but in the end just settle for ssh into the office for maintenance and ssh from gnome to get files in the office

---

### Post by kd7swh on 2007-01-19
> **theh0g said:**
> I've tried to connect to office's VPN on all the ways people have suggested here and other forums. I've tried VPN with nm-applet, pptpconfig and vpnc. There is always 238756 options everywhere, where in Windows I simply type in:
IP/host
domain (group)
username
password

That's it, I don't know jack about encryption, compression nor I care, I just need to connect. Is all autodetectable in Windows or how come it simply works there while I can't connect from my Ubuntu? pptpconfig somehow seems to connect, but something must be wrong with DNS or something, since I can't ping or connect to any machine. Can someone please help me, I only have Windows installed because of VPN. Thanks.


Well I use vpnc, and I just put the 

IP/host
domain (group)
username
password

information in a conf file. than use that file to connect. Ex: /etc/vpnc/um.conf would be used  like this:
```
root@laptop:~# vpnc um
Enter IPSec gateway address: **.***.*.*** (IP)
Enter IPSec ID for **.***.*.***: domain
Enter Username for domain: jon
Enter Password for jon: *******

```

Some of this information could just be stored in the .conf but I choose not to do that for increased security.

Even if you don't care about the encryption or compression it maybe important to getting a vpn client working. It took me a few days to get mine streamlined. 

You may also try installing kVPNc it makes configuring new profiles pretty easy.


Best of Luck

---

### Post by theh0g on 2007-02-19
Hey,
kd7swh: I've tried this, but it always asks for "IPSec secret", whatever this is.

Scrooge: I don't know any details...if it works in Windows and OSX without any special settings, so should here.

---

