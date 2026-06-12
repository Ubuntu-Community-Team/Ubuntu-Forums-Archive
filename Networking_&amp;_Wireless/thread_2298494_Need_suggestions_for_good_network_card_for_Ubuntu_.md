---
title: "Need suggestions for good network card for Ubuntu 15.04"
date: 2015-10-11
forum: Networking &amp; Wireless
---

### Post by Nire_Inicana on 2015-10-11
Hello, I have a computer running on Windows 10 along side Ubuntu 15.04. I have to use a wireless network card because where my computer is located I cannot reach a network outlet and moving my computer is not an option. I have tried a few network cards and none of them fully worked.

First I tried a, Encore ENLWI-N | 802.11n Wireless PCI Adapter, there are no linux drivers for this card but some people got it to work with ndiswrapper, but I never have gotten it to work with it.
Second I tried a, Penguin Wireless N PCI Card v5 /w full & low profile, this one worked perfectly until it died. I sent it back to Think Penguin, where I got it from, but haven't heard anything back from them (yet).
Third I tried a, Edimax EW-7722In, this works on windows perfectly, but when I went to install it on Ubuntu it needed a driver so I downloaded the driver and tried to compile it and install it. But I couldn't even compile it because the code and compiler for the driver had so many errors that I couldn't even fix it, by my self.

If some one can find or fix the Linux driver for the third one that I tried for Kernel version 3.6 then that'll be great. But, otherwise can someone give me some suggestion(s) for a better network card that can work on Ubuntu 15.04 and Kernel 3.6 out of the box or with very minimal hassle.

Thanks, 
Nire Inicana

---

### Post by jeremy31 on 2015-10-11
Put the Edimax in and run the wireless script, info [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) post the result

And post where you got the driver from

---

### Post by Nire_Inicana on 2015-10-11
This is the "wireless-info.txt" that was generated from the script.

[ATTACH]264903[/ATTACH]

I bought it from Walmart.

---

### Post by jeremy31 on 2015-10-11
First delete the last two lines from /etc/modprobe/d/blacklist.conf
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

and delete 
```
blacklist rt2800pci
blacklist rt2x00pci

```
Save and exit program
Reboot and run ```
wireless-info
``` and attach the new wireless-info.txt

---

### Post by Nire_Inicana on 2015-10-11
Here are the new and updated wireless-info.tar.gz:
[ATTACH]264904[/ATTACH]

---

### Post by jeremy31 on 2015-10-11
Looks like a working wireless connection to me but it might be helped with ```
sudo ufw disable
```

---

### Post by Nire_Inicana on 2015-10-11
It does work and allows me to connect to my router, but I cannot connect to the internet and I read somewhere that I have to install the driver from Edimax's website to make it connect to the internet.

Edit: I will try "sudo ufw disable" though...

Edit-2: I just disabled ufw and it works! Thank you jeremy31!

---

