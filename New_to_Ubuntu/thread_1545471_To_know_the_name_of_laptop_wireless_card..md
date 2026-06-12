---
title: "To know the name of laptop wireless card."
date: 2010-08-03
forum: New to Ubuntu
---

### Post by amityadav9314 on 2010-08-03
HI
I have compaq 601 presario.
I wanna know the method by which I can know that which wireless card is installed in my laptop.
thanks!

---

### Post by JBAlaska on 2010-08-03
> **amityadav9314 said:**
> HI
I have compaq 601 presario.
I wanna know the method by which I can know that which wireless card is installed in my laptop.
thanks!

Try:
```
lspci
```
```
iwconfig
```

Edit: Google search gave me this: **sp43742 Broadcom Wireless**

---

### Post by anewguy on 2010-08-03
Add an lsusb to that as well, as some laptops' internal wireless connects to the internal USB bus.  If you are new at Ubuntu, follow the instructions below:

- open a terminal window (Applications/Accessories/Terminal)

- type:

lspci <press enter>  Copy that output and paste in a reply here

lsusb <press enter>  Copy that output and paste in a reply here

iwconfig <press enter>  Copy that output and paste in a reply here


Also, check in System/Administration/Hardware Drivers and see if there is a driver listed there.  If so, be sure it is enabled.

Since JBAlaska mentioned their search turned up some sort of Broadcom adapter, you should try the following if at all possible:

- hard-wire a connection from your laptop to your router

- open a terminal window (Applications/Accessories/Terminal)

- type:

sudo apt-get update <press enter>  Wait for this to complete

- now check again in System/Administration/Hardware Drivers and see if a driver is listed there.  If so, be sure it is enabled.

- disconnect the hard-wire from your laptop to the router

- right click on the Network Manager icon

- if "Enable Wireless" is not checked, be sure to check it

- wait a minute or 2

- left click on the Network Manager icon and see if wireless networks now show - if so, the driver is working

If you have any problems/questions please post back - we're here to help if we can!

Dave ;)

---

### Post by amityadav9314 on 2010-08-04
this is the potput i have got...



amit@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
04:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
04:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
04:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
amit@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"aircelgprs"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 1A:2D:9F:28:D0:2B   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
vboxnet0  no wireless extensions.

pan0      no wireless extensions.

amit@ubuntu:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 04f3:0230 Elan Microelectronics Corp. 
Bus 005 Device 002: ID 1c4f:0002 SiGma Micro 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 174f:5216 Syntek 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
amit@ubuntu:~$

---

### Post by amityadav9314 on 2010-08-04
One more thing I would like to ask
When I open system->administration->hardware driver, it shows two driver as follows:-
1:-broadcom b43 wireless driver
2:-broadcom sata wireless driver

but the problem is that the second one is not activated....it says while activatin it....
"sorry the installation of the driver failed
please hae a look at the log files for details  /var/log/jockey.log

---

### Post by anewguy on 2010-08-04
A couple of questions:

- is the first driver activated?

- the second driver, is it "sata" or is it "STA"?

Be sure to only activate one at a time.  If one doesn't work, disable it before trying the next.

Dave ;)

---

### Post by amityadav9314 on 2010-08-04
yeah the first one is activated.
So only one of those can be activated  at a time?
the other one is STA (NOT SATA)...

---

### Post by anewguy on 2010-08-04
> **amityadav9314 said:**
> yeah the first one is activated.
So only one of those can be activated  at a time?
the other one is STA (NOT SATA)...

As I understand things, yes.  Also, to answer your original question about your adapter, it shows in the lspci output as:

02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)


So what you have is the Broadcom BCM4312 - a quite common adapter.

Dave ;)

---

### Post by amityadav9314 on 2010-08-04
As it shows two drivers as follows:-
1:-broadcom b43 wireless driver
2:-broadcom sta wireless driver 
so which of them is needed to be installed in order to access to wifi networks?

---

### Post by amityadav9314 on 2010-08-05
:)

---

### Post by JBAlaska on 2010-08-05
> **amityadav9314 said:**
> As it shows two drivers as follows:-
1:-broadcom b43 wireless driver
2:-**broadcom sta wireless driver** 
so which of them is needed to be installed in order to access to wifi networks?

Use the STA driver. Some people have trouble getting the STA driver to "Show up" or install in hardware drivers.

If this the case for you, type the following in a terminal:

```
sudo apt-get install bcmwl-kernel-source
```

Now reboot, and go to System, Administration, Hardware Drivers.

And you should be able to select the STA driver and have it activate.

Edit: you either have to have a wired connection for the above to work, or you can put the LiveCD in your drive and go to: System, Administration, Software sources and check the box below "Installable from CDROM". Then open a term and do:

```
sudo apt-get update
```

Then:

```
sudo apt-get install bcmwl-kernel-source
```

Now reboot and select the STA driver.

---

### Post by amityadav9314 on 2010-08-05
my b43 driver is activated.
the problem is that neither i can remove b43 nor can activate sta.
why?
every time it's showing an error.

---

### Post by lkraemer on 2010-08-08
Try this:
[http://ubuntuforums.org/showthread.php?t=1470146&highlight=dmesg](http://ubuntuforums.org/showthread.php?t=1470146&highlight=dmesg)

lk

---

### Post by anewguy on 2010-08-08
It would appear to my simple eyes that your wireless is working already.  I have copied the output from one of your earlier posts - notice how it says "ESSID:"aircelgprs""?  It would seem to me it is already connected to some wireless device that is know as "aircelgprs".

```
wlan0 IEEE 802.11bg ESSID:"aircelgprs" 
Mode:Ad-Hoc Frequency:2.412 GHz Cell: 1A:2D:9F:280:2B 
Tx-Power=20 dBm 
Retry long limit:7 RTS thrff Fragment thrff
Power Managementff

```

Dave

---

