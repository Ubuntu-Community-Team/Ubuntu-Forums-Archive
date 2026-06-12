---
title: "Samba strangeness: authentication works behind router, not outside it"
date: 2007-07-06
forum: Networking &amp; Wireless
---

### Post by SkyFire360 on 2007-07-06
Hey all

Having a weird problem with Samba.  I have three computers on my home network: a windows XP gaming/work machine, and XP laptop, and a linux fileserver running ubuntu and Samba 3.0.22.

Quick Facts:
* I am sharing a folder on my linux box via samba
* The username on my linux box is the same as my windows box, but the windows box has a capital first letter (so does the laptop)
* I **can** authenticate and access the linux box on my XP machine (I can also map drives) with my windows username/password
* I have forwarded 135-139 and 445 through  my router
* I have registered a www domain
* If I go to work and access \\[www.mywebsite.com\share](www.mywebsite.com\share), it prompts me for a username/password

Now here's the annoying part: no matter what I do, I can't authenticate. My smb.conf is as follows:

```
[global]
workgroup = MyHome
netbios name = MyMachine
server string = Linbox
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
log file = /var/log/samba/%m.log
max log size = 50
encrypt passwords = yes
smb passwd file = /etc/samba/smbpasswd
security = user
local master = yes
os level = 33
domain master = yes
preferred master = yes
wins support = yes
dns proxy = no
passdb backend = smbpasswd
passdb expand explicit = no
username map = /etc/samba/smbusers

[share]
path = /warehouse
```

I also have "username = Username" in my smbusers file, and have confirmed that the username is in the smbpasswd file.

The problem is that behind the router, everything works perfectly.  Outside, I can't seem to authenticate.  I'm stumped.  Any Ideas?

---

### Post by taylorsnow on 2007-07-06
whats your domain name... it sounds like you dont have a DNS server pointing to your box at home.... just curious....

---

### Post by SkyFire360 on 2007-07-06
The DNS appears to be fine.  The HTTP server I'm running on it works well enough.  I also have a static IP, and the same thing results when I access it via the \\xxx.xxx.xxx.xxx\share way too. :-k

---

