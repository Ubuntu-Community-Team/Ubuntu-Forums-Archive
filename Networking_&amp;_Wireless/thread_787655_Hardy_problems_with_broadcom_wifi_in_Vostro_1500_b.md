---
title: "Hardy problems with broadcom wifi in Vostro 1500 but perfect in e1505"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by bishop9226 on 2008-05-09
I've been searching the forums and google for the last 3 hours but no one has really covered what my problem is here we go.

Setup:

I have an e1505 and a Vostro 1500.  Both use the broadcom wifi driver and I'm fairly certain its the exact same one too since both are dell 1395 minicards.

With the e1505 I have had NO trouble using the restricted driver fwcutter after a fresh install once I connect the laptop to a wired connection and go through an ubuntu autoupdate.  

However, with the vostro 1500, the restricted driver NEVER shows up.  So I try going into synaptic and downloading the bw4xx-fwcutter and nothing happens.  So I dl'd the dell exe driver for the vostro did the ndiswrapper trick that all the guides say to do (I had to do this for my e1505 back in feisty).  

Problem:
Now wifi WORKS in the vostro and once its connected it is nice and fast...the problem is that it takes MULTIPLE tries to connect and sometimes upto 5 minutes to get on wifi.  This is the SAME problem I had last year with feisty and my e1505, esp when any wifi had security settings (like mine does at home).

How can I get the fwcutter restricted driver to show?  I really hate ndiswrapper and don't want to use it anymore.  

Thanks

---

### Post by Ayuthia on 2008-05-09
If you are just looking to install fwcutter, all you have to do is:
```
sudo apt-get install b43-fwcutter
```.

The Hardware Driver Manager does not show the Broadcom driver when NDISwrapper is used.

---

### Post by bishop9226 on 2008-05-09
yeah ok i did that (from synaptic, there are two of them to choose from too).  but it never shows up under restricted drivers and i still cant use wifi.  once i dl it your way and do the "fetch" - how do i get it to work?

---

### Post by Ayuthia on 2008-05-09
Let's start by checking your lshw -C network.  It will tell us if the firmware was installed correctly and if it is trying to use the driver.  From there, we can see if we can see any access points.

By the way, do you know your card id(lspci -nn)?  I just want to verify that your card is working with b43.  There are a few cards to that are not working with b43 right now.

---

### Post by MadMedis on 2008-05-10
Ayuthia: thanks for the post!  I have a Microsoft MN-720 PCMCIA wireless card (it uses the broadcom "legacy" chipset), which worked great under Gutsy (I used the Restricted Driver Manager to get it working), but the upgrade to Hardy broke the wireless adapter.  I ran "sudo apt-get install b43-fwcutter" as you suggested and my wireless card came to life!

---

### Post by Ayuthia on 2008-05-10
> **MadMedis said:**
> Ayuthia: thanks for the post!  I have a Microsoft MN-720 PCMCIA wireless card (it uses the broadcom "legacy" chipset), which worked great under Gutsy (I used the Restricted Driver Manager to get it working), but the upgrade to Hardy broke the wireless adapter.  I ran "sudo apt-get install b43-fwcutter" as you suggested and my wireless card came to life!
Can you post your lspci -nn?  I am curious which chipset it is and it could possibly help others in the future.  Thanks!

---

### Post by MadMedis on 2008-05-10
Sure, here you go (I am using a Dell Inspiron 5100 laptop, and this wireless adapter is the only attached device):

00:00.0 Host bridge [0600]: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface [8086:2560] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge [8086:2561] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 82)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge [8086:24c0] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DB (ICH4) IDE Controller [8086:24cb] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 02)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 02)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] [1002:4c57]
02:01.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
02:04.0 CardBus bridge [0607]: Texas Instruments PCI4510 PC card Cardbus Controller [104c:ac44] (rev 02)
02:04.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCI4510 IEEE-1394 Controller [104c:8029]
03:00.0 Network controller [0280]: Broadcom Corporation BCM43xG 802.11b/g [14e4:4325] (rev 02)

---

