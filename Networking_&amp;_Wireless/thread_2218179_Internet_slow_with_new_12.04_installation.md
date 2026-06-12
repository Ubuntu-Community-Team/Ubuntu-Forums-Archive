---
title: "Internet slow with new 12.04 installation"
date: 2014-04-19
forum: Networking &amp; Wireless
---

### Post by jerryd2 on 2014-04-19
Lubuntu forum,
 Dell D400 Latitude Windows XP Home 32 bit no PAE support.
 Linksys WRT54G V3.0 DD-WRT firmware.

 Finally got Lubuntu 12.04 installed on my old Dell 400 and can
 successfully dual boot.

 Wireless connection was successful using sudo command to install
 the resident firmware but the connection speed is very, very slow.

 I generally get 12MB download and 10MB upload speeds with windows
 but with Lubuntu I'm getting less that 1GB download and upload.

 With windows Ethernet connection I get 50MB+ download but with
 Lubuntu I get about 20MB.

 Same router and security settings.

 I have the linux driver for my wifi card but don't know how to
 install it.

Jerryd2

---

### Post by varunendra on 2014-04-20
Please open a terminal (Ctrl-Alt-T) and post back the outputs of -
```
uname -mr
lspci -nnk | grep -iA2 net
lsmod
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

**PS:**
You should use the default fonts in your posts. Bold, coloured etc. fonts should be used only to highlight the important parts of a post, if really required.

---

### Post by mörgæs on 2014-04-20
12.04 is out of support. You will be better off with a fresh install of 14.04, in which the PAE problem is solved:
[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

---

