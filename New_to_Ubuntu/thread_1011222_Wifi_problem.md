---
title: "Wifi problem"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by Hellno on 2008-12-14
Hi

I've just installed linux ubuntu, i have a compaq presario CQ60, and i'm having problems with the wireless.. i just can get it to work..

Also, whenever i install a new package it ends with an error, and when i restart my computer like it tell&#347; me i should the screen stay's black, and it doesn quite restart.. I'm a little desperate..:S

---

### Post by Michael.Godawski on 2008-12-14
hi Hellno, 

let's start with the wlan, shall we?
Please open the terminal 
applications > accessories > terminal 
run these commands and put the output her:

```
sudo lshw -C network
iwconfig
```

Concerning the black screen... check if your graphic card drivers are active in
system > administration > hardware drivers.

---

### Post by HotShotDJ on 2008-12-14
> **Hellno said:**
> I've just installed linux ubuntu, i have a compaq presario CQ60, and i'm having problems with the wireless.. i just can get it to work..What wireless card/chipset?  Without that information, we have no idea what to do.  To find this information, from a terminal (Applications --> Accessories --> Terminal) type```
sudo lshw -C network
```
> **Hellno said:**
> Also, whenever i install a new package it ends with an errorWhat is the exact error message?

---

### Post by Hellno on 2008-12-14
ok, done...

oh, yeah, i have an atheros 802.11..

---

### Post by Michael.Godawski on 2008-12-14
> ok, done...

oh, yeah, i have an atheros 802.11.. 	
:p
Are you able to copy and paste the exact wording of the output? Do you have a working wired internet connection on the Ubuntu machine?

Only guessing so far; have a look at:


[LIST]
[*][https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)
[/LIST]

---

### Post by Hellno on 2008-12-14
-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2a:9f:1f:a8:0e:fd
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


here it is..
ok, i&#7743; looking..

---

### Post by porchrat on 2008-12-14
For future reference, this is the name of your card: AR242x

Lucky for you there are quite a few drivers out there, personally I use the compat-wireless drivers, but quite frankly there are so many guides for the AR242x that you should just do a search for AR242x or AR5007 on these forums (another name given to that card by ubuntu) and you'll be swimming in helpful advice.

---

### Post by Hellno on 2008-12-15
Hello again.

i've tried to follow steps of another posts, but my wifi insists in not to work....

plus, when i try to install linux-backports-modules-intrepid, like i saw in a threat, in returns the following error:
Errors were encountered while processing:
 linux-image-2.6.27-7-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

and i think the same thing keeps returning whenever i try to install anything..

---

### Post by porchrat on 2008-12-17
> **Hellno said:**
> Hello again.

i've tried to follow steps of another posts, but my wifi insists in not to work....

plus, when i try to install linux-backports-modules-intrepid, like i saw in a threat, in returns the following error:
Errors were encountered while processing:
 linux-image-2.6.27-7-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

and i think the same thing keeps returning whenever i try to install anything..

Then try ```
sudo apt-get install dpkg
```

---

### Post by lovelyvik293 on 2008-12-17
For AR242x just have a look on this:-
[http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html)

---

