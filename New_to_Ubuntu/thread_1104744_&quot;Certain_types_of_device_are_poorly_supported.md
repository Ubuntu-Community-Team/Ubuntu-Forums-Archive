---
title: "&quot;Certain types of device are poorly supported by Ubuntu&quot;"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by Inquiring on 2009-03-23
I was thinking of switching to Ubuntu from Windows, but aside from the learning curve, the Switching page says this:

[INDENT]Certain types of device are poorly supported by Ubuntu for various reasons. If you have such a device, it may be difficult or impossible to get it to work under Ubuntu. Below is a list of some poorly-supported device types:

[LIST]
[*]Software dial-up modems
[*]Some USB broadband modems
[*]Scanners
[/LIST][/INDENT]

Is the lack of support inherent in Linux? If not, are there any plans to support these devices in the future?

I use my dial-up modem and scanner for sending the occasional fax. Switching to Linux would apparently require buying a fax machine and new scanner, not to mention creating possible other hardware problems. It's not even the cost--I'd like to get off the MS treadmill, but avoiding hardware problems is one reason people aren't upgrading to Vista. I don't need to go to an entirely unfamiliar OS and have hardware problems on top of it. Also, I don't see a lot of Linux drivers out there (e.g., for my Sony CRT monitor).

Also, I note that support for releases typically ends after three years. Can new releases be installed with minimal disruption, i.e., not having to reinstall applications, etc.?

Thanks.

---

### Post by chuckyp on 2009-03-23
The best way to find out if your hardware is supported is to boot the installation cd. It boots in to a full working OS that doesn't install anything to your HDD until you run the install routine. 

Also when a new version of ubuntu comes out you will be prompted and asked if you want to upgrade via the software upgrade icon. This is usually a seamless upgrade as long as you stick to the built in repositories for software. If you start installing software from third party (unsuported) repos you may run in to a problem. Also all you're settings will be unchanged ex: customizations to backgrounds application specific settings etc... All apps will be updated if they are from the repos.

I've found that unless you really have some obscure hardware you won't have any issues with drivers. The more people that are using your hardware the better chance that a linux driver was written by someone. For instance my HP printer and my camera just work. Plug them in and devices are detected automatically the way windows should be.

---

### Post by Inquiring on 2009-03-23
Thanks. I don't have the install CD, but what about Wubi, which I read about recently? It allows you to run Linux on a PC like another application.

---

### Post by mocoloco on 2009-03-23
> **Inquiring said:**
> Is the lack of support inherent in Linux? If not, are there any plans to support these devices in the future?

You'd have to ask the manufacturers of your device if they have plans for Linux support in the future, since it's up to them to release drivers, or the specifications so that others can write drivers.
For example many modems were made without the full modulation capabilities, and were built to rely on Windows system calls and CPU cycles. These are called [winmodems]("http://en.wikipedia.org/wiki/Softmodem"). You can still get some winmodems to work under Linux and Ubuntu.
As chuckyp said, try booting from a liveCD and see what works off the bat. For what doesn't just a bit of research on the specific device or chipset can lead you to know how hard it is to get it working under Ubuntu.

Edit: sure Wubi's a great option too.

---

### Post by Inquiring on 2009-03-24
> **mocoloco said:**
> You'd have to ask the manufacturers of your device if they have plans for Linux support in the future, since it's up to them to release drivers, or the specifications so that others can write drivers.
Okay, thanks. These are older devices, so I imagine probably not, but I'll give Wubi a try.

---

### Post by freesitebuilder on 2009-03-24
These two sites have lists of compatible hardware:
[http://www.ubuntuhcl.org/index](http://www.ubuntuhcl.org/index)
[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

The second page relies on us users updating the wiki with our experiences. :)

---

### Post by 3rdalbum on 2009-03-24
> **Inquiring said:**
> Thanks. I don't have the install CD, but what about Wubi, which I read about recently? It allows you to run Linux on a PC like another application.

No, it's a Windows program that installs Ubuntu in a dual-boot configuration. It's not a virtual machine or emulator. Using a virtual machine probably won't help a lot as a virtual machine doesn't expose your real hardware to Linux.

Just boot up from the Ubuntu desktop CD - it's the most common CD that you get on magazine coverdiscs and from the Shipit service. Try out your scanner and modem there.

Lack of hardware support is usually apparent in any alternative operating system where there are no standards. Every scanner communicates with the computer differently. Every USB-connected ADSL modem and all "softmodems" communicate differently. You'd find that USB-connected ADSL modems and dialup softmodems won't work on Mac OS X either; it's not inherent to the operating system, it's just due to there being poor vendor support.

Hardware problems shouldn't stop anyone from switching to Vista these days; everything made in the last couple of years will come with Vista drivers. Another reason why you don't see Linux drivers about is that most things are already supported in the kernel; oh, and monitors don't need drivers.

---

### Post by billgoldberg on 2009-03-24
Why don't you post the brand and model of your scanner and modem?

If it doesn't work out of the box, don't panic, there are still a lot of companies that have linux drivers on their website.

I had to install the driver for my scanner manually, and it works perfectly.

--

Your question about upgrading.

A new version of Ubuntu comes out every 6 months. But most are supported for 3 years (lts releases for 5 years). 

After three years it would still be possible to upgrade, but an clean install (from cd, usb, ...) would be better and faster.

If you upgrade, the programs you installed will be upgraded as well.

---

### Post by wannadumpwindows on 2009-03-24
> **Inquiring said:**
> Okay, thanks. These are older devices, so I imagine probably not, but I'll give Wubi a try.

Older devices, assuming they aren't too old, are usually supported better than newer ones. People have had time to reverse engineer the software, or write drivers for those devices, so in most cases, older hardware usually works without any hassle.

---

