---
title: "Atheros AR5006eg / installing Madwifi"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by aaron100 on 2008-11-13
I recently downloading ubuntu onto my laptop as Vista was annoying me and my wireless card has stop working so i've looked around and found that the easiest way is to install madwifi.
I've downloaded madwifi and unpacket it but i have no clue how to install it since i'm a newbie to ubuntu.

Could anyone give me any advice on this or the easiest way to get my Atheros AR5006eg wireless card working.

---

### Post by mattlb0619 on 2008-11-13
ive got a atheros ar5007 on a pavilion dvv9720us, i believe we need the same thing.

cant get wifi working...  search lead me to, [http://madwifi-project.org/ticket/1192](http://madwifi-project.org/ticket/1192) but it is greek to me as i havent been using ubuntu but like 5 hrs.

please walk us through installing this.

thanks

---

### Post by eks on 2008-11-13
First, go to System/Administration/Hardware Drivers. Try to activate "Support for Atheros 802.11 lan cards", then reboot. If this does not work, try the first paragraph of this wiki page:

[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

Which, translated in small steps is:

. open System/Administration/Synaptic Package Manager
. search for "backports"
. install the package "**linux-backports-modules-intrepid**" (mark it for download and click Apply)
. go into System/Administration/Hardware Drivers
. Activate "**Support for 5xxx series of Atheros 802.11 wireless lan cards**"
. make sure "Support for Atheros 802.11 lan cards" is **NOT** activated
. reboot

Just to explain what's happening, you are installing a package (linux-backpors-modules-intrepid) that has newer versions of drivers, released from madwifi and maintained by Ubuntu developers. They are supposedly stable, but don't have 6 months of testing like most parts of Ubuntu. It can also be installed manually, following the steps on the second part of that wiki. This newer version is called "ath5k" (the one in "support for 5xxx series..."). If you tried to install the driver manually, you might probably have to do some manual cleaning which is listed on the [wiki]("https://help.ubuntu.com/community/WifiDocs/Driver/Atheros").

Either way, none of that is difficult. Linux is all just a bunch of text files that you can open and change from anywhere. ;)

---

### Post by mattlb0619 on 2008-11-13
there is no 'linux-backports-modules-intrepid' listed...

---

### Post by eks on 2008-11-13
> **mattlb0619 said:**
> there is no 'linux-backports-modules-intrepid' listed...

Are you sure you have installed Ubuntu 8.10 (Intrepid)? Not 8.04 (Hardy)?

Also, try the Search button, not the Quick search. It must be there.

---

### Post by mattlb0619 on 2008-11-13
its  hardy not 8.10...

edit: 
i cant even get ktorrent installed

---

### Post by eks on 2008-11-13
> **mattlb0619 said:**
> its  hardy not 8.10...

Ugh... :(

I'm sorry, this solution won't work then. You still have many options though:

1) install the driver manually, which means download the code and compile it (it's not that difficult, but if it's your first time it might demand some patience and some minutes).

2) plug an ethernet cable to your laptop and upgrade Hardy to Intrepid, and try to make it work through the interface (as mentioned above).

3) download Intrepid, burn into a CD and completely reinstall the system, and do the steps above.


You can try 2 and then 3 if it doesn't work.

---

### Post by mattlb0619 on 2008-11-13
thanks for the help i thinkill just upgrade

---

### Post by mattlb0619 on 2008-11-13
i can find the network now but i cant login to it. im using WEP/TKIP and i know the key im entering is correct... so whats up? it just keeps wanting me to put the key in.

---

### Post by cipher_neo on 2008-12-01
hey guys im having some difficulty getting wireless to work on my samsung nc10 with intrepid. I really need some assistance, i have been at it for days.

I blacklisted the following in /etc/modprobe.d/blacklist

ath_pci
ath_hal

and did sudo apt-get install linux-backports-modules-intrepid

then i made sure that the driver was enabled (the "support for 5xxx" etc) and not the default one.

Still i get no connectivity... 

is there any gurus willing to give a helping hand, much appreciated!

---

### Post by cipher_neo on 2008-12-02
Hey guys i solved the problem, it was due to the fact that in /etc/modprobe.d/madwifi there was a line

blacklist ath5k

i commented out this line and all is well in the world of wireless

---

### Post by frishkorn on 2009-03-22
I'm using a Atheros AR242 (AR5007 I believe) internal on a ASUS Eee PC 701. I was able to disable the default Atheros driver and install linux-backports-modules-intrepid. I'm able to access my wireless router but it seems the ubuntu is not receiving DNS information.

Anyone had similar problems and knows of a fix?

---

