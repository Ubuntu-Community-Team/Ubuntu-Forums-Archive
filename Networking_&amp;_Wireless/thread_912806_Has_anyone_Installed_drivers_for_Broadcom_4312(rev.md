---
title: "Has anyone Installed drivers for Broadcom 4312(rev 01) 802.11 b/g drivers"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by showri on 2008-09-07
hi,
I have Tx2500z laptop with broadcom wireless 4312(rev 01) 802.11 b/g.I have been trying to install drivers for it but unable to do so.Can anyone help me out.

WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:4a:b0:77
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:ce:4b:5a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.1.106 latency=0 module=r8169 multicast=yes

As you can see the module=wl.do we have any working drivers for this wireless .If they are present can anyone help me in installing them.

thankyou

---

### Post by Ayuthia on 2008-09-07
> **showri said:**
> hi,
I have Tx2500z laptop with broadcom wireless 4312(rev 01) 802.11 b/g.I have been trying to install drivers for it but unable to do so.Can anyone help me out.

WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:4a:b0:77
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:ce:4b:5a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.1.106 latency=0 module=r8169 multicast=yes

As you can see the module=wl.do we have any working drivers for this wireless .If they are present can anyone help me in installing them.

thankyou

Can you post your kernel version along with more info about your card:
```
uname -a
lspci -nn
```
The wl driver does work, but I think it does not fully function well until 2.6.24-21.  However that is in the hardy-proposed repositories (the testing version before the actual release).  If you don't mind using the testing version, you can try this:
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

However, the other options to try would be to either use ndiswrapper or try to rebuild the wl driver from source.  Those two options can be done, but if you have the 14e4:4315 version of the 4312 card, it will be a little more difficult because it is hard to get the right Windows driver for ndiswrapper and if you rebuild the wl driver, you will have to remove the kernel version of the wl driver.  They are both possible, but will require more work.

---

### Post by superprash2003 on 2008-09-07
hope this helps [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by showri on 2008-09-07
showri@showri-laptop:~$ uname -a
Linux showri-laptop 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64
this sis my kernel version

08:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

my wireless version

---

### Post by showri on 2008-09-07
I have tried all methods to install my wireless driver,but unable to do so.can anyone help me from scratch as to how to install wireless drivers.

---

### Post by david sousa on 2008-09-07
Yes! [http://ubuntuforums.org/showthread.php?p=5693578](http://ubuntuforums.org/showthread.php?p=5693578)

---

### Post by gali98 on 2008-09-07
I have this same exact card (in the tx2000) and the wl driver works fine.

Yes I [14e4:4315] (rev 01).

All you have to do is plug in ethernet and make sure you are fully update (with normal updates, not proposed) then go to restricted drivers.
(System->Administration->Hardware Drivers)

There should be an entry named wl. 
If it is already checked then uncheck it, then check it again.
After that (if it wasn't checked just check it)
just restart (that's the easiest thing to do)

Try that as that what has worked for me (on 32 and 64bit)

Kory

---

### Post by newtubunix on 2008-09-07
If that didn't work try this:
I have a slightly different broadcom chip but this should work with all of the variants.
Go to this site and download compat-wireless from there under "where to download":
[http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)
Then follow the instructions under "Building and installing"
Unload all previous drivers with "sudo make unload"
Load the b43 driver, by loading all drivers from that package: "sudo make load" or only the b43 driver with "sudo modprobe b43"

---

### Post by RichardLaurenson on 2008-09-07
> **gali98 said:**
> I have this same exact card (in the tx2000) and the wl driver works fine.

Yes I [14e4:4315] (rev 01).

All you have to do is plug in ethernet and make sure you are fully update (with normal updates, not proposed) then go to restricted drivers.
(System->Administration->Hardware Drivers)

There should be an entry named wl. 
If it is already checked then uncheck it, then check it again.
After that (if it wasn't checked just check it)
just restart (that's the easiest thing to do)

Try that as that what has worked for me (on 32 and 64bit)

Kory

GRR and for me too, except that I was trying to right click the icon and then find wireless dialog. Infact I double clicked the network and chose the wireless that popped up.... :rolleyes: 
Richard

---

### Post by Ayuthia on 2008-09-07
> **newtubunix said:**
> If that didn't work try this:
I have a slightly different broadcom chip but this should work with all of the variants.
Go to this site and download compat-wireless from there under "where to download":
[http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)
Then follow the instructions under "Building and installing"
Unload all previous drivers with "sudo make unload"
Load the b43 driver, by loading all drivers from that package: "sudo make load" or only the b43 driver with "sudo modprobe b43"

The 14e4:4315 chipset does not work with b43 at this time.  The b43 developers are still working on it.

---

### Post by Ayuthia on 2008-09-07
> **showri said:**
> I have tried all methods to install my wireless driver,but unable to do so.can anyone help me from scratch as to how to install wireless drivers.

I saw that in your other thread that you have ran the updates for hardy-proposed and it still does not work.  Can you now post the results for:
```
lsmod|grep -i -e wl -e b43 -e ssb -e ndiswrapper -e bcm43xx
```
This will help identify what wireless modules are currently loaded (if any).  If you have not tried this yet, please try the following:
```
sudo modprobe -r b43 ssb bcm43xx wl ndiswrapper
sudo mopdrobe wl
sudo ifconfig eth1 up
sudo iwlist scan
```Please let us know if any wireless sites come up or if any error messages come up.  If it still does not connect, can you check the last part of dmesg to see if any error messages come up for the wl driver.  It should be at the end of the dmesg results (the dmesg command is run in the Terminal).

---

### Post by gali98 on 2008-09-07
Ayutha

the command 

sudo ifconfig eth1 up

might be a problem, as sometimes the wireless is eth0 (like on mine right now).
however mine switches back and forth.

A better command might be

```
 sudo /etc/init.d/networking restart
```

In intepid this should be default on install.. and b43 should support this card sooner or later, and that will be a lot better....
Anyone know where wl comes from?
Is it part of the b43 project?

Kory

---

### Post by Ayuthia on 2008-09-08
> **gali98 said:**
> Ayutha

the command 

sudo ifconfig eth1 up

might be a problem, as sometimes the wireless is eth0 (like on mine right now).
however mine switches back and forth.

A better command might be

```
 sudo /etc/init.d/networking restart
```

In intepid this should be default on install.. and b43 should support this card sooner or later, and that will be a lot better....
Anyone know where wl comes from?
Is it part of the b43 project?

Kory
I don't disagree with you about the sudo /etc/init.d/networking restart method.

As for the wl driver, it comes directly from Broadcom and has nothing to do with the b43 project.  The wl driver is currently in Intrepid so I am guessing that it will be there when it is released.

The b43 driver is also still there, but like Kory said, it is currently not available for the 4315 chipset.  They are working on it though.

---

### Post by gali98 on 2008-09-08
> **Ayuthia said:**
> 
The b43 driver is also still there, but like Kory said, it is currently not available for the 4315 chipset.  They are working on it though.

That is also a question I had. It says it is Broadcom 4312 when listing pci devices, but the id says 4315.... Where did the 4312 come from?

Kory

---

### Post by Ayuthia on 2008-09-08
> **gali98 said:**
> That is also a question I had. It says it is Broadcom 4312 when listing pci devices, but the id says 4315.... Where did the 4312 come from?

Kory
The database for identifying pci cards is located in /usr/share/misc/pci.ids.  So if you go into that file and search for 4315, you will find that it identifies it as:
```
    4315  BCM4312 802.11b/g
        1028 000b  Wireless 1395 WLAN Mini-Card
        1028 000c  Wireless 1397 WLAN Mini-Card
        103c 137c  BCM4312 802.11b/g Wireless LAN Controller
        103c 137d  BCM4312 802.11b/g Wireless LAN Controller
```
So if you do a lspci -nnmv, you will see that the Vendor is Broadcom [14e4] and the Device is 4315, the rest of the definition is actually defined by the subvendor info (SVendor).  

Since you have a tx2000 (I am guessing it is an HP), doesn't your card show the 4312 when you do lspci?

---

### Post by gali98 on 2008-09-08
Yes it does (and yes it is HP)
So that means it is a 4312?

I put in an email to the guys at the bcm43xx project about the whole thing, but they haven't answered me back yet.
Kory

---

### Post by Ayuthia on 2008-09-08
> **gali98 said:**
> Yes it does (and yes it is HP)
So that means it is a 4312?

I put in an email to the guys at the bcm43xx project about the whole thing, but they haven't answered me back yet.
Kory

It is called the 4312 card.  The vendor and device number doesn't change for the hardware, but it's name can be changed.  That is why I prefer to use the vendor and device id when assisting.  I am not for sure if you remember when you first installed Ubuntu, your card was identified as a USB device and was named a 4310 before it was updated to 4312.  Because of these type of changes, it is easier to use something that stays more constant like the vendor and device id.

Broadcom calls it a BCM4312 but also says it has a device id of 4315.

---

### Post by gali98 on 2008-09-08
ahhhh....

Well all I know is it doesn't work :)

(with b43)

Kory

---

### Post by jearod on 2008-10-09
[http://ubuntuforums.org/showthread.php?t=880218&page=16](http://ubuntuforums.org/showthread.php?t=880218&page=16)

The first page of the thread has all the information...I'm using it with a WPA2 key and it works great. I posted a question on pg 16 regarding making this driver load by default on boot...if anyone has any suggestions please let me know.

BTW using a Dell Mini 9 if that is relevant.

---

### Post by sliverman69 on 2008-10-20
you are all complete NUBS...he's talking about the OFFICIAL driver that was released from Broadcom FOR linux in .tar.gz format that you can now install for the BCM4311, BCM4312, BCM4321, and BCM4322 cards...you can get the source here...it was released in july... [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) ...

the only problem is I have been having issues installing it on my system so far, but it could be that I am having problems since this install of ubuntu is not a clean one, I had suse 10.2 on here and decided to switch back once they switched to 11.0 and friggin' KDE 4.0...blech!  but, that is another topic for another day/thread.  

Anyway, has anyone been successful in installing this driver and how did you get it to work.  No, IT IS NOT A FWCUTTER-LIKE or NDISWRAPPER-LIKE driver.  It's official!  I don't know why or what made them do it, but I am glad they did.

So, I don't mean to be mean, I am just frustrated that you all didn't do any REAL searching before you posted...or you are just dealing with what you know.  Either way, next time search google instead of just searching the forums...or check broadcom occasionally to check and make sure that they don't have an official driver...I know they don't like linux, but, I happened uppon this in the search of windows drivers for some ethernet cards in windows (not my choice there) they are school research computers owned by my school and set up by OIT...they are the biggest bunch of failures that call themselves IT that walk the face of the earth).  

Part of linux is getting out there and learning new things about how to use the OS and maximize you usage.  I need this to work because my school's wireless routers/APs like to kick my laptop off the wireless network every 30 seconds and force me to re-login using my username and password (which is long).  I am fairly certain that it's ndiswrapper that the APs don't like because it worked fine with fwcutter, but was slow as CRAP!!! 1Mb/s is too friggin' slow...especially since our school has a backbone of 55Mb/s down and 16Mb/s up...give or take a little.

Sorry again for being rude, but I am just frustrated that everyone is linking to fwcutter and ndiswrapper when there is a NATIVE driver out there that all you have to do is compile and install...you do remember how to do that, right?  We shouldn't abandon the command line since that is the driving force of this OS...it's very handy most of the time...

Best regards,
sliverman69

---

### Post by sliverman69 on 2008-10-20
disregard most of that last post, I didn't see that you were supposed to link to the first page of that sticky...anyway, it doesn't show up in the list of drivers available...is there a command line solution?

---

### Post by johnshentiro1 on 2008-10-20
I have the same driver for Broadcom 4312(rev 01) 802.11 b/g drivers,but i can not get connected to the site with wireless.any others?

---

