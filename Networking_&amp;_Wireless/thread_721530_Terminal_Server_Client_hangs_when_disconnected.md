---
title: "Terminal Server Client hangs when disconnected"
date: 2008-03-11
forum: Networking &amp; Wireless
---

### Post by ibbuntu on 2008-03-11
Hi,

I use rdesktop to remote desktop to my work machine, which requires me to connect to a VPN. This works fine, however I occasionally disconnect my VPN, forget I've done so, and go back to my Terminal Server Client screen in fullscreen. This obviously no longer responds, but it also doesn't respond to Ctrl-Enter, so I cannot exit it and I then get stuck and the only thing I can do is restart X using Ctrl-Alt-Backspace.

I know the obvious answer is "well don't do that then!", but if I happen to be a muppet again, is there any other way to get out of TSC? Is this a bug, should TSC disconnect if it loses its connection? Shouldn't it still let me exit even if the connection has been dropped?

Thanks.

---

### Post by PhrygianCat on 2008-03-12
Have you try using gnome-rdp? I find it to be better & easier to work with. Give it a try & see if you have the same problem.

---

### Post by koenn on 2008-03-13
you can probably stop TS client with
```
 kill $(pidof tsclient) 
```
you might have to do that as root / with sudo

Ctrl+Allt F1 will get you a console where you can run commands
Ctrl+Allt F7 will take you back to your desktop env where, hopefully, tsclient has died

---

