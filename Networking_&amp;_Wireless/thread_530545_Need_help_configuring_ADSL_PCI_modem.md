---
title: "Need help configuring ADSL PCI modem"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by bleearg on 2007-08-20
Hi,
I'm trying to configure an ADSL PCI modem that I recently purchased for use with Ubuntu 6.10.  I've gone through many of the similar posts on here and found that either there were no responses to old posts, or the circumstances do not match my setup.  Let me explain what I have.

3com ADSL PCI modem
Ubuntu 6.10
No PPPoE

The modem *appears* to be somewhat recognized when I do a 'lspci':

```
02:09.0 ATM network controller: Alcatel Unknown device 1101 (rev 01)
```

My ISP, who is also my employer, does not do PPPoE.  This means I do not require a username and password when connecting with a regular external ADSL router.  As long as the VPI/VCI and encapsulation are set properly, you can connect.

I'm not entirely sure where to start, as I've never configured an internal ADSL modem before.  Any pointers would be helpful.

Thanks!

---

### Post by linuxwizard on 2007-08-20
See if this will help
[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

---

### Post by bleearg on 2007-08-21
Thanks for the response, but I read through that, and well, as I said in my original post, I am not using PPPoE.  Since that guide is specifically for setting up PPPoE, it's not at all helpful in my situation.

---

### Post by pxwpxw on 2007-08-21
> **bleearg said:**
> Thanks for the response, but I read through that, and well, as I said in my original post, I am not using PPPoE.  Since that guide is specifically for setting up PPPoE, it's not at all helpful in my situation.

Suggest you check in detail how the router (you referred to above) is configured. If it is not using password authentication, then it may be using a static ip address. Then I would expect there should be an online user guide available for the pci modem, and a linux driver may be required.
The pppoeconf package appears to be only for ethernet connection to an external modem via a standard NIC. I assume your pci modem has an adsl phone line interface.

---

### Post by bleearg on 2007-08-21
Yes, the router on the other end of this ADSL connection is configured with a static IP address.  The problem with the "online user guide" is that all the user guides are for Windows.  I've searched and cannot find a user guide for Linux for this PCI card.

Does the output from my 'lspci' appear abnormal?  I see that the PCI card is recognized as an ATM network controller, but it also states that it's an 'unknown device'.  I assume this means that I just don't have the proper driver, correct?

---

### Post by pxwpxw on 2007-08-21
> **bleearg said:**
> Yes, the router on the other end of this ADSL connection is configured with a static IP address.  The problem with the "online user guide" is that all the user guides are for Windows.  I've searched and cannot find a user guide for Linux for this PCI card.

Does the output from my 'lspci' appear abnormal?  I see that the PCI card is recognized as an ATM network controller, but it also states that it's an 'unknown device'.  I assume this means that I just don't have the proper driver, correct?

You are right. However the Windows guide may give some clues for later, does it provide better identification including refernece to USB ADSL modem.
I would try the card out using windows if you have it, just to establish it works,, and give an idea of the windows networking. Note that it probably has no built in firewall, security wise.
"Unknown device" is OK there, just means not listed somewhere, the key info is Alcatel ATM device 1101 rev01, and 3com I suppose..
I am not familiar with it.


You can get more info with these:
```

sudo lshw
sudo lspci -v
sudo lsusb -v

```

Then might be best to run another thread specifically asking for help with Alcatel pci ADSL modem driver, there may even be a module or other package to suit it. (Link back to here)  Might pay to look at Alcatel, 3com web sites.
There is a modem Chips reference site somewhere, I will also have a look for that.

edit:
found this, maybe the right area but not the same modem.
(google:
 alcatel pci modem chips technology

[http://www.chipweb.de/dsl/index.php?menu=1&id2=23](http://www.chipweb.de/dsl/index.php?menu=1&id2=23)

---

### Post by bleearg on 2007-08-22
Thanks for the info, pxwpxw.  I'm not going to have a problem configuring the modem's settings, it's more of how to get the modem recognized by the OS and how it will show up (or if it shows up) in the 'ifconfig' output.  I've tried looking for 3com drivers, but I've turned up nothing but lots of old posts about this modem not being supported under Linux.  However, since it seems to be recognized, I'm wondering if that's true anymore.  

I think my best bet is to ditch this particular modem and find something a bit newer and more supported.

---

### Post by netztier on 2007-08-22
> **bleearg said:**
> I've tried looking for 3com drivers, but I've turned up nothing but lots of old posts about this modem not being supported under Linux.  However, since it seems to be recognized, I'm wondering if that's true anymore.  


Well, the Modem being recognised by lspci doesn't mean that there is a suitable kernel module (=driver) for it. It just means that the card has registered itself with the PCI Bus on the system.
Now you should find out which kernel module is able to support that ATM NIC - and for that purpose, knowing as much as possible about it might help - which chipset etc.

On my notebook (Ubuntu 7.04, 32bit), the following ATM driver modules are available:

```
marc@torch:[COLOR="Red"]/lib/modules/2.6.20-16-generic/kernel/drivers/atm[/COLOR]$ ls -al
total 460
drwxr-xr-x  2 root root  4096 2007-06-10 00:25 .
drwxr-xr-x 44 root root  4096 2007-05-29 09:39 ..
-rw-r--r--  1 root root 34264 2007-06-07 22:59 ambassador.ko
-rw-r--r--  1 root root 12860 2007-06-07 22:59 atmtcp.ko
-rw-r--r--  1 root root 34604 2007-06-07 22:59 eni.ko
-rw-r--r--  1 root root 29052 2007-06-07 22:59 firestream.ko
-rw-r--r--  1 root root 70360 2007-06-07 22:59 fore_200e.ko
-rw-r--r--  1 root root 38812 2007-06-07 22:59 he.ko
-rw-r--r--  1 root root 22192 2007-06-07 22:59 horizon.ko
-rw-r--r--  1 root root 40308 2007-06-07 22:59 idt77252.ko
-rw-r--r--  1 root root 36160 2007-06-07 22:59 iphase.ko
-rw-r--r--  1 root root 31960 2007-06-07 22:59 lanai.ko
-rw-r--r--  1 root root 34916 2007-06-07 22:59 nicstar.ko
-rw-r--r--  1 root root  9676 2007-06-07 22:59 suni.ko
-rw-r--r--  1 root root  7548 2007-06-07 22:59 uPD98402.ko
-rw-r--r--  1 root root 25176 2007-06-07 22:59 zatm.ko

```

To see if any of these might match your card, try **modinfo <module file name>** and if the output hints that the module supports chipsets similar to the one on your card, try **sudo modprobe <module name>**. Be sure to check **dmesg** afterwards to see if the module has been properly loaded

best regards

Marc

---

### Post by pxwpxw on 2007-08-22
> **bleearg said:**
> Thanks for the info, pxwpxw.  I'm not going to have a problem configuring the modem's settings, it's more of how to get the modem recognized by the OS and how it will show up (or if it shows up) in the 'ifconfig' output.  I've tried looking for 3com drivers, but I've turned up nothing but lots of old posts about this modem not being supported under Linux.  However, since it seems to be recognized, I'm wondering if that's true anymore.  

I think my best bet is to ditch this particular modem and find something a bit newer and more supported.

I agree, you would be much better off with a NIC and an exterrnal router.
USB modems are peculiar.

But how about these kernel modules first. 
Speedtouch used alacatel chip I think. 
You might try modprobe speedtch or usbatm, see if anything happens.
Might be some more in your system.

$ ls -l   lib/modules/2.6.20-15-powerpc/kernel/drivers/usb/atm

-rw-r--r-- 1 root root 17632 2007-04-15 16:47 cxacru.ko
-rw-r--r-- 1 root root 22672 2007-04-15 16:47 speedtch.ko
-rw-r--r-- 1 root root 37984 2007-04-15 16:47 ueagle-atm.ko
-rw-r--r-- 1 root root 25076 2007-04-15 16:47 usbatm.ko
-rw-r--r-- 1 root root 11916 2007-04-15 16:47 xusbatm.ko
madmax@ibook:~/Desktop/f704usb$

---

