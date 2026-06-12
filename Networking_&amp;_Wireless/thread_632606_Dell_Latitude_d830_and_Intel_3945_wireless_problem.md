---
title: "Dell Latitude d830 and Intel 3945 wireless problem"
date: 2007-12-05
forum: Networking &amp; Wireless
---

### Post by mblind on 2007-12-05
Hello,
 I have a Dell Latitude D830 with a built in Intel 3945 wireless controller. 

Here is my problem.. I can connect to a wireless access point if a WEP password is not required. BUT if there is a WEP password (Which is everywhere) I am unable to connect.. I have used the standard restricted driver as well as trying this:

[http://ubuntuforums.org/showthread.php?t=595060](http://ubuntuforums.org/showthread.php?t=595060)

But other than improving a dropped signal I am still not able to connect.. Anyone please help. I have looked all over the forums and nothing is helping.

---

### Post by stlcoptony on 2007-12-05
I'm having the same problem. When I put "lsmod | egrep 'module|iwl|ipw" into the terminal, it tells me that only the iwl3945 and iwl3945_mac80211 is loaded, but when I try to connect to my network (NetworkManager shows the ssid as available, no encryption, which is correct), it never connects. anyone have any other suggestions?

thanks

---

### Post by mblind on 2007-12-05
I swear that this point I would rather just DISABLE the Intel 3945 and use a (pcmcia) pc card.. anyone know a good one for 7.10?

---

### Post by stlcoptony on 2007-12-05
> **mblind said:**
> I swear that this point I would rather just DISABLE the Intel 3945 and use a (pcmcia) pc card.. anyone know a good one for 7.10?

I second this. If there is one that doesnt cost too much and won't stick out too far, I would go for it. I'm assuming that if I turn off the hardware switch for the internal card, upon installation ubuntu would detect the pcmcia card...? Otherwise, does anyone know how to get this card working? I even read through the dell wiki and tried that, to no avail!

thanks

---

### Post by mblind on 2007-12-05
I see that the SMC SCMWCBT-G (You can buy it a newegg.com for 26 bucks)
works great under linux.. you would use the madwifi.org drivers.

But I don't know how to disable the build in Intel.. ANYONE?

Also, Is there any better place to get Ubuntu Support?? It's hard to know if anyone is going to answer your questions here.. Sometimes yes, Sometimes no..
It doesn't make for the best user experience.. Ya know?

---

### Post by tturrisi on 2007-12-05
I haved a dell d830 that I ordered w/ a dell 1390 wifi instead of the Intel wifi because the intel 3945 linux drivers are still pretty bugged.  I used the dell 1390 for a week w/ the bcm43xx drivers and it worked well.  But I wanted an atheros chipset so I bought this one and it is awesome:
[gigabyte W101GT]("http://www.oxfordtec.com/us/MiniPCI-EXPRESS-Wireless/c42/p113/GIGABYTE-WI01GT-miniPCI-EXPRESS-Wireless-card---Atheros-Super-G-108-Mpbs-AR5005GS-mini-PCI-E,-mPCIe-adapter/product_info.html")

It's real easy to install in the d830, just d/l the service manual for the laptop from dell support and follow the direction on removing the necessary parts.  Took 10 minutes tops to swap the cards.

I have a writeup for linux on the d830 here:
[http://members.cox.net/tonyt/d830](http://members.cox.net/tonyt/d830)

---

### Post by mblind on 2007-12-05
Cool, I just order that exact model.. Thanks for the reply.. Great price as well..

---

### Post by mblind on 2007-12-06
How would you remove the 3945 drivers and use the new wireless card? (gigabyte W101GT) 

Also, Would madwifi.org be a good choice for a driver for the gigabyte card?

---

### Post by tturrisi on 2007-12-11
There are 2 antenna leads on the pciE card.  When connecting them to the new card, make sure they get attached snug.  You'll feel them "snap" into place.  When done, put a piece of elec tape over the connections and card to ensure that they stay fastened when mobile.

And before you replace the card, install the madwifi drivers else you'll have to use a wired connection to install them.  DON'T use the Ubuntu madwifi package, use the latest madwifi-ng and install it like this in a ROOT terminal:
```
apt-get install subversion
apt-get install build-esential
apt-get install linux-headers-`uname -r`
cd /usr/src
svn checkout http://svn.madwifi.org/madwifi/trunk/ madwifi-ng
cd madwifi-ng
make
make install
depmod -ae 
```

---

### Post by mblind on 2007-12-12
wow, thanks..

---

### Post by FoxOne on 2007-12-12
I have the same laptop, I downloaded the driver from intel and it worked fine with the wrapper.

---

