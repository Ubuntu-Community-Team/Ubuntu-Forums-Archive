---
title: "Compaq Presario V3118AU wireless issues"
date: 2006-11-29
forum: Networking &amp; Wireless
---

### Post by ozPATT on 2006-11-29
hi all, 

I just bought a Compaq Presario V3118AU, and I want to run Ubuntu on it. 

I am trying to set up the wireless bit, and not having much joy. assuming this might be due to lack of drivers or something? 

I have gone into networking, and enabled the wirless device, providing the SSID and the password. 

But when I go into Network Tools, I have no option there to use it. 

I have gone into the devices and it seems to say (im not too sure...) that the WLAN Interface is from Broadcom Corporation and is PCI Bus Type. 

Please could someone tell me if it is possible to run wireless internet through Ubuntu on this computer, and if so, how I can get it to work? 

Many thanks

Patrick

---

### Post by woopud on 2006-11-29
I used this how to to set up mine.
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
Bert

---

### Post by ozPATT on 2006-11-29
hi, thanks for that. I have just gone through the how to, and I must be nearly there! haha... in the network tools, eth1 now shows, and when i use iwconfig it tells me that eth1 is wireless. 

but... I can't seem to select it by clicking on the network icon at the top of the screen. i have been in networking, and enabled it, it is sending and receiving packets, and wireless is switched on on the laptop. 

It doesn't seem to put 2 and 2 together... any ideas? 

thanks for the help so far

also, when i do iwlist, it picks up the wireless signal, so i guess my only issue is actually connecting to it...

---

### Post by twade on 2006-11-29
I'm not sure how similar mine is to yours (Presario V3010CA, NVidia with Broadcom BCM4311). Check for details at the link
[http://www.ubuntuforums.org/showthread.php?t=193350&highlight=4311](http://www.ubuntuforums.org/showthread.php?t=193350&highlight=4311)
If your's has the Broadcom BCM4311 card (you can check using the output from lspci) you'll have to use ndiswrapper and not the BCM43xx driver installed by default (the bcmwl5.inf driver on the link worked, the one that came with my computer didn't). Also you may have to remove previous attemps first (instructions about 3 posts down in the link)

Once I had ndiswrapper installed I found that connecting to some networks was a little sketchy using the GUI interfaces or the /etc/network/interfaces file so I wrote some scripts that appear to work.
eg:

```

ifconfig wlan0 down
iwconfig wlan0 essid XXXXX
iwconfig wlan0 key open XXXXXXXXXX
ifconfig wlan0 up
dhclient wlan0
```

I find this setup works quite well with Dapper, but when I tried upgrading to Edgy it was constantly going down or not coming up at all.  It might have been a conflict between the NVidia drivers and ndiswrapper as discussed in this thread:
[http://www.ubuntuforums.org/showthread.php?t=306569](http://www.ubuntuforums.org/showthread.php?t=306569)
I don't know. I gave up and went back to Dapper.

Good luck!

---

### Post by twade on 2006-11-29
I should also add, that from your post it looks like you are likely using edgy.  There may also be a problem with the wireless getting assigned to eth1 rather than wlan0.  Check for more details in this thread:
[http://www.ubuntuforums.org/showthread.php?t=278441&page=3&highlight=edgy+bcm4311](http://www.ubuntuforums.org/showthread.php?t=278441&page=3&highlight=edgy+bcm4311)

---

### Post by cnajova on 2006-11-29
Hi. I was trying to post a messege in the bug report, but I'm not usre how. I have a Com[aq V2718WM with the same type of wireless card. What I have figured out is to make this card work for me , I had to compile a new kernel with wireless and pcmcia support, and also misc binnary support. Then i had to build the kernel with direct (make modules_install install). It seems the kernel-package will not install the libraries needed to make the wireless devices. Also I compiled a ndiswrapper package from source. This should get You up and working. After I installed. I edit the /etc/modprob.ed/alias, changing the wlan0 entry to eth1 caused the led to be displayed after the next reboot. Kernel-2.6.18.3.  This should work for Edgy. [email]cnajova@yahoo.com[/email]  Be sure when you compile the new kernel, only include wireless support. Don't select any modules.

---

### Post by ozPATT on 2006-11-29
hi, thanks for the info, am i really that far from being sorted :s it seems so close, being that it is picking up the signal when i scan, and it is showing in the networking tools and networking bit. 

:( 

i am still very much a noobie to linux, so I'm afraid comiling a new kernel is about as understandable as chinese :s

using lspci, it shows my network controller as Broadcom Corporation Unknown Device 4311. does that mean it is the same as yours, twade?

---

### Post by FrodoB on 2006-11-29
Detailed instructions for bcm4311 and ndiswrapper on a Presario laptop:

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

---

### Post by ozPATT on 2006-11-29
it works! :D i downloaded network-manager, and then rebooted. got the little icon next to the network one, and although it doesn't connect automatically, if i manually click on the manager and connect, it works :D 

thanks for the help! :D im a happy ubuntu-er :D

---

### Post by twade on 2006-11-30
I forgot about that link FrodoB, it is a good summary.  I did in fact try following it when I tested out Edgy, but still couldn't get connected consistently.  I hope you have better luck with Edgy than I did ozPATT.  Please let me know whether wireless turns out to be stable for you and and whether you did anything different and I might try upgrading again in the near future.

---

### Post by twade on 2006-11-30
4311 is the same as mine.

---

### Post by ozPATT on 2006-12-05
> **twade said:**
> I forgot about that link FrodoB, it is a good summary.  I did in fact try following it when I tested out Edgy, but still couldn't get connected consistently.  I hope you have better luck with Edgy than I did ozPATT.  Please let me know whether wireless turns out to be stable for you and and whether you did anything different and I might try upgrading again in the near future.

well, so far, it seems relatively stable. I find that it wont connect automatically. I need to manually connect each time I boot, but once it is connected, I am not having any issues.

---

### Post by FrodoB on 2006-12-06
Maybe this bit of information that was added to the wiki entry:

sudo gedit /etc/modules
Add the word **ndiswrapper** and save the file using "save as" this will then load everytime you boot

---

