---
title: "How to access a directory on a remote computer?"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by lavadisco on 2009-01-22
I've got both WinXP and Ubuntu 8.10 on my laptop. I often need to connect to my computer at work while I'm at home. In XP, I log into the VPN, open up the Run prompt, type \\bwhite.xxx.xxxx.gov\ and about a second later I'm asked for my username and password. A folder then pops up with my work directories.

I just installed the VPN for Ubuntu. I know it works because I can access secure sites behind the work firewall. Now I want to browse directories just like I can in XP. I tried using the "Connect to Server..." icon and other things, but nothing worked. There seems to be too many options (ports, etc). 

Can anybody lend a hand here? I can't imagine this is very difficult, is it? I feel like I'm one easy step away...

---

### Post by tangibleorange on 2009-01-22
you could try this:

open up nautilus (file browser)
Open up the go menu, and then click location.
in the bar that appears, type:

smb://bwhite.xxx.xxxx.gov/

obviously replacing the xs with the real address.

good luck!

---

### Post by lavadisco on 2009-01-22
That did the trick, thanks!

---

