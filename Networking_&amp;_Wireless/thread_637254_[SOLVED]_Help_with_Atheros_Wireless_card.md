---
title: "[SOLVED] Help with Atheros Wireless card"
date: 2007-12-10
forum: Networking &amp; Wireless
---

### Post by alex1966 on 2007-12-10
I haven't had any wireless access on my new Gutsy install from the beginning. My laptop(Sony Vaio vgn-n365) has atheros card , which is supported by Madwifi. After installation of restricted module for i386 I have following:
-correct driver installed and actually talking to  kernel(lshw -C network)
-I can scan for routers and see them(iwconfig)
-my card gets proper IP settings via router's dhcp

What I DON"T have is actual comunication and internet access.

Any thoughts?
Thanks

---

### Post by alex1966 on 2007-12-10
P.S.

What's  amazing about whole hype about ubuntu is when I boot same comp into Mandriva 2008 LiveCD wireless works in less than 10 seconds. Belive it or not.

---

### Post by alex1966 on 2007-12-10
Now, it looks a lot  like an ole microsoft here -no paying -no gain. And , please quit saying ubuntu has a great support. Couse ir's not true. You adoption of Linux kernel isnt working (Debian sucks in general).

---

### Post by alex1966 on 2007-12-13
P.S.
Mandriva 08 enables SAMBA and NFS by default. And this is a free! Mandriva ( no stolen codecs or anything else). I am switching  to Manny - fast and furious. Good luck- ubu users.
 truly yours
 Aleksei B. Yaskov

MCP
 MCSE
CCNA
ASTARO
3com tipping point

---

### Post by alex1966 on 2007-12-13
And this is on their GNOME version - kinda foster child to their  KDE flagship. Only minus I find with this Mandriva distro - if one runs it on comp with onboard video - no video playback on anything , except you tube format, when you use compiz( lets be prudent - compiz is for kids, "Leopard sucks!")

---

### Post by raiwo on 2007-12-14
then why not just use Mandriva if it works out of box?

anyway

```
lspci | grep Athe
```

shows the model of your card, you can browse [madwifi]("http://madwifi.org/wiki/Compatibility") for  Compatibility.

---

### Post by kaervos1024 on 2007-12-14
The output of "lspci" and "lshw -C network" would definitely help us assist. 

From everything I've seen, the VGN-N365 has an Intel 3945 wireless chipset, not Atheros. 

Some Vaios are using the Atheros ar5006eg chipset, which is problematic, but has been made to work in Ubuntu via ndiswrapper. I'll provide references if this turns out to be the case.

Samba and NFS are a breeze to enable in Ubuntu... whats good about having them enabled by default? Some users may not even have a use for them.

As far as video playback with the integrated video, I have a Sony Vaio VGN-FS840/W with the same Intel GMA 950 as the VGN-N365. It plays any sort of video, and performs very well in Ubuntu 7.10 using the default Intel - Experimental Modesetting driver.

---

### Post by alex1966 on 2007-12-14
Thanks for response. I'd like t get those references, please.
Yes my Vaio vgn-n365 has Atheros wireless chip.
And generic kernel 2.6.22-14 does not see that chip. But if i use restricted modules for i386 system sees it and wired NIC starts loosing dhcp randomly.
PS. Tried Ubuntu CD and whats amazing- Live mode picks up wireless in a jiffy.With the same generic module set.
So I thought ,mayby reverting from compiz to no effects at all would do the tric- nope, it did not.
As for mandriva-I like ubuntu better,and don't see why not to try fix it.
Thanks again.

---

### Post by kaervos1024 on 2007-12-14
For the ar5006eg chipset, I noticed a resolution in a different thread using ndiswrapper: 

[http://ohioloco.ubuntuforums.org/showthread.php?t=621562](http://ohioloco.ubuntuforums.org/showthread.php?t=621562)

The instructions used that resolved the issue were posted by Chalewa, here:

[http://ohioloco.ubuntuforums.org/showpost.php?p=3868406&postcount=48](http://ohioloco.ubuntuforums.org/showpost.php?p=3868406&postcount=48)

Again, this is only for the ar5006eg chipset. I would double check to make sure that is your exact Atheros model, since I still haven't seen the output of your lspci or lshw.

I saw on the net that your Vaio model has Intel 3945 wireless. Thats not the case?

---

### Post by alex1966 on 2007-12-14
Thanks foir help Kaervos1024, Chalewa that walkthrough solved my wireless Atheros chip issue on Vaio VGN-n365.
Thank you.

---

### Post by kaervos1024 on 2007-12-14
Glad to hear it, Alex. Hope you enjoy your new Linux laptop. Ubuntu support isn't too shabby after all, eh? ;)

If you are all set, you should mark this thread as Solved. 

Enjoy the season!

---

### Post by alex1966 on 2007-12-14
kaervos1024,
 Thanks again,
 This issue was my personal problem. As  an admin for enterprise company with 86000 computers I always looking for a ways to save  money. Not paying fees for Windows is great. Support -what is most crucial issue with hardware- as we all know stuf breaks. HP is fairly good , Dell is awesome. Ubuntu's just great OS. Thank you .

---

