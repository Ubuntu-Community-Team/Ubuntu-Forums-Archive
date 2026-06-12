---
title: "Install wireless network on Fedora 10"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by mrdosa on 2009-03-16
Hi! I have a HP Pavilion dv4-1124nr laptop, and I dont have a wire connection. I have another lappy which I use to connect to the internet via wireless. i would like to install wireless on my hp pavilion. I recently installed fedora 10 on it. I know, this is not the place, but I have a ubuntu user for long, but this thing i am unable to find any answer to. I can download packages on other pc, and use it on  this one.
Please help me out
Thanks

---

### Post by skymera on 2009-03-16
Well, I've never used RedHat based systems before.

But a good place to start is telling us what your wireless card is.

---

### Post by mrdosa on 2009-03-16
Hi! Its a broadcom b43 wireless card 802.11 b g

---

### Post by skymera on 2009-03-16
Is this a PCI card? If so can you post the output of this:

```
 lspci 
```

**If** USB:

```
 lsusb 
```

and finally do this

```
 iwconfig 
```

---

### Post by Dynaflow on 2009-03-16
Try starting here:  [http://forums.fedoraforum.org/showpost.php?p=1177687&postcount=2](http://forums.fedoraforum.org/showpost.php?p=1177687&postcount=2)

---

### Post by mrdosa on 2009-03-16
Network Controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

and it says no wireless extensions for lo eth0 and pan0 when i key in iwconfig

---

### Post by Simian Man on 2009-03-16
The package you need is called broadcom-wl from [RPM Fusion]("http://rpmfusion.org/").  Under "Browse available pacakges", choose the entry for Fedora 10, Nonfree, release and either i386 or x86_64 (depending on which you installed).  Then click on 'B' under jump to letter.  Then click on "boradcom-wl".  Then there will be a download link to download the rpm.  Save it to a flash drive to something and transfer it to your Fedora machine.  Then double-click to install with the package manager.  After a reboot, you should be good to go.

Post back with any troubles!

---

### Post by mrdosa on 2009-03-16
Ok.sorry..downloaded the package
But when I double click it, and it starts installing, it stops with an error
An internal system error has occurred
'NoneType' object has no attribute 'getProvides'

---

### Post by Simian Man on 2009-03-16
OK maybe it has other dependencies.  Try installing it directly with rpm on the command line:
```

su -
rpm -Uvh filename.rpm

```

And post the errors if there are any.

---

### Post by mrdosa on 2009-03-16
# rpm -Uvh broadcom-wl-5.10.27.6-3.fc10.noarch.rpm
warning: broadcom-wl-5.10.27.6-3.fc10.noarch.rpm: Header V3 DSA Signature: NOKEY, Key ID b1981b68
error: Failed Dependencies:
    wl-kmod >=5.10.27.6 is needed by broadcom-wl-5.10.27.6-3.fc10.noarch

When I install kmod-wl-5.10.27.6-5.fc10.5.x86_64.rpm I get same error, and the failed dependency is 
its needs kmod-wl-2.6.27.5-117.fc10.x86_64-5.10.27.6-5.fc10.5.x86_64.rpm
and when I install that, it says that it needs the above two files as dependencies
So..its cyclic!!
:(

---

### Post by Simian Man on 2009-03-16
So why not try installing all three with one command:
```

su -
rpm -Uvh broadcom-wl-5.10.27.6-3.fc10.noarch.rpm kmod-wl-5.10.27.6-5.fc10.5.x86_64.rpm kmod-wl-2.6.27.5-117.fc10.x86_64-5.10.27.6-5.fc10.5.x86_64.rpm

```

Hopefully that should work.

---

### Post by mrdosa on 2009-03-16
Hey!
ThANKS MAN!! tHANKS A LOT...I OWE YOU BIG TIME! YOU HAVE MADE MY DAY! tHANKS ONCE AGAIN

---

### Post by Simian Man on 2009-03-16
Alright!!  I am so glad it worked :).  Enjoy your interwebz!


Just so noone gets the wrong idea about rpm: his dependency problem would have been handled automatically had he had internet access.

---

