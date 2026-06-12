---
title: "Wireless problem with Netgear WG111v2"
date: 2008-06-01
forum: Networking &amp; Wireless
---

### Post by timmah1980 on 2008-06-01
Having struggled for hours trying to find the answer to this, I'm reluctantly asking for help. I apologise if the answer to this is already available, but I have struggled to find it.

I've got a laptop (Acer Aspire 1710) which has a built-in Broadcom BCM4306 (rev 03) wifi adapter. Whilst running WinXP, it didn't like the WPA encryption on our wireless network, so I'm not bothering with that one. I have tried using a variety of methods (found online), but it will not see the network at all.

So...option 2 - using a Netgear WG111v2 USB dongle.

I've checked the compatibility list and it appears to be compatible "out of the box" with my version of Ubuntu (Hardy 8.04). Plugged it in and after a while it picks it up.

I've got the Network Manager set to roaming mode, so that when I click the network icon (next to the clock), it pops up a drop-down box with my wireless network listed. It's got a blue bar next to it, which I'm assuming is the signal strength. Despite the router being about 4ft away, with a clear line of sight, the blue bar only fills about an eighth of the available box.

So...I click on the wireless network, enter in the password and it fails to connect. I disable the security, and that doesn't seem to work either as there isn't an option for "no security". I change the security on the router to WEP (rather than WPA), generate a hex WEP key, input the details into the Network Manager (having disabled roaming mode), and still nothing. It popped up the five wireless signal strength bars for a second, then they disappeared.

I'm very new to the world of Linux, and am absolutely loving Ubuntu - I have Ubuntu Studio running, with the AWN dock and Compiz Fusion. I'm having a practice with my laptop, with the intention of using Ubuntu for my home entertainment PC. If I cannot configure a single wifi adapter on it though, despite all it's positive points, it's pretty much useless to me.

If anyone can offer any help or advice, it would be most appreciated. Thanks.

---

### Post by heavenscloud71078 on 2008-06-12
Mine works fine for me but to an extent. I have only WEP, and after having the system up for 30 mins to an hour my connection is completely lost and unable to get one unless I reboot.

TL;DR BUMP/HELP!!

---

### Post by NR1224 on 2008-06-12
same here, i thinks its a problem with the wg111v2 driver

---

### Post by Peter K Nicol on 2008-06-13
I have the same set-up and I can now (after many days of struggle) join any un-encrypted wireless network and access the internet but I can't get past the WEP key on my home system (Netgear). Tonight or tomorrow I am going to disable the key on the router and see if I can get internet access and will report back.

---

### Post by Peter K Nicol on 2008-06-13
Well, that's it. I disabled the WEP setting at the router and I have access to the internet without any difficulty. 
Therefore the question is - Does anybody know how to set up Hardy to run like Fiesty did and accept a 128 bit WEP passphrase?
I am running ndiswrapper with the Win98 driver for Netgear WG111v2. I have network manager set to roaming mode.
I have tried almost everything suggested in the stickies.
Any suggestions would be gratefully accepted.

Peter

---

### Post by zenerian on 2008-06-15
After installing Hardy 8.04 on a dual boot system my netgear WG111v2 came up fine with about an 70% - 90% signal reported but when I started to download some updates the download speed became slower and slower until it stopped working.
My reported signal strength was still ok at about 60%.
I thought it might just be a slow server so I tried to download my email and it just sat there and eventually timed out.
Silly as it may seem I read somewhere in these forums that they thought the wireless adapter was overheating so I blew on it while downloading and the speed increased.
Am I going mad or is there some validity in the 'overheating' idea.
Any suggestions out there or should I just go and get another Linux supported wireless adaptor.
BTW I didn't mention that the adaptor works fine with MS vista and the blue indicator light on the adaptor even works.

---

### Post by Peter K Nicol on 2008-06-18
This is what worked for me.

[http://ubuntuforums.org/showthread.php?t=830762](http://ubuntuforums.org/showthread.php?t=830762)

---

