---
title: "Simple wireless bridge (diy)"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by marks256 on 2008-05-27
So, here is my problem...

My workshop is in my basement, but we only have internet on the top floor of our home (2 story home + basement). :(

I cannot run a cable, or my mum would shoot me... :D

So, since i have wireless in my home, i was wondering if it would be possible to "forward" the network connection on a machine with wireless (running ubuntu. probably 8.04), to an Ethernet card, and run the ethernet card to a router, to use for all my computers in the basement?

In other words forward the wireless to the ethernet, then to a router. or i could even add a bunch of ethernet cards to the linux box and just call that the router. I dont' need any security on this box, so it could even be configured as a hub.

I have attached a picture of what i mean.... Sorry for the low quality; first time using the gimp... :D


Thanks guys! No REAL rush on this. However, sooner would be better than later. ;)

[edit]
basically i want to make one of these [http://cgi.ebay.com/Linksys-Wireless-G-Ethernet-Bridge-WET54G_W0QQitemZ250250457329QQihZ015QQcategoryZ67250QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.com/Linksys-Wireless-G-Ethernet-Bridge-WET54G_W0QQitemZ250250457329QQihZ015QQcategoryZ67250QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)
[/edit]


Thanks
-Marks256

---

### Post by AliTabuger7 on 2008-05-28
I would say that this should be possible.
I haven't tested it, but I have read a little about it.

The easiest way would probably be to install the package called "firestarter". It is a firewall program that also allows you to easily set up internet connection sharing.

You should be able to follow this tutorial:
[http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php)

Your external device will probably be wlan0 and your internal device will probably be eth0.

If that doesn't work, you may need to either install some of the DHCP packages as well, or use a static IP configuration. Both methods I believe are available in that tutorial.

---

### Post by marks256 on 2008-05-28
Ok. Cool.

I will go get a box and load ubuntu on it. Hopefully it will work. :)

---

### Post by marks256 on 2008-05-30
Didn't work. :( The box i was going to use didn't like linux, so i tried windoz. Let's just say windoz' repuation held up... it didn't work either.

What ever. I will just run a cable... Mum will have to live with it. Dad said it was fine... :D

Thanks for the help anyway. ;) :guitar: (sorry, i just wanted to use that smiley....:D)

---

### Post by kevdog on 2008-05-30
You can definitely do what you want with bridging.  However I found it much easier my self to do the following:

Buy 2nd router wrt54gl -> flash with dd-wrt firmware and set for repeater bridge. 
[http://www.dd-wrt.com/dd-wrtv3/index.php](http://www.dd-wrt.com/dd-wrtv3/index.php) 

Equipped router #1 and #2 each with winsurfer antenna: [http://www.freeantennas.com/projects/template2/index.html](http://www.freeantennas.com/projects/template2/index.html)

Again the router cost me about $60 dollars -- might find it cheaper on sale or on internet, but the features of dd-wrt are amazing and well worth it!

---

