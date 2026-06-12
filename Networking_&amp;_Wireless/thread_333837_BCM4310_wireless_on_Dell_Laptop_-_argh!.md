---
title: "BCM4310 wireless on Dell Laptop - argh!"
date: 2007-01-08
forum: Networking &amp; Wireless
---

### Post by RainGeek on 2007-01-08
Early warning - I'm new to linux and Ubuntu.

I've installed 6.10 "Edgy" on a Dell Latitude D620 laptop. It has a BCM4310 wireless card. Until just a few days ago I had Xandros Linux running on the same hardware without any problems. Under Xandros I just pointed the ndiswrapper at the bcmwl5.inf file and off it went, worked like a charm.

I can't get this thing to work on Ubuntu.

I've followed the instructions on the HUGE thread for "HOWTO: Broadcom 4318 Wireless Cards". I suspect I am missing something very easy, but I can't figure it out. Help!

I've attached a text file with my complete log of everything I've done to try to get this to work. I know it's long, but I figure it would be better to check my newbie actions this way. Remember that this was done on a fresh install of Edgy.

I use WPA on my wireless network and I can't really take that down without screwing up the other computers on my network. I know I have to install wpa_supplicant after I get the wireless card working, but I can't get to that point!

Here is some of the diagnostics to get started (these are repeated in the attached file, at the end). Let me know if I need to provide any additional information.

Thanks,
-RG

geek@aqua:~$ ndiswrapper -l
Installed drivers:
bcmwl5          driver installed, hardware present 

geek@aqua:~$ lspci | grep Broadcom
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)

geek@aqua:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet dhcp

geek@aqua:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

#eth0 mac 00:16:ce:2d:e5:cd arp 1
eth1 mac 00:14:22:f6:fc:50 arp 1

geek@aqua:~$ cat /etc/modprobe.d/ndiswrapper
alias wlan0 ndiswrapper

geek@aqua:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
ndiswrapper
ndiswrapper
ndiswrapper

geek@aqua:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:14:22:F6:FC:50  
          inet addr:192.168.0.13  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:22ff:fef6:fc50/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:77 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9944 (9.7 KiB)  TX bytes:4496 (4.3 KiB)
          Interrupt:185 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

geek@aqua:~$

---

### Post by n00b@linux on 2007-01-08
It looks to me like:
(a) the kernel has recognised the device (results from 'lspci | grep Broadcom' result)
(b) the kernel module has been installed (result from 'ndiswrapper -l')
and that you just need to configure an interface for it (no listing for in 'cat /etc/network/interfaces').
 
Just to double check, run```
iwconfig
```and post the results.

---

### Post by RainGeek on 2007-01-08
First - thanks for the assist! I appreciate it. :-)

Results from iwconfig below:

```

geek@aqua:~$ iwconfig
lo            no wireless extensions

eth1        no wireless extensions

sit0         no wireless extensions

```
Thanks,
-RG

---

### Post by RainGeek on 2007-01-12
Anybody?

Some other things to ponder:

Using the Gnome Admin tools (System -> Admin -> Network Settings) my wireless card doesn't even show up in this tool. I can see the eth1 card (aka wired connection) and Modem, but no wireless card.

I installed network manager, and it only displays "Wired Connection", it does not show any wireless information.

And yes, my laptop has a physical switch to turn on/off the radio. I've checked it five times and it is set to ON. I even rebooted just to make sure.

When I do a lshw -C network command, the entry for the wireless controller says "*-network UNCLAIMED".

(I can post the actual code later, I'm on the wrong system at the moment)

So, anyone?

-RG

---

### Post by hoek on 2007-07-25
im having the exact same problem except im using an hp notebook

---

### Post by gangolli on 2007-07-25
Here's a hunch.  Does 

> 
lsmod | grep bcm


show bcm43xx by any chance?  If so, add a line to blacklist it in /etc/modprobe.d/blacklist.   Reboot.
Now do the same lshw -C network and see if things are better.

---

### Post by kevdog on 2007-07-25
Couple  of things, you are close to getting it working, but as the other poster hinted, you are still probably loading the alternative bcm43xx driver.  You can check definitively with both:
lsmod | grep bcm43xx
lshw -C network

The last command will tell you the driver associated with your card.  If bcm43xx is shown, you need to add the statement:
blacklist bcm43xx
to /etc/modprobe.d/blacklist

Next, within /etc/modules, ndiswrapper only has to be listed once, so I would gksu gedit /etc/modules and remove the extra entries.  You dont get more points for listing it multiple times.

Ndiswrapper by defaults sets up an interface on wlan0.   I believe your old wireless interface was eth1.  What you need to do is to first edit your /etc/iftab file:
gksu gedit /etc/iftab

and change eth1 to wlan0 (if the listed MAC address truly represents the MAC address of your wireless card).

Based on the last change, you are also going to have to change eth1 to wlan0 in your /etc/network/interfaces file.

Although I recommend to everyone to take away WPA initially, if you can make the changes above, reboot, and then verify on reboot that
lshw -C network
shows ndiswrapper as the driver associated with your card, and
iwlist scan
shows your network and lists WPA modes, then I think we can proceed to the next step, without going through the initial verification step.  Kind of a leap of faith approach that everything would work without encryption.

---

### Post by smalldog on 2008-07-18
Dear all BCM4310 users, we are out of luck. Of course, I have purchased a laptop with such wireless card. It works only under non-encrypted condition and from the [http://linuxwireless.org/en/users/Drivers/b43]("http://linuxwireless.org/en/users/Drivers/b43")   founded that such card is not yet support by linux.

---

