---
title: "XUBUNTU, AOL WIRELESS and NETGEAR WG111 WIRELESS USB ADAPTER  HELP HELP HELP!"
date: 2007-06-22
forum: Networking &amp; Wireless
---

### Post by dan fisher on 2007-06-22
I have got a USB wireless adapter which is on the compatibility list as being completely compatible with UBUNTU 7.04 (without ndiswrapper).

I have installed XUBUNTU 7.04.

I was told that after installation and plugging in said wireless adapter UBUNTU would detect it and install drivers.

Is this true of only UBUNTU and not XUBUNTU?

The system doesn't do anything when I plug the USB wireless adapter in.

I left the wireless adapter unplugged while installing ubuntu - was this a mistake?

The wireless adapter is a NETGEAR WG111 (the most compatible adapter I could find)

HELP!

also I will be able to connect to the AOL service from XUBUNTU through the wireless router supplied with AOL - a NETGEAR 54mbps wireless router (model DG834G v3) won't I?

I am not interested in using the AOL software (i.e. PENGAOL).

I just want a straightforward connection AOL is the cheapest service on the block here (UK).
__________________

      

dan fisher 
View Public Profile 
Send a private message to dan fisher 
Find all posts by dan fisher 
Add dan fisher to Your Buddy List 

  #2       9 Hours Ago  
dan fisher  
First Cup of Ubuntu
   Join Date: Apr 2006
Beans: 5 

 
Re: XUBUNTU, AOL WIRELESS and NETGEAR WG111 WIRELESS USB ADAPTER 

--------------------------------------------------------------------------------

By the way the machine is a DELL Dimension 8300

maybe USB isn't working?
__________________

      

dan fisher 
View Public Profile 
Send a private message to dan fisher 
Find all posts by dan fisher 
Add dan fisher to Your Buddy List 

  #3       8 Hours Ago  
dan fisher  
First Cup of Ubuntu
   Join Date: Apr 2006
Beans: 5 

 
 Re: XUBUNTU, AOL WIRELESS and NETGEAR WG111 WIRELESS USB ADAPTER 

--------------------------------------------------------------------------------

ok on issuing the lsusb - list USB devices command I get:

Bus 005 Device 002: ID 0846:6a00 NetGear, Inc. WG111 Wifi (v2)

I bought this USB wireless card as the UBUNTU site says it works out of the box in feisty (7.04).

where to next?

I want to use the native drivers not the ndiswrapper drivers.

I thought it would detect and give me an installation dialogue something like plug n play ...

(XUBUNTU 7.04)
__________________

---

### Post by dmizer on 2007-06-22
yes it should be plug and play.  but you still have to tell the adaptor HOW to connect.  there should be a networking configuration in your menu under administration.  do you not see your adaptor in networking?

further, you're using AOL, so i'm not sure if there may be some special configuration for that which would require the pengaol software.

---

### Post by dan fisher on 2007-06-24
BUMP

I have found more information

dmesg gives me:

[80.360680] wiphy0: hwaddr 00:18:4d:fe:3d:33, rtl8187 V1 + rtl8225z2
[80.360693] ubscore: registered new interface driver rtl8187

^ this has the MAC address for my wireless WG111 USB dongle.

lsmod (list modules) | grep 8187 gives me:

rtl8187                  34944       0
mac80211             175364     2   rc80211_simple,rtl8187
eeprom_93cx6      4352         1  rtl8187
usbcore                 134280     4   rtl8187,ehci_hcd,uhci_hd

All this tells me that the driver has installed and there are modules for it.

lsusb (list USB devices) gives me:

BUS 005 Device 003: ID 0846:6a00 Netgear, Inc. WG111 WiFi (v2)

all the other USB slots are empty - the machine has the 0846:6a00 code for the vendor and product code.

From all this I would assume that the driver is installed for the NetGear WG111v2 ... rtl8187 is it's chip.  This is a fresh install I haven't done anything to the system yet.

All of the documentation for how to set up the WG111v2 dongle shows how it is done using 'ndiswrapper' (interface to use windows drivers).

Can somebody tell me how to progress this?

Is this driver installed ok?

Why do people seem to be using ndiswrapper when feisty appears to install this driver 'out of the box'?

I hope somebody can advise me on this.

I just want somebody to look over what I've found out and validate my assumptions.

:D

---

### Post by panurge77 on 2007-06-27
wrong thred

---

### Post by royalgfx on 2007-08-31
Hey

I just fresh installed 7.04 FF, and I bought a netgear wg111. 

lsusb recognises it as

Bus 001 Devicde 006: ID 0846: 6a00 NetGear, Inc. WG111 WiFi (v2)

How do I get this thing to work!?

---

