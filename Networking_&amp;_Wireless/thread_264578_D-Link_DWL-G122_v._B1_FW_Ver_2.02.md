---
title: "D-Link DWL-G122 v. B1 F/W Ver 2.02"
date: 2006-09-24
forum: Networking &amp; Wireless
---

### Post by Desabrir on 2006-09-24
I have mine working, however it randomly shuts off and takes about a minute or two for it to get back up and running again. 

I thought maybe it was overheating as it was fairly hot, but I took it 's cover off and placed a memory chipset cooler from my video card on to the RAlink chipset and put a fan in front of it.

:confused: 

h4n5

---

### Post by roberto22085 on 2006-09-25
Have you checked your power settings??

---

### Post by Desabrir on 2006-09-25
Power Settings? I'm fairly new to the linux area. I know there are power settings for signal strength, but I have absolutely no idea how to check them, let alone check them with this particular USB adapter.

Ubuntu got it working, (even though it freezes when you activate it, reboot as long as you have it configured and it works.) but I wouldn't even know how to make advanced changes like that.

Any pointer?

h4n5

---

### Post by Desabrir on 2006-09-26
ok, so I looked at the dmesg and found out that My adapter kept switching to IPv6 and giving the error that there are no IPv6 routers on the net work -- of course I have $30 a netgear router.

So in order to do a quick fix, i deleted all of the hosts in the netowrk settings that refered to IPv6. Now all hell broke loose. Does anybody have a list of **ALL** of the IPv6 hosts?

Also, how to I keep my apater from trying to use IPv6?

I think this is what has been causing my toubles.

h4n5

---

### Post by Desabrir on 2006-09-27
Bump, Just want to gsee if i can get those settings. :-/

h4n5

---

### Post by Desabrir on 2006-09-28
Update!! (for those still listening)

ok so I got those hosts settings by using the Ubuntu install disk. Loaded the Live version and copied them from the settings there.

Also. 

I have found the problem. The actual USB adapter crapped out. Did Ubuntu do this by means of a bad driver? It was working for for over 2 months on Windows XP Pro.

Well thanks for taking the time to read this. :)

h4n5

---

