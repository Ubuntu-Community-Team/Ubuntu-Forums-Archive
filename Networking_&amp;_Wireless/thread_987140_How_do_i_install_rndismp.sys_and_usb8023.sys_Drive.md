---
title: "How do i install: rndismp.sys and usb8023.sys Drivers?"
date: 2008-11-19
forum: Networking &amp; Wireless
---

### Post by IBUA on 2008-11-19
Hey, 

I was recommended trying this [http://www.jooz.net/rndis/]("http://www.jooz.net/rndis/") driver system thingy to see if this would get my Truemobile 1300 USB Wirless adaptor to work on Ubuntu 8.04 as no one else was helping and this is the only advice i got

But for the installation instructions, they are quite sort of advanced for me as i am a total newb for sort of complicateed code/installations

so

[B]1. Is this safe for me to do?
2. Could anyone give me a sort of run through with all the nessecary commands to do this installation?[/B]

Here are the instructions if you can't be bothered to look at the link:

Installation:

    * install the kernel source/headers package for your particular distro.
    * backup original kernel modules usbnet.ko, cdc_ether.ko and rndis_host.ko (find them under /lib/modules/<kernel-release>/...)
    * as root run clean.sh to remove the distro supplied version of the modified modules.
    * finally run make (as normal user) and make install (as root) this installs the modules in /lib/modules/<kernelversion>/extra
    * plug in the device and run iwconfig to see if a wireless device has appeared.
    * setup wireless networking in the normal way for your linux distro. 

Cheers.

Thanks for the help.

---

### Post by Nostalos on 2008-11-19
I tried this several times myself on 8.04 but was never able to get it working with my smart phone.

However as of 8.10  rndis drivers are working out of the box.

---

### Post by IBUA on 2008-11-19
> **Nostalos said:**
> I tried this several times myself on 8.04 but was never able to get it working with my smart phone.

However as of 8.10  rndis drivers are working out of the box.

Cheers ill try 8.10.

---

