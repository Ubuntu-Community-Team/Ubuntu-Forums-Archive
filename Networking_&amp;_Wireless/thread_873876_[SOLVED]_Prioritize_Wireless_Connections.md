---
title: "[SOLVED] Prioritize Wireless Connections"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by bill516 on 2008-07-29
Prioritizing Wireless Connections?

I use a laptop exclusively (Asus Z96J) with a wireless connection.  lspci identifies the chip as an Intel 3945 ABG.  According to iwconfig my connection is established on eth01.   I use WPA Personal.  Network Settings\Wireless Connections shows "roaming mode enabled."  Applications\Passwords & Encryption Keys (Seahorse 2.22.2) correctly lists my network with its very long WPA password.  Seahorse also contains profiles for several other wireless nets I use when I travel.

When I bring up Linux at home (where I am most of the time), nm-applet sometimes appears to know that I am searching for "my net" and it asks for the keyring manager password, as it should.  The connection then is made.  At other times it seems not to find "my net" at all, but it does find others in the neighborhood of no interest to me.  I then indicate "connect to other wireless network."  I do not enter the impossibly long WPA key for "my net.".  If I let nm-applet thrash it usually will open keyring manager.  When I supply the keyring manager password the connection to "my net" then is completed.  This can take 2 to 3 minutes.

Problem:  This is the only sequence that sometimes will completely lock up my system to the point where I must hard reboot.  nm-applet apparently does not call keyring manager.  The result is a complete lockup.  That does not happen frequently, but it has happened.

I assume I can fix this by going back into Wireless Connections and clearing "roaming mode enabled."  Then I should be able to enter my  "my net" configuration manually and save it?  This should solve the problem I have described?

If I am right that would work except that I travel to several locations and I use the same four or five networks when I do.  Do I have to manually configure these each time I change locations?

Is there some way to set up nm-applet (or which application?) so that I can make a prioritized list which says, in effect, "first look for this net, then this net, then this net ... connect to the first one found."

My apologies if the answer to this is somewhere on the forum, but I could not find it.  Thanks for any help!

---

### Post by pytheas22 on 2008-07-29
Network Manager can do some dumb and buggy things.  You may want to try using the connection manager [wicd]("http://wicd.sourceforge.net/") instead; you can install using the package from [here]("http://downloads.sourceforge.net/wicd/wicd_1.4.2-1-all.deb?modtime=1203246585&big_mirror=0").

Once you configure the network that you want to connect to in wicd, you can check a box that says something like, "Always connect to this network."  And it will always connect to that network, not another network, unless you explicitly tell it to do otherwise.  NM likes to try to guess what you want it to do, often with unhappy results.

Also, if you want wicd to always start when you log in to your desktop, go to System>Preferences>Sessions and create a new launcher with the command:
```

/opt/wicd/tray.py
```

(I think that works; if not, let me know).

By the way, installing wicd will force you to uninstall NM.  If for some reason you ever want to get NM back, just run:

```
sudo apt-get install network-manager-gnome
```

---

### Post by bill516 on 2008-07-29
Thank you!  It may take me a day to do this, but I will report back and let you know if it worked.

---

### Post by bill516 on 2008-07-30
Here's where I am with Wicd (July 30).

I downloaded Wicd as explained on the Wicd home page at wicd.sourceforge.net.  I followed the instructions "Installing Wicd in Ubuntu."  That appeared to work.  On completion I found Wicd in Applications\Internet.

I attached an Ethernet cable to my laptop and I made an internet connection.  So the wired interface does work through Wicd.

Repeated attempts to do so through the Wireless port have failed.  Here is what I have done in Wicd Manager.

I show "MyNet WPA" this is correct.

I checked "automatically connect to this network"

Under that line in light grey there appears:

"95%  secured WPA  00:40:F;E7:97:46 Master Channel 6"

The following are clear.  I have not checked these.

"Use Static IPs"
"Use Static DNS"

I have checked "Use Encryption"

I have indicated "WPA 1/2" from the drop-down list

I have inserted my very long passkey from Seahorse and checked it multiple times to make certain it is right.  I believe it is.

In Wicd Manager\Preferences I have tried the default WPA Supplicant driver "wext" and also "IPW"  Using different WPA Supplicant drivers apparently makes no difference.

Also under preferences, Wicd lists the wired connection as eth0 and the wireless as eth1.  I believe this is correct because it is consistent with iwconfig.

I have checked \etc\network\interfaces as suggested in the Wicd install instructions.  As it should, my file contains only the lines

auto lo
iface lo inet loopback

In short, everything I can check (or that I have thought to check, at least) looks right.  But Wicd evidently does not think so, at least on the wireless side of the house.

The fact that the wired connection just fired up immediately makes me think we are close Pytheas22, but I cannot get the rest of the way with the wireless.  Can you help further?

---

### Post by pytheas22 on 2008-07-30
Ah, I guess in this case wicd is being buggier than NM.  Make sure you still have roaming made enabled in the System>Administration>Network utility for your wireless card.  Also be sure that NM is completely uninstalled:
```

sudo apt-get remove --purge network-manager
```

and restart your computer if you haven't since installing wicd.  Also, if your WPA password has weird characters in it, like blank space, $, ^ or something, it might help to change to a password that only uses standard characters.  It will be just as secure as long as it's long and not a word in the dictionary.

If none of those things helps, the only thing that I can think to do is to troubleshoot the wicd connection from the command line.  Connecting to WPA manually is tedious but it can be done.  It involves editing a file called /etc/wpa_supplicant.conf to work with your router.  wicd stores its own wpa_supplicant.conf's, and seeing which one it made for your wireless card--although it apparently doesn't work--would be a start to figuring out which values you need to use.  Once you do figure them out, you can write a script to connect manually to your network, which would work well once it's all set.

So to see which configuration wicd tried to use, please post the output of:
```

cat /opt/wicd/encryption/configurations/*
```

and to learn more about the settings for your wireless network at home:
```

iwlist scanning
```

Doing this by hand isn't going to be easy and there will probably be several failures before you're able to connect, but if you have the time to spend on this issue, I'm willing to do it.

---

### Post by bill516 on 2008-08-04
Update August 4

Linux has been restarted multiple times with no functional wireless capability through Wicd.

The WPA password contains only numbers and upper/lower case characters.

I do not broadcast my SSID, if that is relevant.

You suggested that I make sure "you still have roaming enabled ... for your wireless card."

If I go to System\Administration\Network\wireless connection, I see "This network interface is not configured."  What that means I do not know, since that is also what it says about the Ethernet connection I am using presently.  If I look at "properties" I can check "enable this connection" but it appears I have to fill out the needed SSID and other information relative to my network.  To date I have not had to do this in order for wireless to work. (When it works, of course.)

I do not see some simple-minded box such as "Check here if you love roaming."  I should see that?

Do I need to do something with this configuration?

Here are the results of your several data requests.



> Me@Home:~$ sudo apt-get remove --purge network-manager
[sudo] password for Me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package network-manager is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libglitz-glx1 libglitz1 libnl1 linux-headers-2.6.24-16-generic
  linux-headers-2.6.24-16
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Me@Home:~$

I do not think I want to do anything more here until I know that I need to do it.


> Me@Home:~$ cat /opt/wicd/encryption/configurations/*
cat: /opt/wicd/encryption/configurations/0040f4e79746: Permission denied
Me@Home:~$

Hmm, Permission denied.  On my own machine yet.  This would not seem to be good.

And finally:

> Me@Home:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

eth1      No scan results

And this don't look no gooder, so to speak.  No scanning in sight, it appears.

I can remove Wicd and reinstall NM, but I suspect others are having similar problems if I read the forum correctly.  So if you are willing, let's try to play this out and we'll see what happens.

Thanks so much again, Pytheas22.

---

### Post by pytheas22 on 2008-08-04
It sounds like your wireless driver has become broken.  I'm not sure how--installing wicd should not have had anything to do with that--but there's something strange going on.  What is the output of:
```

iwconfig
dmesg | grep -e eth1 -e iwl
lshw -C Network
lspci
lspci -n
```

I'm wondering if a bad driver has been the problem all along.  If so, it should be easy enough to fix--if worst comes to worst you can always use ndiswrapper instead of the Intel drivers--but please post the output of the commands above so that we can figure out what's going on.  The Network GUI should not be telling you that the interface is not configured.

---

### Post by bill516 on 2008-08-05
Bad driver might make sense, given that NM had been flakey for a time.  Using ndiswrapper with the Intel woud be odd (at least in terms of wht I think I know) but we'll do what works!

Here's the output from your latest request.  Quite verbose, but I assume you want to see it all.

> Me@Home:~$ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Me@Home:~$ dmesg | grep -e eth1 -e iwl
[   34.178685] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   34.178689] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   34.178853] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   34.901159] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   34.902173] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   34.978972] udev: renamed network interface wlan0 to eth1
[   51.378934] ADDRCONF(NETDEV_UP): eth1: link is not ready

Me@Home:~$ lshw -C Network

WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:05:ec:76
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth0
       version: 10
       serial: 00:18:f3:5e:f0:5f
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.1.102 latency=64 maxlatency=64 mingnt=32 module=r8169 multicast=yes

Me@Home:~$ lspci


Once again my thanks for your willingness to stay on this.  We are well beyond where I would have been able to go and I am very curious!
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc M56P [Radeon Mobility X1600]
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
06:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
06:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
06:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
06:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)

Me@Home:~$ lspci -n

00:00.0 0600: 8086:27a0 (rev 03)
00:01.0 0604: 8086:27a1 (rev 03)
00:1b.0 0403: 8086:27d8 (rev 02)
00:1c.0 0604: 8086:27d0 (rev 02)
00:1c.1 0604: 8086:27d2 (rev 02)
00:1c.2 0604: 8086:27d4 (rev 02)
00:1d.0 0c03: 8086:27c8 (rev 02)
00:1d.1 0c03: 8086:27c9 (rev 02)
00:1d.2 0c03: 8086:27ca (rev 02)
00:1d.3 0c03: 8086:27cb (rev 02)
00:1d.7 0c03: 8086:27cc (rev 02)
00:1e.0 0604: 8086:2448 (rev e2)
00:1f.0 0601: 8086:27b9 (rev 02)
00:1f.2 0101: 8086:27c4 (rev 02)
00:1f.3 0c05: 8086:27da (rev 02)
01:00.0 0300: 1002:71c5
04:00.0 0280: 8086:4222 (rev 02)
06:01.0 0c00: 1180:0832
06:01.1 0805: 1180:0822 (rev 19)
06:01.2 0880: 1180:0843 (rev 01)
06:01.3 0880: 1180:0592 (rev 0a)
06:01.4 0880: 1180:0852 (rev 05)
06:07.0 0200: 10ec:8169 (rev 10)

Me@Home:~$

---

### Post by bill516 on 2008-08-05
My apologies!  That last response was mangled and there appeared to be no way for me to remove it.  Perhaps I just do not understand the forum software well enough.  OK, let's try that again and this time I'll review the post before I click that send button!

Here's what I was trying to report:

Me@Home:~$ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Me@Home:~$ dmesg | grep -e eth1 -e iwl
[   34.178685] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   34.178689] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   34.178853] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   34.901159] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   34.902173] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   34.978972] udev: renamed network interface wlan0 to eth1
[   51.378934] ADDRCONF(NETDEV_UP): eth1: link is not ready

Me@Home:~$ lshw -C Network

WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:05:ec:76
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth0
       version: 10
       serial: 00:18:f3:5e:f0:5f
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.1.102 latency=64 maxlatency=64 mingnt=32 module=r8169 multicast=yes

Me@Home:~$ lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc M56P [Radeon Mobility X1600]
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
06:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
06:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
06:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
06:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)

Me@Home:~$ lspci -n

00:00.0 0600: 8086:27a0 (rev 03)
00:01.0 0604: 8086:27a1 (rev 03)
00:1b.0 0403: 8086:27d8 (rev 02)
00:1c.0 0604: 8086:27d0 (rev 02)
00:1c.1 0604: 8086:27d2 (rev 02)
00:1c.2 0604: 8086:27d4 (rev 02)
00:1d.0 0c03: 8086:27c8 (rev 02)
00:1d.1 0c03: 8086:27c9 (rev 02)
00:1d.2 0c03: 8086:27ca (rev 02)
00:1d.3 0c03: 8086:27cb (rev 02)
00:1d.7 0c03: 8086:27cc (rev 02)
00:1e.0 0604: 8086:2448 (rev e2)
00:1f.0 0601: 8086:27b9 (rev 02)
00:1f.2 0101: 8086:27c4 (rev 02)
00:1f.3 0c05: 8086:27da (rev 02)
01:00.0 0300: 1002:71c5
04:00.0 0280: 8086:4222 (rev 02)
06:01.0 0c00: 1180:0832
06:01.1 0805: 1180:0822 (rev 19)
06:01.2 0880: 1180:0843 (rev 01)
06:01.3 0880: 1180:0592 (rev 0a)
06:01.4 0880: 1180:0852 (rev 05)
06:07.0 0200: 10ec:8169 (rev 10)

Me@Home:~$

---

### Post by pytheas22 on 2008-08-05
Things appear to be working normally with the iwl3945 driver, based on your output.  So I'm not sure why it's failing to connect.  Do you still get no scan results from:
```

iwlist eth1 scan
```

If so, I don't know what to do to troubleshoot iwl3945 any more...

There's another native driver called [ipw3945]("http://ipw3945.sourceforge.net/") that you could try.  To install it, run:
```

sudo -s
apt-get install build-essential
echo 'blacklist iwl4965' >> /etc/modprobe.d/blacklist
echo 'blacklist iwl3945' >> /etc/modprobe.d/blacklist
```

Now reboot, then continue with:
```

sudo -s
wget http://bughost.org/ipw3945/ucode/ipw3945-ucode-1.14.2.tgz
tar -xzvf ipw3945-ucode*
cp ipw3945-ucode* /lib/firmware/$(uname -r)
wget http://bughost.org/ipw3945/daemon/ipw3945d-1.7.22.tgz
cp ipw3945d* /sbin
cp ipw3945d*/x86/* /sbin/
wget http://james.colannino.org/downloads/patches/ipw3945-1.2.2.patch
wget http://prdownloads.sourceforge.net/ipw3945/ipw3945-1.2.0.tgz?download
tar -xzvf ipw3945-1.2.0*
cp ipw*patch ipw3945-1.2.0/
patch -p1 < ipw3945-1.2.2.patch
```

You'll be asked which file you want to patch; enter "ipw3945.h"

```
make SHELL=/bin/bash
make install
chmod 777 /sbin/ipw*
touch /etc/modprobe.d/ipw3945
echo 'install ipw3945 /sbin/modprobe -i ipw3945 ; sleep 0.5 ; /sbin/ipw3945d –quiet' >> /etc/modprobe.d/ipw3945
echo 'remove ipw3945 /sbin/ipw3945d –kill ; /sbin/modprobe -r -i ipw3945' >> /etc/modprobe.d/ipw3945
modprobe ipw3945
```

Now reboot and see if you can connect in wicd (or at least if you have an interface recognized).

Installing ipw3945 might be really hard (initially I thought it would be easy, then I tried it myself, realized it wasn't so simple, and just spent an hour figuring out the instructions above...they're adapted from this [guide]("http://www.ubuntugeek.com/using-ipw3945-instead-iwl3945-in-hardy.html"), which claims to work).  But it shouldn't hurt anything--in a worst case, to get back to where you were before ipw3945, you just need to remove iwl3945 from /etc/modprobe.d/blacklist and you'll be back on that driver.

Please give that a shot and see how it goes (but don't be shocked if you get errors).  If ipw3945 doesn't help, we can still try ndiswrapper...

Also please tell me if "iwlist scan" returns anything, as I wonder at the top of this long post...

---

### Post by bill516 on 2008-08-05
OK, here is iwlist per your request.

Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 

I confes I am too ignorant to know what iwlist should return, so I do not know how that looks or what it really tells me.

Meanwhile, I will get to work on your other requests.

---

### Post by bill516 on 2008-08-05
And here is iwlist scan:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

eth1      No scan results

not good, it appears.

---

### Post by bill516 on 2008-08-05
New Information:

I decided on impulse to try Wicd again, ignoring the fact that there is no logical reason it should work.  So I disconnected the cable and rebooted the machine.  Wicd did not appear to work.  It could not see my netowrk despite a wireless router sitting ten feet away.

Then I found "hidden network" on the Wicd menu and gave it my SSID.  Wicd then seemed to behave as though it was attempting a connection, at least it thrashed around longer. But in the end it still could not connect.

Then I noticed a listing for an apparently unprotected router.  I stifled my ethical sense and tried it.  Sure enough, Wicd connected almost immediately and there I was with the New York Times, courtesy of somebody in the neighborhood!  So I immediately disconnected.

This tells me that the Intel driver works and that Wicd works.  The problem is with the hidden SSID/WPA combination?

So, next step is to let the SSID broadcast for a few minutes.  I'll reboot and see what that does.  My suspician:  Despite multiple checks (and believe me they have been multiple!), the problem lies with my WPA password.

But one test at a time.  Stand by while Doofus investigates.

---

### Post by pytheas22 on 2008-08-05
Good to hear that you were able to connect to a wireless network.  I didn't realize that your ESSID was hidden--it *shouldn't* matter, but it could.

Since you know that the driver you have now at least can get you connected, I'd disregard the stuff about compiling ipw3945.  I think the way to go is to see if you can connect with the ESSID being broadcast and WPA, or with hidden ESSID but no encryption (also give WEP a shot; it tends to work better, although as far as securing your network, everyone knows that it's a joke).

---

### Post by imdano on 2008-08-05
You mentioned your wpa key is very long.  How long, exactly?  wpa_supplicant only supports up to 63 characters.

---

### Post by bill516 on 2008-08-06
Pytheas22:

We have a WPA problem, no doubt about it.  If I leave SSID set to "no broadcast" but remove WPA, I can connect almost immediately.

Imdano:  My key is 64 characters long. I counted carefully. If you are right that WPA Supplicant can only deal with 63, we may have found our problem.

Friends I now have still another problem, or misunderstanding.

I have from time-to-time heard about WPA Supplicant, as in "Well, you need ..."

I know it is installed on this machine, so how do I find it in order to configure it?  Is this a terminal-Vim operation?  Fine if it is but I wish I knew.  The command-line does not intimidate me, I just need to know what I am doing when I get there!

If it is true that WPA Supplicant will only allow 63 characters rather than 64, how am I or anyone else supposed to know that?  63 does not strike me as a logical computing number.

If that is true why did NM-Applet usually -- but not always -- connect to my wireless router with ESSID broadcasting off and my 64 character key in use?

Thank you, Imdano, for your possible solution to part of my initial  puzzle.

Pytheas22, you have been a trooper.

Can one or both of you explain what is going on here?

Do either of you know of a way for me to set up a wireless client so that it will attempt to connect from a prioritized list of networks, each of which has its own WPA key?  Each of them is sitting in Seahorse, in fact.

If I could manipulate the order of that list, which I do not seem to be able to do, and something like Wicd could work from it we would have a nifty little tool indeed.

If we could get to that I'd turn cartwheels, especially if I understood how it was done!

In the meantime I can only thank each of you for getting me this far.

I'll check back tomorrow.

P.S.  My initial attempt to send this failed, because the wireless link had been dropped.  I was able to reconnect and send.

---

### Post by pytheas22 on 2008-08-06
> Do either of you know of a way for me to set up a wireless client so that it will attempt to connect from a prioritized list of networks, each of which has its own WPA key? Each of them is sitting in Seahorse, in fact.

wicd would be one way to do that, of course--you tell it which network to connect to automatically and it will always choose that one first.  Another way to do it would be to write a custom script, which would involve figuring out how to connect to your WPA network from the command-line.
> 
I have from time-to-time heard about WPA Supplicant, as in "Well, you need ..."

I know it is installed on this machine, so how do I find it in order to configure it? Is this a terminal-Vim operation? Fine if it is but I wish I knew. The command-line does not intimidate me, I just need to know what I am doing when I get there!

A good guide to connecting manually is [here]("http://ubuntuforums.org/showthread.php?t=571188").  Basically to use wpa_supplicant, you have to write a file at /etc/wpa_supplicant.conf for the network that you want to connect to; in this file, you tell wpa_supplicant the passphrase and other settings of the network.  Then you run a command like:
```

sudo wpa_supplicant -w -D<something> -i<interface> -c/etc/wpa_supplicant.conf
```

and wpa_supplicant negotiates the authentication and authorization to the network for you.  After that, you get an IP address (if you use dynamic IPs) with dhclient, and you're online.

You can try writing a configuration file for your network and seeing if you can connect that way.  It can be complicated to figure out all of the settings that you need to enter for your network, and you probably won't get it on the first or second tries.  But fortunately wpa_supplicant gives good output when you run it to help you figure out what's going wrong (run with the argument '-vvv' for extra-verbose output).

As per imdano's suggestion, you may want to try changing your WPA password to something short and simple, like "password"--no spaces or weird characters--just to see whether you connect that way.  That would help determine whether the length of your passphrase is a problem.  [Wikipedia]("http://en.wikipedia.org/wiki/Wi-Fi_Protected_Access") does say:
> 
The passphrase may be from 8 to 63 printable ASCII characters or 64 hexadecimal digits (256 bits)

so it may be the case that the whole problem is simply that you need to make your passphrase one character shorter.

---

### Post by bill516 on 2008-08-06
OK, I am going to call this solved, since I think I know what to do.  Sounds like some further work, but I ought to be able to figure it out.  I'll post again if I cannot.

My apologies for not catching the problem with the length of the password.  I have been using these passwords for some time and that had just never surfaced.

Take away message:  Overlook nothing.  The gremlins lie well hidden in our assumptions.

You've done a terrific job, my friend, and the people on this forum ought to know it.

One day I might know enough to return the favor to someone.

---

### Post by TBKDan on 2008-09-17
I've been searching a bit to find the answer to a similar issue, and thought I'd post some input: you need to run 'iwlist scan' via sudo.

```
sudo iwlist scan
```
Just in case someone else stumbles along and tries to troubleshoot :)

---

