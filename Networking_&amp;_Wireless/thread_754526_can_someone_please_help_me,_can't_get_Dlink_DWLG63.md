---
title: "can someone please help me, can't get Dlink DWLG630 to work"
date: 2008-04-13
forum: Networking &amp; Wireless
---

### Post by nihiilist on 2008-04-13
I have been trying for days to get my wireless card running and am about to give up on Ubuntu.  I have searched through the help posts on this forum but can't get it working.

I can use the manual configuration sticky to get it to work temporarily with WEP encryption but as soon as i reboot it no longer works plus I want to use WPA2.  When I run lshw -C network it tells me the driver is acx_pci, is this driver capable of running WPA2?

I tried the ndiswrapper and the XP drivers but I keep running into errors trying to get the drivers installed, maybe someone can give me a step by step guide to this method?

Is it possible to use my card with WPA2 in Ubuntu 7.10, please help I am very frustrated.

---

### Post by nihiilist on 2008-04-14
bump, i know there are alot of wireless threads but I want to keep this on page 1

---

### Post by nihiilist on 2008-04-14
i should note I have version B of the DWL G630

---

### Post by nihiilist on 2008-04-15
bump.  I loaded Kubuntu 7.10 and tried to connect with knetworkmanager, it would get to 28% then dissapear

---

### Post by nihiilist on 2008-04-16
cmon it's been a few days and not one person has an idea?  I know someone is having the same problem

---

### Post by nihiilist on 2008-04-19
can anybody offer some advice?  This is what I have tried so far.

wpa_supplicant is installed

If I go to manual settings and enter my information and close the manager nothing happens, if i click on my network in the list I can't choose WPA2 encryption.  I tried to connect to a neighbors uprotected router and nothing happens.

I tried to connect using the manual configuration sticky with no encryption and it worked for a while then stopped on the next reboot.

My card is recognized and the acx pci driver is installed automatically on install of Ubuntu.

I tried the WPA sticky and again nothing happens.

---

### Post by imari2542 on 2008-04-20
I know your fustration.  I've been trying for days to get wireless working too.  I've posted on here twice with no answers.

I've read extensively in these forums anything that even remotely has to do with d-link cards, found linux drivers on their website...follow the instructions and get error messages, have used NDISwrapper and nothing.....read tutorials from this site and others but am no further along.

It's fustrating also because NO ONE has answered either of my posts.  sigh...I'll just keep on trying.  I'm also a newbie.

I just got pokerstars working with wine so I feel a bit encouraged that I can get the wireless working.

Good luck with your wireless...hope you get it working soon.

---

### Post by Bandit60 on 2008-04-20
I'd help if I could. Just replied to imari on his post. I'm a newbie too, and I spent weeks trying to get a Linksys with an RT61 chipset to work, then finally gave up. I  looked at what others said worked right out of the box, then checked Fry's Electronics, and fond one of them, a D-Link WDA-2320, and it worked with Network Manager. 

I did uninstall ndiswrapper and Network Manager, and installed Wicd, and got the Linksys WMP54GR working, but it had poor performance, so I went with the D-Link, and it was worth the $45. You may want to try Wicd.

---

### Post by tturrisi on 2008-04-20
There is no WPA support in the ACX100 driver (yet).
[http://acx100.sourceforge.net/wiki/WPA](http://acx100.sourceforge.net/wiki/WPA)
Read through the various guides and info above.

---

### Post by nihiilist on 2008-04-21
I understand there is no WPA support on this card yet but I cant even get it to connect to an open access point, the 2 dots swirl around to indicate it is trying to connect then they just dissapear.

I am running Ubuntu on a laptop, does anyone know of a PCMCIA card that works with WPA2 out of the box?

---

### Post by nihiilist on 2008-04-22
I finally got it to work using the tutorial here [http://ubuntuforums.org/showthread.php?t=324148](http://ubuntuforums.org/showthread.php?t=324148)

I did this on a brand new install, then Ubuntu wanted to update and the wireless stopped working.  Restarted the networking services and it works again.

---

### Post by taylorjh on 2008-05-02
> **nihiilist said:**
> cmon it's been a few days and not one person has an idea?  I know someone is having the same problem



I just did a clean install from CD of Hardy Heron, replacing Gutsy Gibbon on an IBM T20 laptop. My Dlink DWL-G630, version C2 (Atheros chipset) wireless card worked without problems on my WPA secured network with Gutsy. With Hardy, it works fine for Open Networks (unsecured) and roaming but I cannot get it to work with my WPA secured network.

John

---

### Post by Payteer on 2008-05-09
Hello, it is the same for me on D-Link DWA-610.  On the box it said it supported Linux, my ****.  I, like the previous user can get open networks connected, but can not get the card to see the WPA security id I input for my home network.  I think this is something that needs to be addressed soon.  I believe it is an RT61 chipset, if that makes any sense.  As you can tell I am a Newbie using Hardy.

---

