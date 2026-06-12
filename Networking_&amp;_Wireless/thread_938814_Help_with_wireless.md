---
title: "Help with wireless"
date: 2008-10-05
forum: Networking &amp; Wireless
---

### Post by Neil_The_Newbie on 2008-10-05
I am getting increasingly frustrated with Ubuntu 8.04 specifically wireless. For the second time in a couple of months my wifi has stopped working. I have made no changes to my system but after checking with update manager it seems to of stopped working after the machine was first started up after the last automatic update - some 4 hours ago. When this happened last time i spent so much time trying to find a solution (something i dont want to do again). For now i have to use my wired connection. This is frustrating as i am not conversant with the inner workings of linux - i just use my pc as a tool for other things such as the net and word processing. But wifi for me is essential. I appreciate you need to get your hands dirty with technical knowledge sometimes but the point of my post is to say that for people like me this is making Ubuntu very unappealing (not to mention unusable). I know the next version is out soon but i'm not interested in different coloured themes as much as i am having a reliable wifi. When I boot in windows vista it works fine - all the time. Ubuntu really need to get the wifi issues sorted out for Ubuntu to become a credible OS for non tech users and mortals such as me.:)

---

### Post by niteshifter on 2008-10-05
Hi,

Let's put the blame where it belongs: On the hardware vendors very few of which produce open source drivers for their hardware. The upstream devs get handed a blob of binary code - no source, precious little documentation, little contact with the vendor's key people. With this what they have to do is essentially reverse engineer the inner working of the vendor's code.

Let's try an experiment. You mentioned word processing - so you write things. Good. Now, here on my machine is a Writer document. It's title is Consumer Car Service Tips. It describes in detail the things a car owner can do to service their vehicle. Could you please:
Clarify the instuctions in Part I?
Make the Servicing Your Brakes Instuctions a little clearer?
etc.
etc.

You protest: Niteshifter, I need to see the document, talk with you bit more, and get some deeper understanding!

Response: <Cricket Noises>

That's what the devs have to put up with. Cut 'em some slack 'K? They're doing the best they can with what's available. What they have done is remarkable. And s l o w l y the hardware vendors are coming around, becoming more open. The complexity isn't all technical, IP rights, existing contractual arrangements also figure in.

(The same occurs in my corner of the computing universe - embedded control, automation, machine vision, SCADA, etc. It's right frustrating dealing with "black box code". Hence my .... 'sensitivity' on this issue.)

---

### Post by PocketDog on 2008-10-05
I ended up borrowing a USB wireless dongle from a spare PC in the house for my laptop, it works flawlessly with no configuration or drivers required. Intrepid has much improved wireless support apparently, have you considered it? I don't want to upgrade to it myself until it goes live at the end of the month

---

### Post by bodhi.zazen on 2008-10-05
It is frustrating in any OS when hardware is not working. I would caution you though that Wireless can be difficult in any OS and in fact I know many people who struggle as much or more with Vista as with Ubuntu.

If you would like assistance please tell us about your hardware 


Wireless card ? Router ? Wireless protocol (WEP, WPA) ?

My only other piece of advice is wicd :

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

It is easy to install and use, and it give me better results then network manager.

Finally I am going to move this post and change to a more appropriate title.

---

### Post by lswb on 2008-10-05
Hardware vendors could certainly make it easier for OS developers, no question about that. And the developers have really done an incredible job of making most hardware useable. However, an argument can be made the some unfortunate choices were made in hardy. Some hardware that worked in earlier releases stopped working or had reduced functionality.

In the case of wireless, for instance, newer drivers for ralink and some intel chipsets (among others?) were adopted that did not have all the capabilities of the older drivers.

NetworkManager as shipped with hardy has some real flaws; a ppp connection to the internet is hardly exotic, for instance, but NM 0.6.6 won't recognize when one is active, and even worse, uses dbus to tell other apps that no network is connected! Ad-hoc wifi networks are another problem for NM. I could go on, but if you really need more examples just take a look a launchpad.

Sure the driver and networking problems may be corrected in some future upgrade, but it is dissapointing to see these regressions in a LTS version like 8.04

---

### Post by 73ckn797 on 2008-10-05
I posted the following thread: [http://ubuntuforums.org/showthread.php?t=938883](http://ubuntuforums.org/showthread.php?t=938883) 

I will try wicd to see if that fixes the connection. Does that sound like a good idea?

---

