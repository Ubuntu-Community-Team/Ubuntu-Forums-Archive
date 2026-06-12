---
title: "[SOLVED] WireLess card will not work"
date: 2008-06-01
forum: Networking &amp; Wireless
---

### Post by Hyper Tails on 2008-06-01
I have Problems with my wireless card 
it works in my windows vista os
but not in hardy.:confused:

When i'm in my hardy os I have to put a ethernet cable in the laptop (pain in the butt)and I was woundering how to get it working

Wireless card:Atheros AR5007EG Wireless Network Adapter
Laptop:Acer Aspire 5715-4740

---

### Post by pytheas22 on 2008-06-01
Take a look at [http://ubuntuforums.org/showthread.php?t=766169](http://ubuntuforums.org/showthread.php?t=766169) .  Apparently you're not the only one having trouble with this card, but the fix looks simple.

---

### Post by Hyper Tails on 2008-06-03
thanks i've got it working but theres only one problem

How do i make it find the driver?

---

### Post by pytheas22 on 2008-06-03
> How do i make it find the driver? 

I'm not sure what you mean.  If your wireless connection is working now using ndiswrapper, which driver do you need to find?

---

### Post by Hyper Tails on 2008-06-07
I need to find my wireless driver

---

### Post by pytheas22 on 2008-06-07
> I need to find my wireless driver

If the card is working right now, you don't need to find a driver; it's already working.  Do you have a wireless Internet connection right now under Ubuntu?

If you mean that your wireless card still doesn't work and you're trying to figure out which Windows driver to use with ndiswrapper, I can help you.  But please clarify, as I'm still confused regarding what you need help with.

---

### Post by Hyper Tails on 2008-06-07
okay this is what i mean

---

### Post by pytheas22 on 2008-06-07
Thanks for the information; I understand the problem now.

Download the driver from [http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz) .  Extract it (right click and select "extract here"), then navigate to the file net5211.inf inside /ar5007eg-32-0.2/ar5007eg/ .  That's the file you want.

---

### Post by Hyper Tails on 2008-06-11
okay i got it but how do i make detect my networks

---

### Post by pytheas22 on 2008-06-11
Try typing:
```

sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
```

and see if you can connect after that.  If it still doesn't work then, please post here the output of:
```

iwconfig
cat /etc/modprobe.d/blacklist
ndiswrapper -l
```

---

### Post by Hyper Tails on 2008-06-11
It still won't detect any networks what do i need to install

---

### Post by pytheas22 on 2008-06-11
Please post the output of:
```

iwconfig
cat /etc/modprobe.d/blacklist
ndiswrapper -l
```

so that I can figure out why it's not working.

---

### Post by Hyper Tails on 2008-07-04
I built a desktop 2-3weeks ago and  i installed vista and hardy and my motherbord came with a wireless adapter and It works just fine.

My goal is to get my laptop one working.

Any software out there would do the trick?

---

### Post by pytheas22 on 2008-07-05
Unfortunately there's no single software that's going to solve the problem.  From the information you posted a few weeks ago, your wireless should be working, so there must be a problem somewhere preventing it from doing so.

Please post the output of these commands so that we can find the problem:
```

iwconfig
cat /etc/modprobe.d/blacklist
ndiswrapper -l
lshw -C Network
iwlist scan; iwlist scan
dmesg
```

---

### Post by Hyper Tails on 2008-07-07
this is what i got while doing it

Sorry about the compiz fusion effect

---

### Post by pytheas22 on 2008-07-08
ndiswrapper thinks everything is ok, but it's not claiming your wireless card for some reason.  Are you using 32-bit or 64-bit Ubuntu?  If you're on 64-bit, let me know, as that will explain the problem and I can tell you how to solve it.

Also, make sure that ndiswrapper is loaded (it should be automatically but there may be a problem):
```

sudo modprobe ndiswrapper
```

then wait a few seconds and see if your wireless card works.

Otherwise, this command will force ndiswrapper to try to drive your card:
```

sudo ndiswrapper -a 168C:001C net5211
```

But the ndiswrapper manual page warns that that can be dangerous (it could damage your wireless card).  I used it once and it didn't hurt anything, but do it at your own risk.

---

### Post by Hyper Tails on 2008-07-21
here what i got from it.

---

### Post by pytheas22 on 2008-07-23
Very strange...I'm still not sure what's going on.  From everything I see, ndiswrapper should be working.  Would you mind posting the output of these commands please (in this order):
```

sudo modprobe ndiswrapper
iwconfig
lshw -C Network
```

---

### Post by Hyper Tails on 2008-07-27
I just discovered i'm using the 64 bit versoin of ubuntu from installing virtual box and the 32 bit one didnot work but the 64 one did.

i haven'y tried that code you gave me yet because i was away for a couple of days but i'l try it soon.

do i need to update mt system in order for this to work?

---

### Post by pytheas22 on 2008-07-27
Alright, that explains a lot...the Windows drivers that you load into ndiswrapper need to be for the same architecture as your Linux kernel--so you need 64-bit Windows drivers if you're on 64-bit Ubuntu.  Remove the Windows drivers that you currently have--you can use the GUI or the command:
```

sudo ndiswrapper -r net5211
```

then download the 64-bit version of the Windows driver from [http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz) and install it into ndiswrapper.

---

### Post by Hyper Tails on 2008-07-29
got it working !!!111!!! 
Thanks.

Question: if i need to reinstall ubuntu for any reason how do i get this menu back so i can tell it to use my wireless card again 
heres what i mean 

[http://ubuntuforums.org/attachment.php?attachmentid=73323&d=1212891748](http://ubuntuforums.org/attachment.php?attachmentid=73323&d=1212891748)

---

### Post by pytheas22 on 2008-07-29
I'm glad you finally solved the problem.

That menu is a program called "ndisgtk" and is a graphical front-end to ndiswrapper; packages for it are available on the Ubuntu live CD and in the online repositories.  To install it, just type:
```

sudo apt-get install ndisgtk
```

(or you could use System>Administration>Synaptic Package Manager if you want to install it without using the command-line)

Before you run that command, make sure that either 1) you have an Internet connection or 2) your Ubuntu CD is in the drive and is enabled to be used a repository (go to System>Administration>Software Sources to make sure it's enabled).

---

### Post by Hyper Tails on 2008-07-29
it detects my wireless access point but when i try to connect to it and it will never be sucessful

will any codes help?

---

### Post by pytheas22 on 2008-07-29
What is the output of:
```

iwlist scan
```

Also, you could try using wicd to connect instead of Network Manager.  wicd is another connection manager that sometimes works better.  You can install wicd from [here]("https://sourceforge.net/project/downloading.php?group_id=194573&use_mirror=voxel&filename=wicd_1.4.2-1-all.deb&32524844").

If wicd doesn't allow you to connect, there are some other things to try, but first I'll need to see the output from "iwlist scan."

---

### Post by Hyper Tails on 2008-07-29
I got to work now!!

many thanks goes out to you. ;)

---

### Post by pytheas22 on 2008-07-29
Nice; glad it's working finally.

Just in case anyone else has a similar problem as you, what exactly did you need to do to make it connect?

---

### Post by Hyper Tails on 2008-07-29
i just typed in iwlist scan and tryed again

---

