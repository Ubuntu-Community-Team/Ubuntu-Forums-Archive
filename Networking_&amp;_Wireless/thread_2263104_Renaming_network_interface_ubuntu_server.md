---
title: "Renaming network interface ubuntu server"
date: 2015-01-29
forum: Networking &amp; Wireless
---

### Post by Gixxy on 2015-01-29
Is there a way to rename the network card on a fresh install of Ubuntu server 14.04 from em1 to eth0?

I have tried solutions on the pages with no luck:

[http://askubuntu.com/questions/217635/how-to-rename-an-ethernet-interface](http://askubuntu.com/questions/217635/how-to-rename-an-ethernet-interface)
[http://ubuntuforums.org/showthread.php?t=2220719](http://ubuntuforums.org/showthread.php?t=2220719)
[http://blogs.bu.edu/mhirsch/2012/12/ubuntu-12-10-renaming-ethernet-interfaces-from-p1p1-to-eth0/](http://blogs.bu.edu/mhirsch/2012/12/ubuntu-12-10-renaming-ethernet-interfaces-from-p1p1-to-eth0/)

Seems like this should be easy and maybe I am missing something stupid.

---

### Post by tjiagoM on 2015-04-08
(Similar question here: [http://ubuntuforums.org/showthread.php?t=2263073](http://ubuntuforums.org/showthread.php?t=2263073))

Hello,

I had the same problem as you (I had a em1 NIC instead of a normal eth0). After trying several things, the one that solved my problem was this:

Edit /etc/default/grub and find these lines:
[FONT=courier new]GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""[/FONT]

Add biosdevname=0, just like this:
[FONT=courier new]GRUB_CMDLINE_LINUX_DEFAULT="biosdevname=0"
GRUB_CMDLINE_LINUX="biosdevname=0"[/FONT]

Then run:
[FONT=courier new]sudo update-grub
sudo reboot[/FONT]

At least this worked for me. After that I modified the /etc/network/interfaces in order to have the IP I wanted for eth0.
If this didn't work for you, I also made some changes before this, maybe they could work for you:

[B]First try
[/B]Get your MAC address like you did or with this command (look for the serial attribute):
[FONT=courier new]sudo lshw -class network[/FONT]
Then:
[FONT=courier new]cd /etc/udev/rules.d
sudo nano 70-persistent-net.rules[/FONT]
Add this(substitute the xx:xx:xx:xx:xx with your MAC address. I don't know if dev_id should be the physical id of the "lshw" command):
[FONT=courier new]SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="xx:xx:xx:xx:xx:xx", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"[/FONT]
And reboot!


**Second try**
[FONT=courier new]sudo cp /lib/udev/rules.d/75-persistent-net-generator.rules /etc/udev/rules.d/
cd /etc/udev/rules.d
sudo nano 75-persistent-net-generator.rules[/FONT]
And add at the end this(substitute xx:xx:xx with the first part of your MAC address):
[FONT=courier new]ENV{MATCHADDR}==”xx:xx:xx:*”, GOTO=”globally_administered_whitelist”[/FONT]
And reboot!

---

### Post by slickymaster on 2015-04-08
Closed. Duplicate [here]("http://ubuntuforums.org/showthread.php?t=2263073").

Please do not create duplicate threads, it dilutes the community’s efforts to provide support and causes confusion.

---

