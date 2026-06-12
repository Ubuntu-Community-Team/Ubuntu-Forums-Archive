---
title: "Ubuntu and USB Wireless Adapter"
date: 2006-10-02
forum: Networking &amp; Wireless
---

### Post by pdania on 2006-10-02
I'm new to Ubuntu and I use a Netgear Wireless Router, on my laptop which I've just installed ubuntu there is a Netgear USB wireless adapter which isn't working with ubuntu, It appears to be detected in Hardware devices, but I can't connect to the internet because it doesn't seem to recognise it as a networking device, Any ideas anyone?  Thanks for your help in advance.

---

### Post by darth_vader_ca on 2006-10-02
are you familiar with the ndiswrapper, it is mostlikely required. install it as well as the wireless tools in ubuntu, afterwards get the microsoft drivers, then in the terminal do sudo ndiswrapper -i "whatever the driver is"
then ndiswrapper -l and see if the hardware is present. after that reboot pc. you should see your wireless adapter in network.

---

### Post by pdania on 2006-10-03
Thanks very much Darthvader, I spent most of Last night trying to install ndiswrapper, it wasn't easy and I'm not pleased to say that I couldn't do it, I was determined to get Ubuntu working wirelessly but in the end I had to stick in an RJ45 cable into the PC Card Lan Adapter which as always works without a hitch.  I want to persevere this time though so I will keep on learning the tricks of Linux which coming from a predominantly Windows environment, isn't easy.  I must add that unless someone hasd a lot of patience they will easily give up and conclude that Linux is an unfriendly operating system.

My browsing experience using Firefox is no pop-ups but seriously lacking in plug-ins, which is in itself a pain, I'd rather have pop-up blockers and be able to view most websites all the time.

---

### Post by Jose Catre-Vandis on 2006-10-03
Have a look through this thread and the links therein. Getting ndiswrapper going isn't that bad once it starts wortking for you. I find it difficult to get the thing to work automagically on boot up, so use a script to start it each time.

[http://www.ubuntuforums.org/showthread.php?t=258527](http://www.ubuntuforums.org/showthread.php?t=258527)

---

### Post by pdania on 2006-10-06
Just to say thanks for your assistance, ndiswrapper worked after some hard work and that particular night I had to stay up until nearly 2am.  I got the Laptop to recognise the USB adapter and was able to get unto the internet.  THE PROBLEM I'm now having is that I have to disable WEP on my wireless router before UBUNTU can do any networking otherwise it just doesn't so wht is the best way to configure WEP in UBUNTU??

---

### Post by Jose Catre-Vandis on 2006-10-06
> **pdania said:**
>  I had to stay up until nearly 2am.  What is the best way to configure WEP in UBUNTU??

Its nearer 4am for me, every night :lol:

To sort out WEP isn't difficult, but search the forums as I do not have the experience. Depending on your router, you could approach things in a different way: my router provides for an access list by MAC address, so you lock it down this way. Depends if you have many transient users or public access? I have set up @ 7/8 devices this way and this means that you can run without encryption, but have security at the same time.

---

### Post by pdania on 2006-10-07
nearer 4am!! That's probably why you've got 'way too much ubuntu' careful you don't catch 'ubuntulitis' I did find a guide on how to do WEP but following it didn't give me any results, locking things down by MAC address is probably a good way to go about it, so I'll try this; if my Router supports it and then I'll have to find out how Ubuntu is configured for it.  I'll be in touch.  Thanks a bunch mate.

---

### Post by pdania on 2006-10-07
Okay, I've been on this nearly all day, I haven't been able to get it to do WPA inspite of this [https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo) my patience is running thin so I'll abandon it and come back.  My Router software doesn't do the MAC  address 'thingie' so I tried to use WPA, Windows XP did it like a breeze but not Mr Ubuntu.

---

