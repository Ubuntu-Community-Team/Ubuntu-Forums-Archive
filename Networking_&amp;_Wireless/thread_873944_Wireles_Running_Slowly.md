---
title: "Wireles Running Slowly"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by snkngshps on 2008-07-29
I recently got a new laptop and did a fresh install of hardy 8.04 on it. My wireless connects without any problem but I've noticed it runs very slowly. Torrents that have reach speeds around 200-250kbs on my other computer only get a max of like 40kbs on this one, and when that is happening it slows down my browsing speed immensly. Does anyone know what could cause that problem?

---

### Post by pytheas22 on 2008-07-29
It could be weaker signal strength, which could be the result of a less powerful wireless card, being farther from the router or a less efficient wireless driver.  To help troubleshoot the problem, please provide the output of:
```

iwconfig
lshw -C Network
iwlist scan
```

Also, have you ever run another operating system on this same computer (e.g. Windows) with the same wireless card, and if so, was the transfer rate alright there?

---

### Post by snkngshps on 2008-07-29
> **pytheas22 said:**
> It could be weaker signal strength, which could be the result of a less powerful wireless card, being farther from the router or a less efficient wireless driver.  To help troubleshoot the problem, please provide the output of:
```

iwconfig
lshw -C Network
iwlist scan
```

Also, have you ever run another operating system on this same computer (e.g. Windows) with the same wireless card, and if so, was the transfer rate alright there?
I haven't tried the wireless with Windows on this computer. It came with vista but I installed ubuntu the minute I got it. Thanks for the help!


joshua@SNKNGSHPS:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:0F:66:DB:17:BD   
          Bit Rate=11 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=88/100  Signal level=-46 dBm  Noise level=-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



joshua@SNKNGSHPS:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:87:6f:c9
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1b:fc:82:56:37
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.106 multicast=yes wireless=IEEE 802.11g




joshua@SNKNGSHPS:~$ sudo iwlist scan
[sudo] password for joshua: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:66:DB:17:BD
                    ESSID:"linksys"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=93/100  Signal level=-41 dBm  Noise level=-70 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:tsf=00000013eefd5d26

---

### Post by pytheas22 on 2008-07-29
Thanks for the information.  You're using b43, the "next-generation" driver for Broadcom wireless cards, which I've heard has some signal-strength issues.  You can try using bcm43xx, the older Broadcom driver, which is more reliable (and has fewer features, but it works fine in normal managed mode).  To use bcm43xx, first add b43 to the blacklist.  Type:
```

sudo gedit /etc/modprobe.d/blacklist
```

A file will pop open.  Add to it these lines:
```

blacklist b43
blacklist b43legacy
blacklist ssb
```

and look for a line that says "blacklist bcm43xx."  Remove that line, then save and close the file.

Next you need to install the firmware for bcm43xx:
```

sudo apt-get install bcm43xx-fwcutter
```

You'll be asked if you want the firmware to be automatically downloaded; say yes.

Then reboot and see if your wireless is working better.

As a disclaimer, I'm not positive that bcm43xx will work for your card--it works for most models of Broadcom cards, but there are some exceptions, and unfortunately there's no reliable list of which ones are supported and which aren't.  So don't be shocked if after the reboot your wireless connection has disappeared entirely; this is ok.  In any case, it's simple to revert back to b43 if necessary simply by removing those three lines above from /etc/modprobe.d/blacklist.

If bcm43xx doesn't work, the next option is to use ndiswrapper, which should also give better signal strength.  But hopefully bcm43xx will just do it.

---

### Post by SlalomMan on 2008-07-29
I've got this same issue; I have a year-old Toshiba Satellite A205-S4617 with an Intel 4695 AG Card...my out puts are as follows:

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"strnkr"  Nickname:""
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:12:17:26:61:44   
          Bit Rate=36 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=57/100  Signal level=-72 dBm  Noise level=-94 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

lshw -C Network:
```
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:a0:d1:78:32:e4
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:1b:22:c7
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 ip=192.168.1.102 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g

```

iwlist scan:
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

```

Any help would be appreciated! I have a triple boot setup and this card runs much faster on both XP and Vista.

---

### Post by snkngshps on 2008-07-29
> **pytheas22 said:**
> Thanks for the information.  You're using b43, the "next-generation" driver for Broadcom wireless cards, which I've heard has some signal-strength issues.  You can try using bcm43xx, the older Broadcom driver, which is more reliable (and has fewer features, but it works fine in normal managed mode).  To use bcm43xx, first add b43 to the blacklist.  Type:
```

sudo gedit /etc/modprobe.d/blacklist
```

A file will pop open.  Add to it these lines:
```

blacklist b43
blacklist b43legacy
blacklist ssb
```

and look for a line that says "blacklist bcm43xx."  Remove that line, then save and close the file.

Next you need to install the firmware for bcm43xx:
```

sudo apt-get install bcm43xx-fwcutter
```

You'll be asked if you want the firmware to be automatically downloaded; say yes.

Then reboot and see if your wireless is working better.

As a disclaimer, I'm not positive that bcm43xx will work for your card--it works for most models of Broadcom cards, but there are some exceptions, and unfortunately there's no reliable list of which ones are supported and which aren't.  So don't be shocked if after the reboot your wireless connection has disappeared entirely; this is ok.  In any case, it's simple to revert back to b43 if necessary simply by removing those three lines above from /etc/modprobe.d/blacklist.

If bcm43xx doesn't work, the next option is to use ndiswrapper, which should also give better signal strength.  But hopefully bcm43xx will just do it.

Thanks for the response! Unfortunately (unless I did something wrong) it did completely disable my wireless. I took out the three added lines and added back in the one that was removed. How do I add ndiswrapper?

---

### Post by SlalomMan on 2008-07-29
I'm pretty sure you can find it in the repository...synaptic. Just search for "ndiswrapper." I'm not sure how to use it, but you have to find a windows driver for your wireless card first.

---

### Post by ModelM on 2008-07-30
I think your answer might be here:

```
joshua@SNKNGSHPS:~$ sudo iwlist scan
[sudo] password for joshua:
lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

wmaster0 Interface doesn't support scanning.

wlan0 Scan completed :
Cell 01 - Address: 00:0F:66B:17:BD
ESSID:"linksys"
Mode:Master
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=93/100 Signal level=-41 dBm Noise level=-70 dBm
Encryption keyff
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
Extra:tsf=00000013eefd5d26 
```

If you look at the line second from the bottom (bit rates) you'll see that the bit rates (speed) tops out at 11.

The top speed for 802.11b is 11, the top speed for 802.11g is 54.

It would appear that this is a 802.11b router or that 802.11g is turned off in the router.

---

### Post by snkngshps on 2008-07-30
> **ModelM said:**
> I think your answer might be here:

```
joshua@SNKNGSHPS:~$ sudo iwlist scan
[sudo] password for joshua:
lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

wmaster0 Interface doesn't support scanning.

wlan0 Scan completed :
Cell 01 - Address: 00:0F:66B:17:BD
ESSID:"linksys"
Mode:Master
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=93/100 Signal level=-41 dBm Noise level=-70 dBm
Encryption keyff
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
Extra:tsf=00000013eefd5d26 
```

If you look at the line second from the bottom (bit rates) you'll see that the bit rates (speed) tops out at 11.

The top speed for 802.11b is 11, the top speed for 802.11g is 54.

It would appear that this is a 802.11b router or that 802.11g is turned off in the router.

Is this something I can change in the router's settings or do I need to invest in a wireless-g router?

---

### Post by snkngshps on 2008-07-30
Nevermind, I read your post incorrectly. It is a B router (I've had it forever). I'll try to get a G router soon. Thanks for the help!

---

### Post by pytheas22 on 2008-07-30
> If you look at the line second from the bottom (bit rates) you'll see that the bit rates (speed) tops out at 11.

The top speed for 802.11b is 11, the top speed for 802.11g is 54.

It would appear that this is a 802.11b router or that 802.11g is turned off in the router.

Good suggestion, but even though transfer rates are capped at 11MB/s (which means download rates of about 1000kb/s), the user should still be seeing much higher download speeds than 40kb/s on the Internet.  The 11MB/s limit would really only become a constricting factor if you have an industrial-strength connection to the Internet (most normal residential services only provide up to 3 or 4MB/s, or ~400kb/s) or for transferring information on the internal LAN (e.g. from one computer in your house to another).  So I still suspect that signal strength is the issue here.
> 
Thanks for the response! Unfortunately (unless I did something wrong) it did completely disable my wireless. I took out the three added lines and added back in the one that was removed. How do I add ndiswrapper?

Sorry it didn't work (I sort of suspected that), but now we can try ndiswrapper.  There's a great (if a bit outdated) guide [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") to using ndiswrapper with Broadcom cards, including your chipset, bcm94311.  Unfortunately there are two different models of bcm94311 cards, and the steps that you need to follow are a little bit different depending on which model you have.  The output of:
```

lspci | grep -i 4311
```

would tell you which model you have--rev. 01 or rev. 02.

Once you figure it out, you can follow that guide, or if you prefer, let me know which rev. # you have and I'll write out steps for you (that guide can be a little confusing, and it was written for older versions of Ubuntu, adding to the confusion).

Remember (the guide may not mention this, since it was not written for Ubuntu 8.04) that in order for ndiswrapper to work, /etc/modprobe.d/blacklist needs to contain these four lines:
```

blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
```

Also remember that if you're using a 64-bit Linux kernel, the Windows drivers that you load into ndiswrapper need to also be 64-bit (I think the guide above doesn't mention this at all and just assumes that everyone is using 32-bit).  If you're on 64-bit, let me know.

---

### Post by snkngshps on 2008-07-30
Thanks, I'll try this before shelling out the money for a new router. If you have the time, and it won't be too much trouble, it would be awesome if you could give me the steps on what to do. I'm pretty comfortable with guides but I have had problems in the past following guides meant for older releases. Also note that I undid everything to the blacklist file that you had me do earlier (removed the three lines I added and added back in the line I deleted) so if I need to do that again let me know.

```
joshua@SNKNGSHPS:~$ lspci | grep -i 4311
05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

```

---

### Post by pytheas22 on 2008-07-30
> I've got this same issue; I have a year-old Toshiba Satellite A205-S4617 with an Intel 4695 AG Card...my out puts are as follows:

Your card has a completely different chipset, so none of this Broadcom/ndiswrapper stuff applies.

I don't know so much about Intel wireless, as I don't own any Intel cards myself, but I found this [thread]("http://ubuntuforums.org/showthread.php?p=4879282") where some people with the same card as you mention similar problems; this [bug report]("http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1623#c9") also seems related.  The solution is supposed to be to upgrade to the latest release of the driver.  So first of all, you should apply all Ubuntu updates and see if that fixes the problem--chances are that it will.

If not, follow these [instructions]("http://linuxwireless.org/en/users/Download") for compiling the latest wireless drivers from source.  If you need help, or if the problem persists even with the newer drivers installed, you may want to start a new thread (and let us know the URL) so that your problem doesn't get tangled up with the problem of the original poster here.

---

### Post by snkngshps on 2008-07-30
I also forgot to mention, I am running 32-bit and I just added
```
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
```

To the blacklist file.

---

### Post by pytheas22 on 2008-07-30
> If you have the time, and it won't be too much trouble, it would be awesome if you could give me the steps on what to do.

Sure, it's not a problem.  Since you've already dealt with the blacklist issue, you need to run just these commands to get it to work (these assume that you are plugged in to the Internet via ethernet; if that's impossible, let me know):
```

sudo apt-get install cabextract ndiswrapper*
wget ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe
cabextract sp34152.exe
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
```

If you get error messages at any point, please post them here.  Otherwise, at this point, you should see wireless networks listed when you click on the Network Manager icon.  If not, try rebooting and then run these commands:
```

sudo rmmod ndiswrapper
sudo rmmod ssb
sudo modprobe ndiswrapper
```

and wait a few seconds to see if networks become visible.

If you still don't have luck, please post the output of:
```

ndiswrapper -l
iwconfig
lshw -C Network
cat /etc/modprobe.d/blacklist
iwlist scan
```

---

### Post by snkngshps on 2008-07-30
Thanks so much for that! I'm at work at the moment, I have been connecting to my computer via remote desktop, but it is connected wirelessly at the moment so I won't be able to test this out until I get home and connect it by an ethernet cable. Thanks again!

---

### Post by snkngshps on 2008-07-30
I followed everything and there were no errors. I'm connected wirelessly right now and everything seems to be running smoothly. I haven't tried to do any heavy downloading or anything yet but hopefully this will clear it all up. Thanks for your help!! Do you think trying to eventually get a wireless-g router would still help the speed or would it be about the same on this driver for both routers?

---

### Post by pytheas22 on 2008-07-30
I'm glad you got it working.  Let me know if the download speeds are better (and if they're not, please post the output of "lshw -C Network" so that we can make sure that your system is indeed using ndiswrapper right now instead of b43).

I don't think that a wireless G router will make much of a difference for you.  Wireless range is a little better under the G protocol, but in terms of downloading stuff from the Internet, as I said in an earlier post, the maximum download speed available from your ISP is never going to be more than a fraction of what your router can transmit, even in B mode.  If you transfer large files between computers on your home LAN, then G mode would make the transfers much faster, but that's the only case where I can see it making a big difference.

Actually I had my home network accidentally operating under B mode for several months because I changed the setting to test something and forgot to change it back.  I only realized that I wasn't in G mode when I happened to notice it in the router configuration utility many months later.  In other words, for me, there was no perceivable difference between B and G modes.

Anyway G mode is becoming outdated now as N mode (which is a lot faster and has a much wider range) is being introduced; you may be better off holding out until N becomes widespread and routers that support it become cheaper, and then get one of them.

---

### Post by snkngshps on 2008-07-30
Well I haven't noticed it going any faster so I ran "lshw -C Network" and it looks like it's still using that old driver. I didn't notice any errors when following your instructions from earlier, but maybe I missed them?

```
joshua@SNKNGSHPS:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:87:6f:c9
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1b:fc:82:56:37
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.106 multicast=yes wireless=IEEE 802.11g

```

---

### Post by pytheas22 on 2008-07-30
hmmm, the lshw output is a bit strange; I'm not sure which driver it's using (it seems to think that you have two different wireless cards but I think it's due to confusion).  To figure out which device you're actually using, what does:
```

ifconfig
```

say?

Also, to double-check that b43 and friends are all blacklisted correctly, what does:
```

cat /etc/modprobe.d/blacklist
```

yield?

---

### Post by snkngshps on 2008-07-30
ifconfig:
```
joshua@SNKNGSHPS:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:23:87:6f:c9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4311 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2846 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5485169 (5.2 MB)  TX bytes:333680 (325.8 KB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4543 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4543 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:238540 (232.9 KB)  TX bytes:238540 (232.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:fc:82:56:37  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:fcff:fe82:5637/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:294594 errors:0 dropped:0 overruns:0 frame:0
          TX packets:292583 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:337000060 (321.3 MB)  TX bytes:33063359 (31.5 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-FC-82-56-37-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```


cat /etc/modprobe.d/blacklist:
```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx

```

---

### Post by pytheas22 on 2008-07-30
Strange...the blacklist looks fine, but b43 is still in control of that card.  Trying adding to /etc/modprobe.d/blacklist the line:
```

blacklist b43-pci-bridge
blacklist b43 ssb
```

then try these commands and see if it makes a difference:
```

sudo rmmod ndiswrapper
sudo rmmod b43
sudo rmmod b43legacy
sudo rmmod ssb
sudo rmmod b43 ssb
sudo modprobe ndiswrapper
```

after that, b43 should really not be in control anymore.  Does lshw mention ndiswrapper now?

The only thing I can think of is that something strange is going on because your ethernet card uses b44, the Broadcom ethernet driver, which is close to b43.  But that shouldn't matter; you should still be able to force the wireless to use ndiswrapper.  Nonetheless, maybe adding "blacklist b44" to the blacklist would make a difference--but note that it's going to break your ethernet; to get it back, you need to remove "blacklist b44" and run "sudo modprobe b44" to reload the b44 driver.

---

### Post by snkngshps on 2008-07-30
Ok I added those lines to the blacklist file but I had a few errors while running those commands. For the record, the wireless currently isn't working, I'm plugged in at the moment:

```
joshua@SNKNGSHPS:~$ sudo gedit /etc/modprobe.d/blaclist
[sudo] password for joshua: 
joshua@SNKNGSHPS:~$ sudo gedit /etc/modprobe.d/blacklist
joshua@SNKNGSHPS:~$ sudo rmmod ndiswrapper
joshua@SNKNGSHPS:~$ sudo rmmod b43
joshua@SNKNGSHPS:~$ sudo rmmod b43legacy
ERROR: Module b43legacy does not exist in /proc/modules
joshua@SNKNGSHPS:~$ sudo rmmod b43legacy
ERROR: Module b43legacy does not exist in /proc/modules
joshua@SNKNGSHPS:~$ sudo rmmod ssb
ERROR: Module ssb is in use by b44
joshua@SNKNGSHPS:~$ sudo rmmod b43 ssb
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module ssb is in use by b44
joshua@SNKNGSHPS:~$ sudo modprobe ndiswrapper

```

Here's the output of

---

### Post by snkngshps on 2008-07-30
I hit send prematurely. Here's the outpost of lshw (it's pretty nuts):
```
joshua@SNKNGSHPS:~$ lshw
WARNING: you should run this program as super-user.
snkngshps                 
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1898MiB
     *-cpu
          product: AMD Turion(tm) 64 X2 Mobile Technology TL-56
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 15.8.1
          size: 1800MHz
          capacity: 1800MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch ts fid vid ttp tm stc 100mhzsteps cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci:0
          description: Host bridge
          product: RS480 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 10
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: RS485 [Radeon Xpress 1100 IGP]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: vga_controller bus_master cap_list
                configuration: driver=fglrx_pci latency=255 mingnt=8 module=fglrx
        *-pci:1
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Network controller
                product: BCM94311MCG wlan mini-PCI
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=b43-pci-bridge latency=0 module=ssb
        *-storage
             description: SATA controller
             product: SB600 Non-Raid-5 SATA
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=64 module=ahci
        *-usb:0
             description: USB Controller
             product: SB600 USB (OHCI0)
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: SB600 USB (OHCI1)
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: SB600 USB (OHCI2)
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:3
             description: USB Controller
             product: SB600 USB (OHCI3)
             vendor: ATI Technologies Inc
             physical id: 13.3
             bus info: pci@0000:00:13.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:4
             description: USB Controller
             product: SB600 USB (OHCI4)
             vendor: ATI Technologies Inc
             physical id: 13.4
             bus info: pci@0000:00:13.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:5
             description: USB Controller
             product: SB600 USB Controller (EHCI)
             vendor: ATI Technologies Inc
             physical id: 13.5
             bus info: pci@0000:00:13.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 14
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide
             description: IDE interface
             product: SB600 IDE
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=pata_atiixp latency=64 module=pata_atiixp
        *-multimedia
             description: Audio device
             product: SBx00 Azalia
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=64 module=snd_hda_intel
        *-isa
             description: ISA bridge
             product: SB600 PCI to LPC Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
           *-network
                description: Ethernet interface
                product: BCM4401-B0 100Base-TX
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: eth0
                version: 02
                serial: 00:1c:23:87:6f:c9
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.108 latency=64 module=ssb multicast=yes
           *-system:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1
                bus info: pci@0000:08:01.0
                version: 19
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci latency=64 module=sdhci
           *-system:1 UNCLAIMED
                description: System peripheral
                product: R5C843 MMC Host Controller
                vendor: Ricoh Co Ltd
                physical id: 1.1
                bus info: pci@0000:08:01.1
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
joshua@SNKNGSHPS:~$ 


```

---

### Post by snkngshps on 2008-07-30
(I realize now I forgot to add on the filters for lshw)

---

### Post by pytheas22 on 2008-07-31
Thanks for the output.
> 
joshua@SNKNGSHPS:~$ sudo rmmod b43 ssb
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module ssb is in use by b44

From that I get the sense that, as I suggested above, the problem is that the system won't unload ssb (which is part of b43) because it's in use by b44, which is driving your ethernet.  So b43 (or its associates) is continuing to sort of drive the wireless card even though it's on the blacklist.  Does this help:
```

sudo rmmod b43
sudo rmmod b43legacy
sudo rmmod b44
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

(if you get errors about "module XXX does not exist in /proc/modules," that's good; it means that the module was not loaded to begin with, and we didn't want it to be)

After this b43, ssb and everything related to them should be disactivated, and ndiswrapper should be driving the card...if the command "lshw | grep ndiswrapper" returns anything, then that's good.  Those commands will kill your ethernet, but not permanently: either rebooting or running:
```

sudo modprobe b44
sudo modprobe ssb
sudo ifconfig eth0 up
```

should make the ethernet come back without a problem.

I won't be back till tomorrow, but please try those commands above and see if they help.  I'm sorry this is turning into such a complicated issue, but I think we're close to figuring it out.  Probably blacklisting b44 is going to be the solution.

---

### Post by snkngshps on 2008-07-31
No problem, I really appreciate your help! Ok I did everything, here's the output of all of it so you can see what had errors and what didn't. The wireless is back. I haven't rebooted to get the ethernet back but I will do that now.

```
joshua@SNKNGSHPS:~$ sudo rmmod b43
[sudo] password for joshua: 
ERROR: Module b43 does not exist in /proc/modules
joshua@SNKNGSHPS:~$ sudo rmmod b43legacy
ERROR: Module b43legacy does not exist in /proc/modules
joshua@SNKNGSHPS:~$ sudo rmmod b44
joshua@SNKNGSHPS:~$ sudo rmmod ssb
joshua@SNKNGSHPS:~$ sudo rmmod ndiswrapper
joshua@SNKNGSHPS:~$ sudo modprobe ndiswrapper
joshua@SNKNGSHPS:~$ lshw | grep ndiswrapper
WARNING: you should run this program as super-user.
                configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. ip=192.168.1.106 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11b

```

It's running on ndiswrapper, so that's good news!

---

### Post by snkngshps on 2008-07-31
I'm downloading a torrent right now that's going 120kbs and I'm connected from work via remote desktop with very little lag so it seems to be running much much better. Thanks for the help. Is there anything else I need to do?

---

### Post by snkngshps on 2008-07-31
Sorry for the triple post but I just ran into another snag. Like I said, I was connected via remote desktop and I needed to restart. I waited a few minutes and trying to remote back into it and it wasn't working. I had my room mate check and he said the wireless isn't working on it anymore.. :-/

---

### Post by pytheas22 on 2008-07-31
> I was connected via remote desktop and I needed to restart. I waited a few minutes and trying to remote back into it and it wasn't working. I had my room mate check and he said the wireless isn't working on it anymore.. :-/

That's ok; this is the behavior that is expected.  When you ran those commands that made ndiswrapper work, it was only a temporary fix that would last until the next reboot of your system.  So it makes sense that after a restart, the wireless is broken again.

To make the fix permanent (now that we know it works), you need to add:
```

blacklist b44
```

to /etc/modprobe.d/blacklist.  Then either reboot again or run these commands once:
```

sudo rmmod b44
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

and ndiswrapper should be in charge permanently, even after you reboot the computer.

Note that the downside to this is that your ethernet will be disabled so long as b44 is on the blacklist.  If you need to reenable the ethernet, you'll have to remove the "blacklist b44" line and run "sudo modprobe b44" to reinsert the b44 module, which will in turn break ndiswrapper.  I know this isn't ideal, but I don't know of a better solution; I guess you have to choose (remember, Linux is all about choice:)) between the ethernet and wireless.

If you have any more trouble please post, but I hope this ends up fixing your download speed issue to your satisfaction.

Also, you should note that the reason you had bad downloads speeds to begin with is that the b43 driver, which was originally driving your wireless interface before ndiswrapper, is still quite new and has some issues with certain kinds of cards.  By the next release of Ubuntu in October (or possibly even through system updates to Hardy), there's a good chance that those issues will be resolved and ndiswrapper will no longer be necessary.  So in the future, things should be much simpler.

---

### Post by snkngshps on 2008-07-31
Awesome, I'll run through that when I get home and I'll post again if there are any other problems. I really appreciate the help. I have one more favor to ask, if you don't mind helping me with it.

Will you give me a list of instructions if, in October I decide I want to check to see if the b43 driver is working any better? And then another set of instructions on how to revert back to ndiswrapper if it isn't working any better?

We tried a lot of things and I'm not 100% sure what all of them did so I don't want to mess anything up if I go to check if an updated b43 is working any better. I'll save that, along with the instructions on switching over to ethernet in a text file for future reference.

---

### Post by SlalomMan on 2008-07-31
> **pytheas22 said:**
> Your card has a completely different chipset, so none of this Broadcom/ndiswrapper stuff applies.

I don't know so much about Intel wireless, as I don't own any Intel cards myself, but I found this [thread]("http://ubuntuforums.org/showthread.php?p=4879282") where some people with the same card as you mention similar problems; this [bug report]("http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1623#c9") also seems related.  The solution is supposed to be to upgrade to the latest release of the driver.  So first of all, you should apply all Ubuntu updates and see if that fixes the problem--chances are that it will.

If not, follow these [instructions]("http://linuxwireless.org/en/users/Download") for compiling the latest wireless drivers from source.  If you need help, or if the problem persists even with the newer drivers installed, you may want to start a new thread (and let us know the URL) so that your problem doesn't get tangled up with the problem of the original poster here.

I followed the directions there;

downloaded compat-wireless from the site, ran "make" "sudo make install" "sudo make unload" and "sudo make load" and it broke my wireless...I'm assuming running "sudo make uninstall" will restore its functionality; i'm running off a wired connection right now. Any ideas? Should I try loading only the driver that I need?

---

### Post by snkngshps on 2008-07-31
Ok I have some bad news. I just got in from work. I did a reboot and the wireless wasn't working at all. I tried running those commands you have listed and now the ethernet isn't working either (luckily I have a spare computer). I imagine taking that line off of the blacklist would re-enable the wireless but wouldn't be controlled by ndiswrapper. What should I try now? :-/

---

### Post by SlalomMan on 2008-07-31
To everyone who's been helping me with my problem: I posted a new topic so I wouldn't clutter up this one with my issues...here it is:
[http://ubuntuforums.org/showthread.php?p=5498289#post5498289](http://ubuntuforums.org/showthread.php?p=5498289#post5498289)

---

### Post by pytheas22 on 2008-07-31
> Ok I have some bad news. I just got in from work. I did a reboot and the wireless wasn't working at all. I tried running those commands you have listed and now the ethernet isn't working either (luckily I have a spare computer). I imagine taking that line off of the blacklist would re-enable the wireless but wouldn't be controlled by ndiswrapper. What should I try now? :-/

Ahhh, sorry it's still not working the way it's supposed to.

First of all, does just:
```

sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

make the wireless come on (probably not, but it's worth a shot)?

If not, try removing "blacklist b44" from /etc/modprobe.d/blacklist, then reboot.  At that point you should have ethernet.  Then if you run:
```

sudo rmmod b44
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
```

the ethernet should go down but the wireless should be on (we'll be back to where we were last night, with the temporary fix).  At least let me know if this makes the wireless work till the next reboot.  If it does, we can find another solution to making the fix permanent without using the blacklist, since that apparently causes problems for b44.
> 
Will you give me a list of instructions if, in October I decide I want to check to see if the b43 driver is working any better? And then another set of instructions on how to revert back to ndiswrapper if it isn't working any better?

Sure, I'll be happy to do that once we know for sure what will make this work!

---

### Post by snkngshps on 2008-07-31
Ok, as you predicted that first fix didn't work but the second did. So wireless is working. Do you think maybe writing a script that just ran through those commands on start up would work, or is there a better fix?

---

### Post by pytheas22 on 2008-08-01
> Do you think maybe writing a script that just ran through those commands on start up would work

Yeah, that's exactly what I was thinking.  A startup script should make the wireless work and avoid whatever weird issue is going on with the blacklisting.

To write a script, type:
```

sudo gedit /etc/init.d/wifi-fix.sh
```

An empty text file will open.  Put in these lines:
```

#!/bin/bash
#this script unloads the b44 module at boot and reloads ndiswrapper; http://ubuntuforums.org/showthread.php?t=873944&page=4 for details

sudo rmmod b44
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
```

then save and close the file.  After that, run this command to make the system aware of the new script:
```

sudo update-rc.d /etc/init.d/wifi-fix.sh defaults
```

And then it should be run automatically whenever the machine boots.

Please confirm that this works, and also I'll get back to you later with instructions on what to do to see about using b43 in October.

---

### Post by snkngshps on 2008-08-01
I got an error message running the last line of code but I think I saw what it was doing and corrected it. Let me know if that looks like it updated properly.

```
joshua@SNKNGSHPS:~$ sudo update-rc.d /etc/init.d/wifi-fix.sh defaults
update-rc.d: /etc/init.d//etc/init.d/wifi-fix.sh: file does not exist
joshua@SNKNGSHPS:~$ sudo update-rc.d wifi-fix.sh
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults|multiuser [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force

```

---

### Post by pytheas22 on 2008-08-01
No, it looks like the system thinks that the file /etc/init.d/wifi-fix.sh doesn't exist.  Are you sure that you were able to save the script correctly after you wrote in gedit?  If so, there may have been some other kind of problem, or possibly the issue could have been that the script was not executable.  Maybe doing it like this would make a difference.  Run:
```

sudo -s
touch /etc/init.d/wifi-fix.sh
gedit /etc/init.d/wifi-fix.sh
```

Then paste in the contents of the script and save it.  Then run:
```

sudo chmod +x /etc/init.d/wifi-fix.sh
```

And finally:
```

sudo update-rc.d /etc/init.d/wifi-fix.sh defaults
```

Better luck?

---

### Post by snkngshps on 2008-08-01
Same error. When I did gedit, the information was already in there so the file was created correctly already. If you notice, in the error it says "**/etc/init.d/**/etc/init.d/wifi-fix.sh". It has "/etc/init.d" listed twice. So if you look at my last post, after getting that error I took "/etc/init.d/" off of the command because it seemed like it was looking there already and that's when I got something other than an error, but I wasn't quite sure if it was successful or not. Here's the full output of what happened this time.


```
joshua@SNKNGSHPS:~$ sudo -s
[sudo] password for joshua: 
root@SNKNGSHPS:~# touch /etc/init.d/wifi-fix.sh
root@SNKNGSHPS:~# gedit /etc/init.d/wifi-fix.sh
root@SNKNGSHPS:~# sudo chmod +x /etc/init.d/wifi-fix.sh
root@SNKNGSHPS:~# sudo update-rc.d /etc/init.d/wifi-fix.sh defaults
update-rc.d: /etc/init.d//etc/init.d/wifi-fix.sh: file does not exist

```

Is there a way to add it through the GUI System/Preferences/Sessions?

---

### Post by pytheas22 on 2008-08-01
Wow, this is being pretty crazy...it's like nothing on your machine will work the way it's supposed to.

Anyway, since we know the file definitely exists, try:
```

cd /etc/init.d
sudo update-rc.d wifi-fix.sh defaults
```

Maybe that will help because you won't be giving it the full path to the file.  It seems to me that there's some bug with update-rc.d that's making it interpret the command-line arguments incorrectly, which is why it's repeating '/etc/init.d.'

If it still doesn't work, you can update the init scripts by default--basically you just have to symlink some things together, which is all that update-rc.d does--but hopefully that won't be necessary, as it's tedious.

And no, unfortunately there's no GUI that I know of for writing boot scripts--although it would be a nice feature that would be trivially easy to write, I think.  Gnome has a GUI at System>Preferences>Sessions to run commands when you log into Gnome, which we could use to call the wifi-fix.sh script, but it would be a lot cleaner and better to have init deal with it.

---

### Post by snkngshps on 2008-08-01
Success!!

```
joshua@SNKNGSHPS:~$ cd /etc/init.d
joshua@SNKNGSHPS:/etc/init.d$ sudo update-rc.d wifi-fix.sh defaults
 Adding system startup for /etc/init.d/wifi-fix.sh ...
   /etc/rc0.d/K20wifi-fix.sh -> ../init.d/wifi-fix.sh
   /etc/rc1.d/K20wifi-fix.sh -> ../init.d/wifi-fix.sh
   /etc/rc6.d/K20wifi-fix.sh -> ../init.d/wifi-fix.sh
   /etc/rc2.d/S20wifi-fix.sh -> ../init.d/wifi-fix.sh
   /etc/rc3.d/S20wifi-fix.sh -> ../init.d/wifi-fix.sh
   /etc/rc4.d/S20wifi-fix.sh -> ../init.d/wifi-fix.sh
   /etc/rc5.d/S20wifi-fix.sh -> ../init.d/wifi-fix.sh

```

It looks like it worked. Now I guess the only things that would be helpful would be..
1. A guide to switching over to ethernet in case I ever need it.
2. A guide to checking on that new driver in October.
3. A guide for switching back to ndiswrapper in case the updated driver doesn't work any better.

By the way, I reached speeds slightly over 400 earlier, so it's definitely working much better. I appreciate all your help, without people like you Ubuntu would be a pain in the neck sometimes.

---

### Post by pytheas22 on 2008-08-02
Alright, I'm glad it's finally all straightened out now.

To switch back to ethernet, run these commands (which modify the wifi-fix script as needed, remove the modules 'ssb' and 'b44' from the blacklist, and insert those modules):
```

sudo -s
sed 's/rmmod b44/#line1/' /etc/init.d/wifi-fix.sh #deletes 'rmmod b44' from wifi-fix.sh (and replaces it with a comment) so that b44 is no longer unloaded at boot
sed 's/rmmod ssb/#line2/' /etc/init.d/wifi-fix.sh #ditto for ssb
sed 's/blacklist ssb//' /etc/modprobe.d/blacklist
sed 's/blacklist b44//' /etc/modprobe.d/blacklist
modprobe b44
modprobe ssb
ifconfig eth0 up
```

To switch from ndiswrapper to the native Broadcom driver, b43 (this will also enable your ethernet at the same time, which isn't necessary to make b43 work, but you may as well do it):
```

sudo -s
sed 's/rmmod b44/#line1/' /etc/init.d/wifi-fix.sh #deletes 'rmmod b44' from wifi-fix.sh (and replaces it with a comment) so that b44 is no longer unloaded at boot
sed 's/rmmod ssb/#line2/' /etc/init.d/wifi-fix.sh #ditto for ssb
sed 's/blacklist b44//' /etc/modprobe.d/blacklist
sed 's/blacklist b43 ssb//' /etc/modprobe.d/blacklist
sed 's/blacklist b43//' /etc/modprobe.d/blacklist
sed 's/blacklist b43legacy//' /etc/modprobe.d/blacklist
sed 's/blacklist ssb//' /etc/modprobe.d/blacklist
echo 'blacklist ndiswrapper' >> /etc/modprobe.d/blacklist
rmmod ndiswrapper
modprobe b44
modprobe b43
modprobe ssb
ifconfig wlan0 up
```

(these commands modify the wifi-fix script as needed, remove the modules 'b43,' 'ssb' and 'b43legacy' from the blacklist, add ndiswrapper to the blacklist, unload the ndiswrapper module, and load the b43 driver).
```

sudo rmmod b44
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
```

And to switch back to ndiswrapper if b43 doesn't work:
```

sudo -s
sed 's/#line1/rmmod b44' /etc/init.d/wifi-fix.sh #tells wifi-fix.sh to remove the b44 module, if it isn't already 
sed 's/#line2/rmmod ssb' /etc/init.d/wifi-fix.sh #same as above for ssb
echo 'blacklist b43' >> /etc/modprobe.d/blacklist
echo 'blacklist b43legacy' >> /etc/modprobe.d/blacklist
echo 'blacklist b43 ssb' >> /etc/modprobe.d/blacklist
echo 'blacklist ssb' >> /etc/modprobe.d/blacklist
echo 'blacklist b44' >> /etc/modprobe.d/blacklist
sed 's/blacklist ndiswrapper//' /etc/modprobe.d/blacklist
rmmod b43
rmmod b43legacy
rmmod b44
rmmod ssb
rmmod ndiswrapper
modprobe ndiswrapper
ifconfig wlan0 up
```

(this modifies the wifi-fix script as needed, adds 'b43,' 'b43legacy,' 'ssb' and 'b44' to the blacklist, removes ndiswrapper from the blacklist, unloads the b43 and b44 modules and their friends, then loads the ndiswrapper module)

Each of these scripts should apply the requested change permanently (through reboots), and each one should work no matter what the current state of the networking situation is on your machine.  There's a lot going on here and I could have missed something, but I proofread at least and think all these commands should work.  Also, I know that all of these commands may be cryptic to you, so if you want to know what exactly these scripts are doing, I'll explain.  But I wanted to write everything as a bash command (instead of giving you instructions like "open this file, find line X, replace it with Y, then scroll down to line Z...") so that you can run these things as scripts if you want, which should be convenient--just have three scripts, enable-ethernet.sh, enable-native-broadcom.sh and enable-ndiswrapper.sh, that you can run quickly whenever you want to switch.

Finally, keep in mind that the commands are all based on the way Hardy behaves; I can't guarantee that Ubuntu 8.10 won't deal with the Broadcom drivers in a different way and throw all of this off.  But feel free to contact me in October if you have any trouble.

---

### Post by snkngshps on 2008-08-02
Awesome, thanks so much. I've booted my machine a few times and haven't had any issues, so I guess we're officially done. Thanks again for all of your help!

---

