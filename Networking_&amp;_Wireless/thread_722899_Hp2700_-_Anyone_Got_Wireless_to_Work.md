---
title: "Hp2700 - Anyone Got Wireless to Work?"
date: 2008-03-12
forum: Networking &amp; Wireless
---

### Post by Astura on 2008-03-12
HP Dv2700 Notebook PC
Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
Ubuntu 7.04
2.6.20-15-generic x86_64


I have followed several guides for ndiswrapper concerning the BCM4310 driver, though not with respect to a fellow Dv2700 computer, and I was wondering if any have got their wireless too work? 

I'm suspecting my laptop has something off with it as other strange bugs like not accepting Gutsy Gibbon nor Allowing Wine to install with out a work around. 

Thanks

---

### Post by Phoenixzeus on 2008-03-13
I haven't tried a broadcomm adaptor, but I know with a bit of fiddling I managed to get my Netgear 511G and an intel prowireless adaptor working.

Does Ubuntu detect the device?
Does it already allocate the driver?
Is there a wireless switch on the laptop or a keyboard combonation that needs to be pressed?
If you type "iwconfig" into terminal what do you get?

---

### Post by Astura on 2008-03-13
astral@velio:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by Astura on 2008-03-13
bump


Still no wireless and I've got no more ideas, anyone?

---

### Post by drdanield@gmail.com on 2008-03-29
Yes, any help regarding this wireless card (BCM4310) on HP dv2700 series laptops would help.  Also, I created a laptop test page .... 
[https://wiki.ubuntu.com/LaptopTestingTeam/HPdv2718us](https://wiki.ubuntu.com/LaptopTestingTeam/HPdv2718us)

anyone please help.

---

### Post by 42Wired on 2008-04-04
I'm running the 64-bit 7.10, and I have no problems with wifi on my dv2700 (specs to follow) until after I come back from Hibernate. If I go into Hibernate, when I come back, it won't detect any wireless networks. It's fixed by restarting, but it is annoying when in class.

If you don't already have it, consider switching to the 64-bit version to see if it works then.

Intel T9300 (Core 2 Duo 2.5 Ghz)
4.0GB RAM
Ubuntu 7.10 (64-bit version)
Linux Kernel 2.6.22-14

---

### Post by faheyd on 2008-04-06
> **42Wired said:**
> I'm running the 64-bit 7.10, and I have no problems with wifi on my dv2700 (specs to follow) until after I come back from Hibernate. If I go into Hibernate, when I come back, it won't detect any wireless networks. It's fixed by restarting, but it is annoying when in class.

If you don't already have it, consider switching to the 64-bit version to see if it works then.

Intel T9300 (Core 2 Duo 2.5 Ghz)
4.0GB RAM
Ubuntu 7.10 (64-bit version)
Linux Kernel 2.6.22-14

I have it running on a HP dv2700t, it comes with a Intel PRO/Wireless 4965 AGN built-in.
Using the 7.10 amd/64bit release.  I connected via wired, Did the update repo's, then updated the whole thing.  Using wep/64bit key because I've got some old devices on my network that only support wep.

---

### Post by 42Wired on 2008-04-07
Do/Did you have/resolve the same problem I do with Hibernate mode?

---

### Post by 42Wired on 2008-04-10
OK, now it's not behaving.

After 20-30 minutes of using a wireless connection, it will disconnect, and stop detecting any wireless networks, like it used to when I came back from Hibernate. Anyone have anyone ideas?

---

