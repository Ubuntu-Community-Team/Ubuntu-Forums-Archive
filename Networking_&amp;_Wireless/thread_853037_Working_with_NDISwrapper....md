---
title: "Working with NDISwrapper..."
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by Master_Glink on 2008-07-08
I finally set-up my wired connection, and I also downloaded the NDISwrapper and the Win98 driver that I needed. I managed to install it successfully and it registers as hardware is present, however when I go to set up my network I still cannot see any access points...

Here's the first situation:
[[IMG]http://img34.picoodle.com/img/img34/4/7/8/t_Hardwareprem_fc2dad6.png[/IMG]](http://www.picoodle.com/view.php?img=/4/7/8/f_Hardwareprem_fc2dad6.png&srv=img34)

But, here's what I get:

[[IMG]http://img37.picoodle.com/img/img37/4/7/8/t_Noaccessm_99c5607.png[/IMG]](http://www.picoodle.com/view.php?img=/4/7/8/f_Noaccessm_99c5607.png&srv=img37)

---

### Post by ruggrat on 2008-07-08
I can't help you, but I'll chime in that I get the same screens with ndiswrapper.

---

### Post by superprash2003 on 2008-07-08
have you tried rebooting your pc.. it normally helps..

---

### Post by Master_Glink on 2008-07-08
I've rebooted several times, after updates and programs I've just installed since this is the first time I've managed to get a working connection, but still nothing has changed with my wireless connectivity.

Thanks for the suggestion though, I'm not giving up so if you have any more ideas or advice please post them here.

---

### Post by superprash2003 on 2008-07-08
in the terminal type iwconfig and post output here

---

### Post by Master_Glink on 2008-07-09
Here's what I get:

> 
lo        no wireless extensions.

eth0      no wireless extensions.



---

### Post by Master_Glink on 2008-07-10
Bump.

---

### Post by kevdog on 2008-07-10
Lest start debugging:

lshw -C network (may show use if a driver is being used)

---

### Post by Master_Glink on 2008-07-10
Here's what I get with the lshw -C network command:

>   *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 01
       serial: 00:e0:b8:e7:e4:d5
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=10.0.0.75 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s


---

### Post by kevdog on 2008-07-10
See even though you are tyring to use ndiswrapper, the driver loaded is the following:

module=r8169

When you loaded the win98 driver inside ndiswrapper and it stated device present -- can you reproduce this statement?  I need to see what it stated was the alternate driver.

If not do the following

sudo rmmod r8169
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist

Then reboot.

---

### Post by Master_Glink on 2008-07-11
From what I understood, yes I get the same response every time I check NDISwrapper, however I don't know what you mean by alternate drivers.

I also tried the commands you specified, but all it said was:


> ERROR: Module r8169 does not exist in /proc/modules

> blacklist r8169

Also, it killed my wired connection.

---

### Post by Master_Glink on 2008-07-11
Bump.

---

### Post by james_vanb on 2008-07-11
run:

```
ndiswrapper -l
```

This will list the driver installed and any alternates.

Any reason you loaded the win98 driver and not the xp driver?  I've always used the xp driver with ndiswrapper.

---

### Post by Master_Glink on 2008-07-12
This is what I get from ndiswrapper -l:

> net8187b : driver installed
	device (0BDA:8189) present


As for installing the Win98 driver: I actually installed the Xp driver first, but since that didn't work I changed the driver to the Win98 to see if that one worked.

---

### Post by james_vanb on 2008-07-12
Could you post output from:

```
iwconfig
```

Is it different from your previous post?

What Wireless Card/USB are you using?

Have you looked through this?

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

---

### Post by james_vanb on 2008-07-12
Just came across a Tutorial that mentions your driver:

> Users of RTL 8180, RTL8185, RTL 8187 using the built in native r8187 / r818x drivers

By default the r8187 and r818x drivers are blacklisted due to a know bug. These drivers are usuable however with a twist to the above methods

If you want to try using these drivers, please load the kernel modules:

sudo modprobe r818x
sudo modprobe r8187

These drivers require a bogus or extra letter be suffixed to the essid name in order for these drivers to work

For example if your are trying to connect to a router with essid=Router, at he command line you would type essid=Routerx. Notice the extra x or bogus character. I have provided an example using the unencrypted connection procedure below, however this extra character needs to be used if attempting to connect to all network types (unencrypted/ WEP / WPA)

sudo ifconfig [interface] down
sudo dhclient -r [interface]
sudo ifconfig [interface] up
sudo iwconfig [interface] essid “Routerx”
sudo iwconfig [interface] mode Managed
sudo dhclient [interface]

If these drivers work for you, and you would like these drivers to load automatically at startup for you, avoiding to have to type sudo modprobe everytime, please edit your blacklist file

gksu gedit /etc/modprobe.d/blacklist

And comment out (or prefix the following lines with a # sign). You want the following lines to appear as below:

#blacklist r8187
#blacklist r818x

Link is here FYI:

[http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html](http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html)

---

### Post by Master_Glink on 2008-07-13
Yeah, I've looked through that tutorial too, before I had a wired connection and before I had downloaded the updates, but I didn't have any drivers in my blacklist.

---

### Post by superjith on 2009-12-27
i am also using rtl 8187 and my usb dongle gets activated[used ndiswrapper and win98 driver] but the led light is dimmer & it doesn't connect to the internet.

can someone tell me what to do ???  :confused:

---

### Post by bkratz on 2009-12-27
Are you plugging directly into the computer or through a non-powered port expander dongles typically use a lot of power?  Also you might try a different port--I've seem where some are 1.1 compatible while others in the same machine are 2.0 compatible.

---

### Post by superjith on 2009-12-28
but everythin's fine when i am using xp . and i am using network manager to connect ,it says connection established but i cannot connect to the internet & my network ip is also not the same when i use ubuntu.

---

