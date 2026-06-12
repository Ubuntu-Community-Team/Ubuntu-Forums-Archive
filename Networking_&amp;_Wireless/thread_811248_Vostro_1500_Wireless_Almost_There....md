---
title: "Vostro 1500 Wireless Almost There..."
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by tufcamman on 2008-05-28
Hi, I've recently done a fresh install of hardy on my Vostro 1500.  After all the updates everything is working great, except of course for the wifi adapter.  I've scoured the forums and found that the card is supposedly compatible with linux, and it scans and finds networks great, and I can even connect to them, but there is no throughput.  I have tried protected and unprotected networks.  Same thing, I can connect to them, but when I try to ping anything I get nothing in return.  Here is the output of my lspci:

```
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```

I have tried using Ndiswrapper and it did not sit well with my system.  If anybody has any ideas that would be great.  Thanks!

---

### Post by tufcamman on 2008-05-29
Allright, I promptly found the solution on my own.  And for the benefit of those who will view this I will post it here.

Hardy uses a different wireless driver than past ones, and you need to use the older driver to make it function properly.

Go into the software sources and enable the hardy backports, refresh the list then enter this code:

```
sudo apt-get install linux-backports-modules-hardy-generic

```

Reboot the computer and thats it, fully functional wireless on that particular intel chipset.  Good luck!

Here is where I got that information:

[http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/](http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/)

---

### Post by maahony on 2008-05-30
I'm using the Intel PRO/Wireless 3945ABG card as well. I enabled the unsupported updates in Adept and installed the updates. I ran the command line sudo apt-get install linux-backports-modules-hardy-generic. Restarted and then went into Network Settings - in the wireless interface config I set the tcp/ip to auto dhcp and setup the wireless ESSID and WEP key of type ASCII. Enabled the interface and got the following error:


Error while listing network interfaces - KDE Control Module
Could not parse the XML output from the network configuration backend.


I've looked at a number of sources and prior to this error the previous steps resolved the issue with not being able to find/connect wireless networks. Any ideas?

---

