---
title: "Broadcom 4311 doesn't work properly after updating Ubuntu 14.04"
date: 2014-08-19
forum: Networking &amp; Wireless
---

### Post by Ksiencha on 2014-08-19
I have two laptops currently: the old one (Broadcom 4311[14e4:4311](rev 01)) and the new one (Qualcomm Atheros AR9462 Wireless Network Adapter pci@0000:03:00.0).

**The main goal**: _create a hotspot on the old one(BCM4311) and connect to it the new one(AR9462)._

**History**: 

**1.** I had Ubuntu 14.04 installed on my old laptop some time ago, and in order to install the needed drivers I followed [**askubuntu answer**]("http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers/38700#38700") , and also I created a hotspot as it is descibed [**here**]("http://www.webupd8.org/2013/06/how-to-set-up-wireless-hotspot-access.html"). And it all worked like a charm.

**2.** Damn me, I've decided to make a fresh install on my old laptop, because it became to slow, and I thought it would help. So I installed Ubuntu, updated everything followed those guides above, and nothing.

Let me explain what nothing means: 
[LIST]
[*]when I check the the icon on the panel it ony shows one or two connections on my old laptop but four or five available connection on the new one, which I don't understand. How can my bcm4311 not see all wifi connections? 
[*]when I do ```
sudo ap-hotspot start
``` it shows me notification on the desktop that hotspot is created but when I ```
sudo ap-hotspot stop
``` - it won't show any notification, which wasn't the case on the prev Ubuntu installation. 
[*]and also the indicator light on my old laptop is off. 
[*]When I try to connect AR9462 to bcm4311 it shows notification that "New device is connected" or something, however on AR9462 it shows that it still is "Connecting..." and then it fails to connect and there's a notification on bcm4311 laptop "The device is disconnected" or something like that. 
[/LIST]

**3.** And again I made a fresh Ubuntu 14.04 install and this time I followed [**Broadcom guide**]("http://ubuntuforums.org/showthread.php?t=2214110") , and guess what: all the problems stay the same. I'm also aware of [**this thread**]("http://ubuntuforums.org/showthread.php?t=2226102"), but as I said nothing's helped me so far.

I don't know what do I do wrong! Please, help me!
I'm definitely not an advanced user of ubuntu but I will put any effort it needs here to solve the problem. Sorry if I won't respond right away - you know we all are humans and have to do other things also. But of course I will respond to everyone who are willing to help me.
Thanks :)

---

### Post by Ksiencha on 2014-08-20
You know what I did - I installed linux mint 17 mate (because you know it's old laptop, and besides I have nothing to lose). I haven't installed any updates and went straight to installing *firmware-b43-installer b43-fwcutter* drivers. Then I installed *ap-hotspot*, created hotspot, and voila - it works finally - I managed to connect my new laptop to this one.

 Again, I haven't installed any updates for this OS, apparently there's something wrong with them which prevents my wifi to work in a proper way.

I've also tried Xubuntu and Lubuntu: I installed first drivers for wifi and ap-hotspot, and it all worked; then I installed updates and after reboot wifi stops working normally.

I'm not sure that this thread can already be marked **solved** because I cannot now install updates which will have a bad result. If anyone knows what's the problem with those updates, please tell me.

---

### Post by westie457 on 2014-08-20
Give this a try.
Plug in a cable
```
sudo apt-get install --reinstall firmware-b43-installer b43-fwcutter
sudo rmmod -vf b43
sudo modprobe b43
```
remove the cable and check Network Manager to see if any more networks are available.

Let us know what happens.

Thank you

---

### Post by Ksiencha on 2014-08-20
Yes, it cas see some available wifi networks.
I also plugged in the cable, launched ap-hotspot and my new laptop could successfully connect to my old laptop hotspot.

Does that mean that I can install updates?

---

### Post by westie457 on 2014-08-20
Now we have your wireless working, are you trying to use this as a router (access point) for all of your other devices to connect to?

I know nothing about ap-hotspot and what it does however I do know that in Network Manager you can set the wireless to be an 'Adhoc' connection (hotspot). AFAIK for this to work correctly the box has to have a cable connected to a modem/router so the wifi chip can be used as a wireless router.

Go ahead and try the ap-hotspot, if it does not work post back here.

---

### Post by Ksiencha on 2014-08-20
Yes, exactly, I use it as a router. And I've already done it, I mean that with the help of ap-hotspot I created an access point on my old laptop[bcm4311](which I use as a router), and my new laptop can connect to it.

---

### Post by Ksiencha on 2014-09-09
Phew! Finally got it! It's firewall the one that was blocking my wi-fi from creating a hotspot properly.
It's just after a while I suddenly recalled that I haven't enabled firewall on my old laptop, so I decided to enable it:

```

sudo ufw enable

```

The next day I tried to connect my Atheros laptop to it, and it failed. I even reinstalled the OS on my new laptop ('cause I haven't updated my old laptop, so I thought it's not its fault), but it didn't help. I remembered though that I enabled ufw, so I disabled it:

```

sudo ufw disable

```

And voilà! It works :)

---

