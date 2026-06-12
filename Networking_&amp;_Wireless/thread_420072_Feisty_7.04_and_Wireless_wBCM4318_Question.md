---
title: "Feisty 7.04 and Wireless w/BCM4318 Question"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by p252 on 2007-04-23
Hi :) 

I have installed Feisty 7.04 and so far it is AWESOME! The one and only problem I am having is with my wireless connection (naturally). With Dapper and Edgy I could get it working great quite easily. I've gone through my usual steps to get it working with Feisty 7.04 and all seemed well. Network Manager picks up my wireless network SSID so I click on it to connect, however, I can't log in. The screen that asks for my WPA2 key keeps popping back up over and over as thought the key I enter is not working. I have checked and double checked my key and settings on my router (works fine for my other computers and worked fine on this one with Dapper and Edgy and I have not made any changes to the router since) and they are fine. I am using Dell TrueMobile (BCM4318).

Any thoughts?

Thanks for the help!

---

### Post by Melcar on 2007-04-23
How do you usually get it to work?  Ndiswrapper or the native firmware support?  I normally use ndiswrapper and it worked fine under Dapper and Edgy, but now under Feisty I experience a similar problem to yours; it will simply not connect despite being able to scan networks and me typing the WPA key countless times.  I had to resort to using the firmware hack which unfortunately limits my speeds to 11Mbps.  I have a 4318 chip by the way.

---

### Post by MystaMax on 2007-04-23
Could one of you guys post a link to the tutorial you followed to get it working w/ BCM4318? I've got a D600 w/ BCM4308 and I got it working by installing the firmware and a reboot. Now I have a D610 and need help. Thanks.

---

### Post by p252 on 2007-04-23
I am using ndiswrapper to run my card. Has always worked great with Dapper and Edgy so I am baffled with Feisty. I could resort to a slower firmware, but, I would really rather not do that if possible. . .

---

### Post by Melcar on 2007-04-23
Firmware hack.  First post on the second page (look at the link in the signature);
[http://ubuntuforums.org/showthread.php?t=414168&page=2]("http://ubuntuforums.org/showthread.php?t=414168&page=2")

and this for using ndiswrapper;
[http://ubuntuforums.org/showthread.php?t=201902%highlight=broadcom+ndiswrapper]("http://ubuntuforums.org/showthread.php?t=201902%highlight=broadcom+ndiswrapper")

---

### Post by p252 on 2007-04-23
Thanks Melcar, I never noticed that link in the signature. I'll see what it can do :)

---

### Post by Melcar on 2007-04-23
> **p252 said:**
> Thanks Melcar, I never noticed that link in the signature. I'll see what it can do :)


Just download the file, install it, and reboot.  Once you log back in your wireless device should work.  Just remember to undo all changes made if you used ndiswrapper (uninistall the drivers, restore any edited files, delete /etc/network/interfaces).  Beware that it will only give you up to 11Mbps.

---

### Post by p252 on 2007-04-23
Yeah, I'd rather have the full power of my wireless card, but, 11mbs is better than none I guess :guitar:

---

### Post by p252 on 2007-04-23
I just wanted to let everyone know that I got my wireless working!!!! And I didn't have to use a slower firmware (I'm using ndiswrapper at 54mbs!). I feel kind of dumb in retrospect, though, I guess I didn't know. Apparently the problem was with the WPA2 encryption. I changed my router settings to plain WPA and my laptop connected with no problem. Not sure what in Feisty has changed so WPA2 doesn't work (did in dapper and edgy), but, I can live with WPA just fine. Hope this helps anyone else having similar problems.

---

### Post by Cenotaph on 2007-04-23
I was having some issues with the ndiswrapper available in feisty, even with WPA authentication. I then chose to install the latest ndiswrapper version from source and it works perfectly, maybe that was the problem.

---

### Post by Melcar on 2007-04-23
> **Cenotaph said:**
> I was having some issues with the ndiswrapper available in feisty, even with WPA authentication. I then chose to install the latest ndiswrapper version from source and it works perfectly, maybe that was the problem.


Could be.  I will try compiling ndiswrapper from source and see if I have any luck, but I'm beginning to suspect that it's networkmanager that's screwed up.

---

### Post by iwarp62 on 2007-04-24
Hi all,

This is a known bug. ([#105977]("https://bugs.launchpad.net/ubuntu/+bug/105977")) It sucks I know. It's not terribly hard to fix though. You need to compile the latest ndiswrapper from source:

Follow Steps 11 through 14 on [this wiki page.]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

Then reinstall your drivers into ndiswrapper just like you tried earlier. This has worked for me and several other users without a hitch:). Give it a shot.

---

### Post by H.E. Pennypacker on 2007-04-24
> Firmware hack. First post on the second page (look at the link in the signature);
[http://ubuntuforums.org/showthread.php?t=414168&page=2](http://ubuntuforums.org/showthread.php?t=414168&page=2)

That did not work for me.

> and this for using ndiswrapper;
[http://ubuntuforums.org/showthread.php?t=201902%highlight=broadcom+ndiswra](http://ubuntuforums.org/showthread.php?t=201902%highlight=broadcom+ndiswra) pper

That did not work for me either.  I used ndiswrapper on Dapper and Edgy, but something's wrong with Feisty.

> I was having some issues with the ndiswrapper available in feisty, even with WPA authentication. I then chose to install the latest ndiswrapper version from source and it works perfectly, maybe that was the problem.

I'll try that out.

---

### Post by Melcar on 2007-04-25
> **iwarp62 said:**
> Hi all,

This is a known bug. ([#105977]("https://bugs.launchpad.net/ubuntu/+bug/105977")) It sucks I know. It's not terribly hard to fix though. You need to compile the latest ndiswrapper from source:

Follow Steps 11 through 14 on [this wiki page.]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

Then reinstall your drivers into ndiswrapper just like you tried earlier. This has worked for me and several other users without a hitch:). Give it a shot.



That seemed to work for me :guitar: .

---

### Post by opensourcerer on 2007-06-17
> **iwarp62 said:**
> Hi all,

This is a known bug. ([#105977]("https://bugs.launchpad.net/ubuntu/+bug/105977")) It sucks I know. It's not terribly hard to fix though. You need to compile the latest ndiswrapper from source:

Follow Steps 11 through 14 on [this wiki page.]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

Then reinstall your drivers into ndiswrapper just like you tried earlier. This has worked for me and several other users without a hitch:). Give it a shot.

I just wanted to verify that this worked for me on an HP NX6125 with the bcm4318 card. I was able to connect to open networks but not my WPA2 network, so I followed the steps to compile the latest ndiswrapper, and now network-manager works just fine. Thanks!

---

