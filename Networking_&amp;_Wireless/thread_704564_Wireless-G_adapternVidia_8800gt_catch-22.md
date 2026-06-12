---
title: "Wireless-G adapter/nVidia 8800gt catch-22"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by iBuntuKnow on 2008-02-22
Well, first off I'm very much a Noob when it comes to Ubuntu...so much so that ive basically only known about the program for a grand totall of 48hours

and within 8 of those hours I managed to find, download, burn, bootup and install a fresh copy of Ubuntu (7.10)...and since then I have been  spending the rest of those 48 hours trying to figure out just what in hell I got myself into

anyways, I digress

So far as i can tell I've got myself two major problems that need some immediate fixin', and they are as such:

My video card and my wireless card

Now, heres the catch:

In order for me to get my 8800 gt graphics card installed and going, I need a "program" called "Envy", which sounds like it, when enabled, finds the appropriate drivers for my card and installs them for me...or something...but in order for Envy to do that, I need atleast some sort of internet connection...and in order for me to get an internet connection, I've got to get my Wireless card up and running...and that has proven to be difficult

This is the exact wireless card I have(Linksys Wireless-G PCI adapter with SRX 2):

[http://www.hitecempire.com/catalog/images/Linksys_WMP54GX.jpg](http://www.hitecempire.com/catalog/images/Linksys_WMP54GX.jpg)

Slightly different than most of the posts ive seen regarding this product (wireless-g and whatnot)...same name...different hardware

or so I think..

at any rate, I have tried various solutions brought up in other forums similar to mine, with both the Wi-fi card and Graphics card...for instance this one for the GPU: 

[http://ubuntuforums.org/showthread.php?t=694846](http://ubuntuforums.org/showthread.php?t=694846) 

...and these two for the wi-fi card: 


[http://ubuntuforums.org/showthread.php?t=621088&highlight=wmp54gx](http://ubuntuforums.org/showthread.php?t=621088&highlight=wmp54gx)

[http://ubuntuforums.org/showthread.php?t=581406](http://ubuntuforums.org/showthread.php?t=581406)


...but to no avail :(


now be honest, am i doomed? :confused:

Please understand that I am very new to Ubuntu (or Linux in general for that matter) and its terminal feature,  as well as all the various jargin involved, so most of the time I have absolutely no idea what those people in other forums are talking about...grub? xserver? sudo?...its all greek to me

but -sigh-...I am willing to take the time and learn...for now

so far, trying to escape the corporate claws of the M$ monster has been a real bitch lol



Thanks in advance though, for any help given,

Aaron

---

### Post by iBuntuKnow on 2008-02-22
geez...anybody?

---

### Post by Ayuthia on 2008-02-22
Do you have the Linksys drivers?  If so, you should be able to use the Gutsy CD to install ndiswrapper-common and ndiswrapper-utils-1.9 by using Synaptic.  From there, you should be able to follow the steps in the link that you posted:
[http://ubuntuforums.org/showthread.php?t=694846](http://ubuntuforums.org/showthread.php?t=694846)

---

