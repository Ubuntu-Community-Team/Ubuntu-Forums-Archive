---
title: "intel 3945 drivers"
date: 2006-12-05
forum: Networking &amp; Wireless
---

### Post by J03 on 2006-12-05
I cannot figure out why my wireless doesn't work. I tried searching the forums for possible solutions, but none of them seem to work. I am thinking i need an updated driver for my intel pro/ve 3945ABG. Thanks

---

### Post by handaxe on 2006-12-05
```
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```

I think not... the above comes from my laptop and my wireless works fine.

Dapper and Edgy both picked it up just fine.

Does the card work under Windows? (ie. do you know it works independently of Linux?)

Do you see the card in the output of ```
lspci
``` and the module with  ```
lsmod | grep 3945
```?

Also ```
ifconfig
``` - does this show the interface at all?

Any clues in /var/log/messages  ?

HA

---

### Post by Greguti on 2006-12-05
Hi,

upgrading from Dapper to Edgy, I found that my i3945 wireless card didn't work in Edgy. But it was working good on Dapper.

I found out how to fix it. At least it worked for me:

1 - make sure the package *linux-restricted-modules-generic* is installed. If not, just type the following command:

```
sudo apt-get install linux-restricted-modules-generic
```(this package contains the driver for this card, afaik.) Reboot your ubuntu.

2 - In Edgy, there is a bug with the Network Monitor utility, it doesn't display the Wifi networks available around your computer... So you need to install the package *wifi-radar* :

```
sudo apt-get install wifi-radar
```

Once it's installed, launch it, and you can see all the wifi networks around you. You can either manage your connexion inside wifi-radar, or copy the name of your wifi network in the Network Monitor utility (type it in the ESSID entry, then type your WEP key).

It worked well for me... Hope this helps.

Regards

Greg

---

