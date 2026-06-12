---
title: "Wireless problem (WPA on ubuntu 7.04 beta)"
date: 2007-03-30
forum: Networking &amp; Wireless
---

### Post by Nihad on 2007-03-30
Hello,

Couple of days ago I installed 7.04 Beta, and it's working great except following...

After some time configuring my wireless, I have set it up to use wireless network, and it is connecting to my AP using WPA encryption, but it seems like it doesn't get DNS info. I've tried setting it up with DHCP and static, and non of there let me go online. 

Problem is, DHCP does not work at all (can't connect and no ip is issued), when in static mode, it connects to AP, but I can't ping anything, except my own machine. 

On the other hand, when I connect on wired net (same router), both DHCP and static works without a glitch.

So I am suspecting DNS settings somehow, but have no idea if that is it, and what to do if it indeed are faulty DNS settings.

I'd like to hear from someone with possible solution or similar problem...

---

### Post by Drate on 2007-03-30
I know nothing of Feisty, but I do know some of wireless... what kind of card are you using?

---

### Post by Nihad on 2007-03-30
Wi-fi card is Broadcom 1490 dual band wlan mini-card. 

I am using wpa-applicator, and followed instruction for setting wi-fi on ubuntu from this forum thread. ( [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539) )

---

### Post by Drate on 2007-03-31
Well, I have a broadcom 4318 I think... and I'm using Edgy.  That said...

Here is what I did to get mine to work, and it's worked for everyone that's tried it with a SIMILAR CHIPSET.  You may want to leave out the blacklisting step, or modify it to your needs, I'm not sure, so, good luck. :)

[http://www.ubuntuforums.org/showthread.php?t=381770](http://www.ubuntuforums.org/showthread.php?t=381770)

---

### Post by Alfdog on 2007-04-01
I'm also having the same problem with my m1210, I put in the dell 1490 card so I could use it with OSx86.  My old 3945abg worked great with 7.04, but this new card... not so much.  Hopefully this will be fixed with the final 7.04 release, but if you do get it working right, please post how.

thanks,
alf

---

### Post by Alfdog on 2007-04-03
I got my Dell 1490 (Broadcom 4310) card working with WPA, on my m1210!

I followed the guide from this thread:
[http://www.ubuntuforums.org/showthread.php?t=367329](http://www.ubuntuforums.org/showthread.php?t=367329)

Read my post at the bottom first

---

### Post by Drate on 2007-04-03
Same as mine really.  Though his is prettier. *sigh*

---

