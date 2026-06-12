---
title: "Maverick - wireless cuts out intermittently - Broadcom"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by naastrodamus on 2010-10-11
My first forum post, but not my first go-round with Ubuntu... Here's some pertinent info:

My system
Gateway MX6027
Broadcom wireless card BCM 4311
Installed Maverick Meerkat yesterday

My system worked like a charm under Karmic, no problems at all. I had the "blank screen" problem with 10.04, so my attempted upgrade was aborted. I decided to try Maverick yesterday, and was glad that the video card issues seem to have been resolved. However...

Installing the driver for my Broadcom card was easy enough. I'm on wireless as I type this, the driver is installed, enabled, all that. But it seems that every few minutes it will just... die. I can usually un-click Enable Wireless, then re-enable it, and get connected again, but who wants to do that?

If I leave the comp unattended and the wireless craps out, sooner or later it will ask me to re-authenticate my wireless password - but not if I catch it fast enough. I've also noticed a couple other things: any time I restart, I have to enter the keyring. On Karmic, it usually only wanted that when I connected to a new wireless network. This time, it's every restart. Also, wireless tends to cut out nearly instantly if I have too much going up & down (i.e. a torrent going while browsing, running Update, etc.) - almost like an 'overload'.

I've googled the heck out of this. I'm not geek-speak-ish enough (haha) to get very technical, but I can usually find a way around a problem. This one, though... It's enough to make me once again trundle back to Karmic. Anybody else having this kind of problem? Any ideas?

Thanks.

---

### Post by Dailydubya on 2010-10-11
I was having the same problem with a Broadcom wireless PCI card. Per some posts on this forum I replaced the default Network Manager with wicd and now it works fine - no more dropped connections or password prompts.

---

### Post by naastrodamus on 2010-10-11
I meant to post a PS that I've tried 3 different wireless networks in 3 different locations... covering all the bases, y'know.

I'll try wicd and see what happens. Thanks.

---

### Post by naastrodamus on 2010-10-11
I meant to post a PS that I've tried 3 different wireless networks in 3 different locations... covering all the bases, y'know.

I'll try wicd and see what happens. Thanks.

---

### Post by naastrodamus on 2010-10-11
Wireless cut out during my attempt to reply... haha. Anyway I'll try wicd and report back.

Was also going to mention as a PS that I've tried on 3 different wireless networks, all with the same result. So that eliminates the "get a new router" argument.

---

### Post by Hippytaff on 2010-10-11
Probably driver issues (seems to be common with broadcom and ralink) look into Nsdiwrapper and blacklisting in the forums and on the ubuntu documentation :-)

---

### Post by eynestyne on 2010-10-14
I have this problem too. 4311 card. It works for a few mins or hours then cuts off. I have to restart to get it back.

Has anyone found a solution?

---

### Post by JackNocturne on 2010-10-14
Confirming this problem too (Same BCM4311)

---

### Post by eynestyne on 2010-10-15
hey guys, i have tried the STA driver recommended by ubuntu's "Additional Drivers" apt as well as fwcutter b43 driver. Both work for a while then cuts out.

I am now testing ndiswrapper using the recommenced driver from the ndiswrapper site: [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:PCI]("http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:PCI")

I will post back to let you all know how this works out

---

### Post by eynestyne on 2010-10-15
ok, that didn't take long.. ndiswrapper knocked out and took everything with it. it seems STA + fwcutter + ndiswrapper = EVERYTHING BLACKLISTED.

deleted a few files and reinstalled the STA.

:(

---

### Post by timuckun on 2010-10-25
I am having similar problems although not as bad (seems to reconnect by itself). It's annoying as hell and wasn't happening in lucid.

Something is clearly wrong here and I hope somebody is aware of it.

---

### Post by ArgusVision on 2010-10-25
Installed 10.10 for a friend. Same broadcom 4311. worked, stopped working, inexplicably started working again... still working last I checked.

---

### Post by seboch on 2010-11-09
I have very similar problem. Wifi was working fine on Ubuntu 8.10.

I have a Dell D505 with a Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03) problem.

Is this problem tracked as a bug somewhere? Does anyone have a solution for this problem?

---

### Post by bababeechums on 2011-01-04
I have the same issue.  Is there a bug tracking somewhere?  I am not sure exactly which broadcom card I have but I know it is in the 43xx series as well (not at home and thus cannot check).  Is there a bug tracking? I would like to add myself to it.  I love ubuntu but wish I didn't have to fix everything each time I update...

---

### Post by bababeechums on 2011-01-04
[FONT=Arial]Found a solution here: [http://nfolamp.wordpress.com/2010/05/02/ubuntu-10-04-and-broadcom-bcm43xx-wireless/](http://nfolamp.wordpress.com/2010/05/02/ubuntu-10-04-and-broadcom-bcm43xx-wireless/)

There is another driver you can use:

$ sudo apt-get install bcmwl-kernel-source[/FONT][FONT=Arial] [/FONT]
[FONT=Arial]$ sudo reboot

hope this works for you too![/FONT]

---

