---
title: "Acer Wireless not functional"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by jezebel on 2009-11-02
Here I am again.

I have a new Acer Aspire One D250 netbook, and installed Ubuntu Netbook Remix 9.10.

But I have no wireless capability. 

I have an old acer 3000 series, and I had found info somewhere and all I had to do was install something through the Synaptic package manager. Don't remember what that was now, and I really really want to get this wireless working!

Please help:confused:

---

### Post by Michael.Palone on 2009-11-02
Okay. Can you post the output of running the command lspci in the terminal?
I think your netbook (like mine) has a Broadcom wireless card. If that is the case, you'll need to get a wired connection and use the Hardware Drivers option under System -> Administration to get the right firmware.

---

### Post by jezebel on 2009-11-02
Thanks, Michael -

I think you're right - it's broadcom. Here are the results from terminal:

tracy@tracy-mini-acer:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
03:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)


Could you explain how I can get the necessary firmware? (I am wired).

---

### Post by Michael.Palone on 2009-11-02
Sorry about the delay- I was on the commute home from university.
So, you do have a Broadcom wireless card. While connected, go to System -> Administration -> Hardware Drivers. Enable the Broadcom STA driver and Ubuntu should fetch the needed firmware and install it.
However, sometimes the dialog box does not give me the option to enable those drivers- in this case, install the bcmwl-kernel-source package in Synaptic. Then repeat the steps in the paragraph above.
I hope this helps- I remember quite well struggling through all of this. It's very frustrating. Let me know how it goes.

---

### Post by jezebel on 2009-11-03
Hey Michael -
Thanks for the help, and sorry for the delay.

I navigated to the right place (Hardware drivers) and found two drivers needed, but the program freezes when I try to install.

The window says, "downloading and installing driver", but actually shows no progress, and I can't cancel or close the window.

---

### Post by Michael.Palone on 2009-11-04
Okay. One more thing I can think of. Get a wired connection again, go back to Synaptic, and install the b43-fwcutter package. Try getting the firmware again.

---

### Post by yeats on 2009-11-04
I was able to get my Dell mini Broadcom wireless working by installing the bcmwl-kernel-source package, restarting, and I was up and running immediately.  (After lots of Googling, of course ;-) )

---

### Post by jezebel on 2009-11-05
Okay - thanks for the posts.

A few things:

I removed ubuntu, then reinstalled using a fresh download and usb. 

It seems cleaner over all, and I was able to go to hardware and it didn't freeze on installing. However, then my system crashed and had a huge fatal missing kernel error.

I stuck in the usb stick again and rebooted...my system is now up and running, but I'm afraid to try to install those drivers again:-(

I'll work up my courage soon!

Tracy

---

### Post by jezebel on 2009-11-06
Okay - thanks for the posts.

A few things:

I removed ubuntu, then reinstalled using a fresh download and usb. 

It seems cleaner over all, and I was able to go to hardware and it didn't freeze on installing. However, then my system crashed and had a huge fatal missing kernel error.

I stuck in the usb stick again and rebooted...my system is now up and running, but I'm afraid to try to install those drivers again:-(

I'll work up my courage soon!

Tracy

---

