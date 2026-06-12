---
title: "Installing WG311T on Ubuntu Server 6.06 LTS"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by nicolasdiogo on 2007-02-22
hi,

i have red a lot on how to install the drivers for the netgear WG311T (Atheros based card by all accounts) on a 64bit Ubuntu Server 6.06 LTS.

i have followed the steps described on Madwifi website religiously.
but not matter what the card never gets recognised.

[http://madwifi.org/wiki/UserDocs/Distro/Ubuntu]("http://madwifi.org/wiki/UserDocs/Distro/Ubuntu")

i have the ath_pci module listed on my linux-restricted-modules-common.  and i have removed it (rmmod ath_pci) and deleted the recomended folder /lib/modules/<linux-kernel>/net

i just have run out of ideas, and would really like some assistance on this one.

thanks in advance,

Nicolas

---

### Post by ubuntu_demon on 2007-02-22
I wanted to suggest to install the restricted modules. But you are running 6.06 LTS server. 

So you should take a look here :
[https://help.ubuntu.com/community/Router/Madwifi](https://help.ubuntu.com/community/Router/Madwifi)

---

### Post by ubuntu_demon on 2007-02-22
I'm very interested in your results. I hope you get WPA2 personal running with CCMP/AES. I'm searching for a wireless card myself see :
[http://www.ubuntuforums.org/showthread.php?t=363633](http://www.ubuntuforums.org/showthread.php?t=363633)

the netgear WG311T is one of the candidates

---

### Post by nicolasdiogo on 2007-02-22
thanks,

it seems to be configured. i mean that iwconfig shows the card:

i am now tryiing to configure WPA1.

any suggestions that may help me?

nicolas

---

### Post by nicolasdiogo on 2007-02-22
i tried the information from here

[http://madwifi.org/wiki/UserDocs/WPA_PSK_on_Both_Ends#TheStationclientSide]("http://madwifi.org/wiki/UserDocs/WPA_PSK_on_Both_Ends#TheStationclientSide")

but the card only return error on the screen.

any idea?  how can i retrieve the error to post it here?

thanks

Nicolas

---

### Post by nicolasdiogo on 2007-02-26
Hi,

it has installed without a glitch..
i am now connecting via WPA2 and another pc is using WEP.

the WPA2 is a ubuntu 6.06 server 64bit and WEP is in 6.10 desktop.

i suppose i have messed so much with the installation that something was failing when compiling the driver.	:-({|=
i reinstalled the kernel source and build-essential packages, and compiled without any error. :) 

so i would recomend this card.

thanks for your assistance,

Nicolas

---

### Post by Spr0k3t on 2007-02-26
I have this same card and recommend it.  I'm using it with Edgy Eft 64bit and it works out of the box.  WPA2 was a little more work to set, but everything is smooth now.  Feisty should be really interesting with the inclusion of network-manager and all.

Oh yeah, get a D-Link ANT-24 to extend the range quite a bit... connects right up.  Went from 22% signal strength @120' to 48% signal strength with no other change the environments... your mileage may vary of course.

For those interested: [http://www.newegg.com/Product/Product.asp?Item=N82E16833127063](http://www.newegg.com/Product/Product.asp?Item=N82E16833127063)

---

### Post by ubuntu_demon on 2007-03-01
great :)

---

