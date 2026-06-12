---
title: "Wireless Broadcom 4318 on Feisty"
date: 2007-05-26
forum: Networking &amp; Wireless
---

### Post by taphos on 2007-05-26
Wireless card Broadcom 4318 worked perfectly on Edgy using ndiswrapper+bcmwl5.inf

But after upgrading to Feisty it just stopped working.

```
lspci
``` displays the card name!

```
ndiswrapper -l
```
still says that driver is installed and hardware is present!

ndiswrapper module loads successfully on computer startup

```
dmesg
```
2 lines appear regarding ndiswrapper driver
```
[ 9382.624000] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[ 9382.688000] usbcore: registered new interface driver ndiswrapper
```

But new network interface does not appear :sad:
```
iwconfig
```
says "No wireless extensions" for all interfaces.

Please HELP! I spent many hours searching for the roots of the problem, but no luck ](*,)

P.S.
I also tried using bcm43xx driver with firmware retrieved with bcm43xx-fwcutter
It worked but was unstable. I was able to connect to non-secured wifi network. 
But encrypted connection was not working.

---

### Post by Kobalt on 2007-05-26
Did you use Network-Manager in Edgy ? If not, then you should know this : Feisty uses NM as default to manage networking. If you didn't use it in Edgy, then you must have edited the /etc/network/interfaces file. But NM needs this file to be almost blank in order to manage properly your network. So you have two options : either you want to use NM, in this case comment (put a # at the begining of the line) anything but the *lo* section in /etc/network/interfaces. After this (and maybe a reboot), NM should work properly and you'll be able to set up everything from there. 
The other option is to remove NM, and keep on using the network monitor applet and /etc/network/interfaces as is.

---

### Post by taphos on 2007-05-26
Feisty Network Manager works ok with wired network.
It also displays the list of available wireless networks with bcm43xx driver.
So I dont think that my /etc/network/interfaces or NM causes the problem.

Thanks anyway.

---

