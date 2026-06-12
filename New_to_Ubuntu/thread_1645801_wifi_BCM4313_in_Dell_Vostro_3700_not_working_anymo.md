---
title: "wifi BCM4313 in Dell Vostro 3700 not working anymore"
date: 2010-12-15
forum: New to Ubuntu
---

### Post by jaykubun on 2010-12-15
Hello there!

I had my wifi already working with kubuntu 10.10 on my Dell Vostro 3700. After a suggested kernel update I lost my wifi capabilities. Here is the infos that might be relevant:

```

$uname -r
2.6.35-23-generic

``````

$lspci | grep Net
12:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)
``````
$sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4313 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:12:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:fb400000-fb403fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:13:00.0
       logical name: eth0
       version: 03
       serial: f0:4d:a2:9b:9e:81
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.59 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:46 ioport:d000(size=256) memory:d2c04000-d2c04fff memory:d2c00000-d2c03fff memory:fb300000-fb31ffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

When I go to Applications->System->Additional drivers I see two Broadcom dirvers, namely Broadcom STA and Broadcom 802.11n. I tried to activate first one, then the other  and also both, but with no change in the behavior. Currently the Additional driever panel states that the Broadcom 802.11n is activated and in use. Well, that is apparently not the case. 
In Network Manager there is a checkbox "Enable wireless" that is checked, but no network appears.

Neither ifconfig nor iwconfig show my wlan.

What is going wrong here? Please help, for I am pretty lost at this point.

Cheers,
Jay

PS: This is a repost of my question in this thread [http://ubuntuforums.org/showthread.php?p=10240452]("http://ubuntuforums.org/showthread.php?p=10240452")
, but since this thread was not mine and is solved I start my question now in its own thread.

---

### Post by Hippytaff on 2010-12-15
You might have a driver comflict which means you would need to blacklist the conlficting driver....however have a read of this first - [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by jaykubun on 2010-12-15
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) was new to me, but unfortunately not really helpful. I followed the advice and 

```
sudo apt-get install bcmwl-kernel-source
```

did actually do something and from what i understood it compiled a wl.ko module. But after a reboot I typed in

```
$sudo modprobe -r b43 ssb wl
WARNING: All config files need .conf: /etc/modprobe.d/intel-5300-iwlagn-disable11n.conf_backup, it will be ignored in a future release.

```

So there is a warning that i don't understand. Then I typed in

```
$ sudo modprobe wl
WARNING: All config files need .conf: /etc/modprobe.d/intel-5300-iwlagn-disable11n.conf_backup, it will be ignored in a future release.
FATAL: Error inserting wl (/lib/modules/2.6.35-23-generic/updates/dkms/wl.ko): Invalid argument

```

[LEFT]This time an error happend. I don't know what I am doing here. But I should maybe add, that I already tried all sorts of things, including the attempt to plug in a usb wlan adapter (TP-Link TL-WN821N). This 
also did not appear in the Network manager or ifconfig or iwconfig. I found a description somewhere 
about installing that device in ubuntu, but it involved a lot of makes and stuff and I guess I maybe did 
something serious to the kernel there... I am really sorry now, because I did not document what I was doing and I don't know how I changed the system. I gave up on the TP-Link device and focussed back on the Broadcom internal wlan card. So far with no success. Can anyone suggest how I get out of this mess without a clean install of everything?

Thanks,
Jay 
[/LEFT]

---

### Post by wep940 on 2010-12-15
It's hard for us to know where your system stands now.  The easiest route?  It may be easier for you at this point to back up what you need and reinstall Ubuntu.  After installation, don't do the stuff you were doing - that's all way out of date.
 
Instead, if possible, connect a hard-wire between your computer and the router and in a terminal type "sudo apt-get update".
 
Then, or if no hard-wire connection is possible, look in System/Administration/Additional Drivers and see if a driver is listed there for your wireless.  If so be sure it is enabled.
 
If you had a hard-wired connection, disconnect it now.
 
Right-click on the network manager icon and be sure that "Enable Wireless" shows and is enabled.
 
Left-click on the network manager icon and see if wireless networks show.
 
If not, STOP here and post back, don't do anything else!

---

### Post by Hippytaff on 2010-12-15
If the drivers you installed from -> additional drivers, that you mention in the opening post, are not working with this kernel, try an earlier kernel from the option at the grub menu (the one that lets you choose os's, recovery mode and previously installed kernels)

---

### Post by jaykubun on 2010-12-15
Booting from the old kernel doe not change the situation. No wlan shows up in the Network manager etc. I really would like to avoid a fresh install if possible, but oh well... I might have to go for that solution in the end. Thanks for the advice so far.

Jay

---

### Post by Hippytaff on 2010-12-15
I have to shoot off now, but if you do decide on a fresh install look into having a seperate /home partition, so that in future, if you have to reinstall for whatever reason, you get to keep your files and settings, so it's not such a problem if you haven't got stuff backed up :-)
 
(I learned that the hard way)

---

### Post by wep940 on 2010-12-15
+1
 
When you go through the install, select manual partitioning.  Delete your existing Linux partitions, then create:
 
1 as swap
 
1 as ext4, mount point "/"
 
1 as ext4, mount point "/home"
 
That should help.  Others may have suggestions as well.

---

### Post by jaykubun on 2010-12-16
Well, I did as you suggested and reinstalled the whole Kubuntu OS. I updated everything - including the kernel update. Rebooted and then installed the STA Broadcom driver. And behold and see, it works. I am happy for now :p and close this thread.

Jay

---

### Post by Gaiter on 2011-01-21
I had almost exactly the same issue on an emachines eM350 NAV51 with a BCM4313 card after upgrading to kernel 2.6.35-24-generic.

Solved the issue and also a niggling speed issue by removing the driver, and recompiling the wl driver from Broadcom.

[Instructions are here]("http://www.broadcom.com/docs/linux_sta/README.txt")

:P

(Running 10.10 Kubuntu)

---

### Post by Hippytaff on 2011-01-22
Welcome Gaiter and thanks for posting a fix for this problem :-)

---

