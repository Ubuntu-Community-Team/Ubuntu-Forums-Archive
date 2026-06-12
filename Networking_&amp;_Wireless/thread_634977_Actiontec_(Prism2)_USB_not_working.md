---
title: "Actiontec (Prism2) USB not working"
date: 2007-12-08
forum: Networking &amp; Wireless
---

### Post by diyfiesta on 2007-12-08
Hi Folks,

Having a bit of trouble setting up my wireless adapter with ndiswrapper and wondered if you had any tips. I think it boils down to not switching the USB adapter "on", that is to say there is no LED lite and I can't do a scan (nothing found) or set the ESSID.

I've had it working on Fedora before so I know it can work and I think the adapter is detected ok but I can't get anywhere with the basic ndiswrapper instructions, Any ideas?

I found this [https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb](https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb) which talks about a different driver, I setup ndiswrapper manually from the windows driver so if I follow the steps to setup linux-wlan-ng will it play nice?

```

@larma:~$ lsusb
Bus 001 Device 002: ID 1668:0421 Actiontec Electronics, Inc. [hex] Prism2.5 802.11b Adapter
Bus 001 Device 001: ID 0000:0000
@larma:~$ lsmod | grep prism
prism2_usb             74756  0
p80211                 33036  1 prism2_usb
usbcore               138632  4 ndiswrapper,prism2_usb,ohci_hcd

```

Thanks for any tips,

Cheers,

---

### Post by diyfiesta on 2007-12-08
playing around some I made some progress, adding prism2_usb to the blacklist gets me further, Im using ndiswrapper with the native drivers .. just cant set it up properly! I'll keep trying and post anything interesting :)

---

### Post by swegner on 2007-12-16
I'm also having trouble setting up a prism2-based wireless adapter.  It's a USB adapter (specifically, Microsoft MN-510), and I'm on a fresh x86 Gutsy install.  From different sources, it sounds like the prism2_usb drivers should work after installing the linux-wlan-ng package.  I've installed and restarted a couple times, but nothing.

I'm hesitant to try the ndiswrapper drivers or messing with a lot pof manual tweaks, because I've had bad experiences with it in the past.  Also, it sounds like the prism2_usb driver *should* be working.  Has anyone had a successful experience?

---

### Post by MystyxMac on 2008-01-10
I also have trouble to let my USB Wireless Adapter work. I use Ubuntu Gutsy and I have the Actiontec 802UI3 Wireless USB Adapter. When i plug it in, I can configure a wireless network via NetworkManager, but it doesn't connect. It doesn't even see a wireless network. 
On the USB adapter is also a led that should be turned on, but it doesn't.
I also tried linux-wlan-ng and ndiswrapper. The last one gives errors when i try to load the module. (i've blacklisted the prism2_usb driver)....

---

### Post by zoke on 2008-01-26
I have a prism2 device and it works fine. What you need to do is install the linux-wlan-ng package and then reboot. This works for my Linksys WUSB11 V3 dongle.

---

### Post by adisor19 on 2008-05-08
Same thing here. I can't get my Linksys WUSB11 v2.5 (Prism 2 based) to work either under 8.04 :(

adi@AdiUbuntu:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 0e0f:0002  
Bus 001 Device 004: ID 066b:2212 Linksys, Inc. WUSB11v2.5 802.11b Adapter
Bus 001 Device 001: ID 0000:0000  
adi@AdiUbuntu:~$ lsmod | grep prism
prism2_usb             82180  0 
p80211                 36240  1 prism2_usb
usbcore               169904  4 prism2_usb,ehci_hcd,uhci_hcd


Anyone got some ideas ?

Adi

---

