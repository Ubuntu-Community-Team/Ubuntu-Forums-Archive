---
title: "I have to modprobe ndiswrapper after every reboot! Please help!"
date: 2007-03-28
forum: Networking &amp; Wireless
---

### Post by POSTGOOP on 2007-03-28
Hi all,

I've installed linux on my mother's computer (so it's important that I have things working so that they won't break when I'm not looking).

I successfully installed her zonet wireless card(zew1602) using ndiswrapper and netmw125.inf from the install cd...

It works, but after I restart the computer, I have to re- 'modprobe ndiswrapper' to get the computer to recognize it. After that, it immediately connects and works fine.

So..... How can I make it work on its own?

Thanks a lot! :)

---

### Post by chili555 on 2007-03-28
I suggest you *sudo gedit /etc/modules* to add this:```
ndiswrapper
```on its own line. Run:```
sudo depmod -a
```Reboot and let us know.

If ndiswrapper is already in /etc/modules/ post back and we'll troubleshoot further.

---

### Post by POSTGOOP on 2007-03-28
It worked! Thanks a million! :)

---

