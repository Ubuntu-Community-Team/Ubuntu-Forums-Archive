---
title: "feisty package upgrade broke wireless networking"
date: 2007-04-09
forum: Networking &amp; Wireless
---

### Post by asdf29 on 2007-04-09
I followed the howto for my laptop hp nx6325 at:
[http://vale.homelinux.net/wordpress/?p=144](http://vale.homelinux.net/wordpress/?p=144)

I did a fresh install of Feisty Beta 64bit.  Followed the instructions and the wireless came up and worked using ndiswrapper.  I decided it was probably a good idea to upgrade all 273 packages that I could.  As soon as this was finished my wireless connection was dropped and I can't reconnect.  When I click on Network Manager all the networks in the area are detected with signal strengths etc...  but I just can't connect to my home network.

> asdf29@flyhead:~$ ndiswrapper -v
utils Error: no version specified!
driver version:        1.38
vermagic:       2.6.20-14-generic SMP mod_unload

> asdf29@flyhead:~$ uname -r
2.6.20-14-generic

I noticed this line in my syslog that didn't used to be there:
> 
Apr  9 13:03:18 flyhead avahi-autoipd(eth1)[12772]: fopen() failed: Permission denied

Anyone got any ideas which package has broken my wireless?

Thanks in advance,
asdf29

---

### Post by TheWizzard on 2007-04-09
use dapper or edgy. or wait until feisty is out of beta.

---

### Post by bdogg64 on 2007-04-09
Did you try reinstalling the ndiswrapper utils ?

---

### Post by asdf29 on 2007-04-10
Yeah tried reinstalling, didn't work.

Setting things up using dapper or edgy is a big mission in itself on a nx6325.  Whereas most things seem to be working alright using feisty beta.


If I knew what package it was I could stop the upgrade...

Anyone got any ideas?

---

### Post by bumfrog on 2007-04-10
i've got a similar problem.  Installed edgy 6.10 and the wireless worked fine.  Upgraded to feisty and now the wireless connects then instantly disconnects then won't connect again.

I can only presume it's a bug in feisty...

---

### Post by bthessel on 2007-04-10
I had new upgrades available last night that broke mine. It was fine after the upgrades until I rebooted. Now I can see the networks but can't attach to them. Go to re-run the Ndiswrapper install tonight to see if that fixes the problem.

---

### Post by bthessel on 2007-04-10
I fixed the problem by enabling Unsupported updates, under the Third-Party Software Tab in the Synaptic repositories. There was then a update for Network Manager available that after install and a reboot caused my wireless to begin working again.

---

### Post by jacksonz123z on 2007-04-10
I have had this problem a few times after Feisty updates.  Each time deleting NetworkManager fixed the problem.  WiFi radar seems to work if you need to roam.  Otherwise you are better off without NM!

---

