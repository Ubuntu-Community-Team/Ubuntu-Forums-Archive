---
title: "Speed and Duplex problem in Ubuntu 13.04"
date: 2013-09-07
forum: Networking &amp; Wireless
---

### Post by akb12 on 2013-09-07
Hello friends, 

I am new to Linux and just know how to copy and paste commands to get things done. But in this case I am not able to solve my problem despite having some guidence available on net.  I am facing a speed and duplex problem here. I am dual booting Windows 8 and Ubuntu 13.04. My network connection only works if I set speed and duplex to 10mbps full duplex. If I don't set it to 10mbps the LED light in modem which shows LAN connectivity becomes on for a second and goes off for two seconds which implies that the connection is not established properly between PC and modem.  It is easy to do in windows because in ethernet card settings I set speed and duplex to 10mbps and it remains always same even after reboot so I have no problem here.  

Now when I boot into Ubuntu the LAN starts acting up again. I know how to set speed and duplex in Ubuntu with following commands :

sudo ethtool -s eth0 speed 10 duplex full

After giving this command it works perfectly. But when I reboot these settings are lost and I have to give command again. I want them to become permanant but don't know how to add some kind scripts or edit any file in etc/network. I tried some of the suggestions avilable on net but then I faced a problem, when I rebooted Ubuntu it shows me a massage that it is waiting for network to start and after one minute it waits again for another minute. After having Ubuntu started I found no internet connection. Though I don't have working internet connection in this scenario(after editing some files in etc/  to make it permanat) but the LAN LED becomes stable like it shoud be when it works good.

So friends please guide me to overcome this problem set by step. If I missed something important to mention her please forgive me. :(

---

### Post by chili555 on 2013-09-07
> after editing some files in etc/ to make it permanatWhich? We need to know so we can review and tweak them.

---

### Post by akb12 on 2013-09-07
I followed these steps

If you want to setup eth0 10 or 100 or 1000 speed with ethtool try this[INDENT]sudo ethtool -s eth0 speed 10 duplex full
 
 
[/INDENT]
If you want to make it permanent you have to add following lines to /etc/network/interfaces file[INDENT]gksudo gedit /etc/network/interfaces
[/INDENT]
Add the following line[INDENT]pre-up /usr/sbin/ethtool -s $IFACE autoneg off 100 duplex full
[/INDENT]
Save and exit the file.

---

### Post by Kevin_Arnold on 2013-09-07
Have you tried just replacing the network cable? A lot of times there is a physical reason in a piece of hardware that a NIC can't connect at 100/1000 full.

---

### Post by akb12 on 2013-09-07
Yes I changed the cable yesterday but it didn't change the result. I have a strong belief that it is my motherboard because since I have switched to this MB I am facing this problem.

---

### Post by chili555 on 2013-09-07
> **akb12 said:**
> I followed these steps

If you want to setup eth0 10 or 100 or 1000 speed with ethtool try this[INDENT]sudo ethtool -s eth0 speed 10 duplex full
 
 
[/INDENT]
If you want to make it permanent you have to add following lines to /etc/network/interfaces file[INDENT]gksudo gedit /etc/network/interfaces
[/INDENT]
Add the following line[INDENT]pre-up /usr/sbin/ethtool -s $IFACE autoneg off 100 duplex full
[/INDENT]
Save and exit the file.Please do:```
gksudo gedit /etc/network/interfaces
```Remove the line(s) you added; proofread, save and close gedit. Now do:```
gksudo gedit /etc/rc.local
```Add this line right above exit 0:```
ethtool -s eth0 speed 10 duplex full
```No sudo is needed there. Proofread, save and close gedit.

You should be all set.

---

### Post by akb12 on 2013-09-07
It didn't work. I did what you said.

---

### Post by akb12 on 2013-09-08
Is that all I can do?

---

### Post by chili555 on 2013-09-08
> **akb12 said:**
> Is that all I can do?Please try changing /etc/rc.local to:```
ethtool -s eth0 speed 10 duplex full autoneg off
```Again, right above exit 0. Now does it persist after a reboot?

---

### Post by akb12 on 2013-09-08
Please have a look at this screenshot. I did save this file but it didn't work. During reboot no massage no warning and it was disconnected again.

---

### Post by chili555 on 2013-09-08
Let's have a look at what the driver is doing as you boot. Find out the driver with:```
sudo lshw -C network
```The driver will be listed like this from my machine as an example:> chili@Think410:~$ sudo lshw -C network
  *-network DISABLED      
       description: Ethernet interface
       product: 82577LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 06
       serial: xx:de:f1:3e:b2:xx
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes [COLOR="#FF0000"]driver=e1000e[/COLOR] driverversion=2.1.4-k firmware=0.12-1 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:42 memory:f2600000-f261ffff memory:f2625000-f2625fff ioport:1820(size=32)
Please post that result as well as:```
dmesg | grep -e eth0 -e *driver*
```...where *driver* is the driver you found above. So, in my example, I'd want to see:```
dmesg | grep -e eth0 -e e1000e
```Yours will probably be different.

Your /etc/rc.local file looks fine. I suspect something else is wrong here.

---

### Post by akb12 on 2013-09-08
Here is the output of both commands.

---

### Post by chili555 on 2013-09-08
Sorry to see that. The driver r8169 has a bad reputation and is often replaced with a different driver. Before we sharpen our scalpels and start surgery, let's try another thing or two. I am encouraged because you can get it to work as expected with a terminal command, so we know it can work.

Please try changing the /etc/rc.local file to:```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
ifconfig eth0 down
sleep 3
ethtool -s eth0 speed 10 duplex full autoneg off
ifconfig eth0 up

exit 0

```Proofread, save, close, cross fingers and reboot.

---

### Post by akb12 on 2013-09-08
To my disappointment it again failed to connect. What would we do now?  I was also suspecting my mobo for this because when I use PCI LAN card instead of my mobo's LAN port I face no such problem. But now I have installed a sound card in that PCI slot so can not use PCI LAN card instead. Do I still have any chance?

---

### Post by chili555 on 2013-09-08
Does it still work to set the parameters from the terminal after it's fully booted?

---

### Post by akb12 on 2013-09-08
It only works when I give this command after fully booted             
sudo ethtool -s eth0 speed 10 duplex full

sometimes it works automatically without any command. But very seldom.

---

### Post by akb12 on 2013-09-09
Here is the latest development, I was searching for new drivers for my mobo's LAN and I found the latest one at Realtek website. I downloaded the drivers for Win 8 and for Ubuntu. First I installed the driver in Windows and I saw no change in its behavior so again I set Speed and Duplex to 10mbps in Windows and it started working again as it used to do. Now I booted in Ubuntu and It worked fine, since then I tried 10 times to reboot and it is working good. I didn't installl downloaded drivers in Ubuntu. By the way I have had followed all the instructions given by you and in the last I did this driver installation thing. 
 Don't know how could this happen. Driver installation in Windows resolves issue in Ubuntu.

---

