---
title: "[SOLVED] Realtek 8139 Broken in Gutsy?"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by Roturgo on 2007-10-19
**_The Problem_**
I upgraded to Gutsy (clean install) and my Realtek 8139 PCI NIC isn't being brought up.  The link lights are off and so obviously there's no network connectivity.

**_The Output_**
ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:40:F4:CB:F8:B7  
          inet6 addr: fe80::240:f4ff:fecb:f8b7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0xa000 

eth0:avah Link encap:Ethernet  HWaddr 00:40:F4:CB:F8:B7  
          inet addr:169.254.11.253  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:78 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6384 (6.2 KB)  TX bytes:6384 (6.2 KB)
```

ethtool eth0
```
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 32
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: d
        Current message level: 0x00000007 (7)
        Link detected: yes
```

lsmod | grep 8139
```
8139too                31232  0 
mii                     7424  1 8139too
```

lspci -v  (relevant portion)
```
01:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RT8139
        Flags: bus master, medium devsel, latency 32, IRQ 16
        I/O ports at de00 [size=256]
        Memory at feaff000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2
```

dmesg (relevant portion)
```
[   99.042316] NETDEV WATCHDOG: eth0: transmit timed out
[  100.706136] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[  100.706140] eth0: Tx queue start entry 4  dirty entry 0.
[  100.706143] eth0:  Tx descriptor 0 is 00082156. (queue head)
[  100.706146] eth0:  Tx descriptor 1 is 00082156.
[  100.706149] eth0:  Tx descriptor 2 is 00082156.
[  100.706151] eth0:  Tx descriptor 3 is 0008203c.
[  100.706159] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  104.741441] eth0: no IPv6 routers present
```

route -v
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
```

**_What I've Tried_**
I know this card works as it worked fine in Ubuntu 7.04, Slackware 12.0, and Windows (posting under Windows right now).

I've tried unloading and reloading the modules, tried bypassing my router altogether and plugging directly into the modem (unnecessary, but did it just for giggles).  I've also tried disabling ACPI as per similar posts, but still no dice.  I've tried bringing the interface down, bringing it back up, and running dhclient manually.  And finally I've tried setting a static IP, though I know this was useless as my link isn't up.

It seems to me that although Gutsy may be loading the module for the NIC, it isn't bringing the NIC up fully.  Anyone else experiencing these issues?

Also, I had this exact same issue when I was testing out openSUSE 10.3, which I believe is running roughly the same kernel version as Gutsy.  Could the RTL8139 driver be broken in this kernel, or is there something that I'm overlooking?

---

### Post by noob12 on 2007-10-19
It is odd that dmesg and ethtool are reporting the link detected.  Is this at the same time that the link light is off?  Is it also off on the router (other side of the cable)? 

Are you getting more instances of
```

NETDEV WATCHDOG: eth0: transmit timed out

```
when you ping?

If this is not an onboard device, check that the card is properly seated in the slot and check cables.

Were you using any boot flags when booting Feisty?

Check that you have wake-on-lan enabled on the Windows side ([http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)).

---

### Post by keithverona on 2007-10-20
This is a confirmation of this error by a relatively new Ubuntu 7.10 user. I get the same "NETDEV WATCHDOG: eth0: transmit timed out" message on a clean install of Ubuntu 7.10 in a PC also with a RealTek RTL-8139 PCI ethernet card. The ethernet card and the PC work just fine with XP. The Link light is off for some reason on the back of the ethernet card. Ubuntu Linux is working otherwise well.

There are other posting on other distributions that maybe the kernel version I have, and Ubuntu 7.10 installs with, (2.6.22-14 generic) has issues with this ethernet card. Can anyone suggest a solution?

---

### Post by RMU on 2007-10-20
Sounds like my problem as well with both 7.10 and opensuse 10.3. No problems in xp.

Seems like DHCP isn't working. No IP, no DNS, nada. I'm wired into a linksys wrt54g. 

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:11:2F:60:A3:4E  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0xcc00 

eth0:avah Link encap:Ethernet  HWaddr 00:11:2F:60:A3:4E  
          inet addr:169.254.5.162  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:20 Base address:0xcc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:163 errors:0 dropped:0 overruns:0 frame:0
          TX packets:163 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12749 (12.4 KB)  TX bytes:12749 (12.4 KB)

```

I'm clueless. Any other info I can provide that would help?

---

### Post by noob12 on 2007-10-20
You may all be experiencing different problems with similar symptoms.  Here are the things I would check.  If all of these fail, I would suggest that you file bug(s) on launchpad and provide them with details of your situation(s). 

(1) Check physical connectivity: cable, seating of the card in the slot.

(2) Check that you aren't a victim of the wake-on-lan issue described and solved here: **[http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)**

If you are seeing multiple repeated instances of watchdog timeout messages, each time you ping or try to reacquire an address, you may have pci routing or timing issues.  Try booting with the **pci=noacpi** boot option.

I'm attaching some generic instructions below for how to boot with boot options (flags).

**Instructions for one-time boot flag entry**

When booting you'll normally see grub flash a menu of boot options up for a little while.  While it is up  with the default selection highlighted, press **e**, then use arrow keys to navigate to the line that starts with **kernel** and hit **e** again to edit it.  Put the flags at the end of the line, separated from each other and from prior material on that line by space or spaces.  Hit Enter to accept, then b to boot.

To confirm you got the flags entered properly, you should see them if you type
```

dmesg | grep 'Kernel command line'

```
after you boot.

The flags will only apply to that one boot.

**Making the flags permanent**

To make flags permanent (apply to all boots), you need to edit the file **/boot/grub/menu.lst** and find the kernel line corresponding to the boot menu entry you are using and add the options there.  Note that there will typically be some kernel lines that are commented out (preceded by # signs).  You can ignore those.

I suggest that you do not edit this file until after trying boot flags using the one-time per-boot method and establishing that they work and solve an issue.

You will need to be root or use sudo to start your editor.  

**Be careful editing the file**, because editing errors may get you stuck in a situation where you can't boot.   In most situations, you can fix minor errors with a one-time edit for one boot as above.  In the worst case you would have to fix this by booting from the LiveCD, mounting the hard drive, and editing the file.

---

### Post by RMU on 2007-10-20
> **noob12 said:**
> You may all be experiencing different problems with similar symptoms.  Here are the things I would check.  If all of these fail, I would suggest that you file bug(s) on launchpad and provide them with details of your situation(s). 

(1) Check physical connectivity: cable, seating of the card in the slot.

(2) Check that you aren't a victim of the wake-on-lan issue described and solved here: **[http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)**

If you are seeing multiple repeated instances of watchdog timeout messages, each time you ping or try to reacquire an address, you may have pci routing or timing issues.  Try booting with the **pci=noacpi** boot option.

I'm attaching some generic instructions below for how to boot with boot options (flags).

**Instructions for one-time boot flag entry**

When booting you'll normally see grub flash a menu of boot options up for a little while.  While it is up  with the default selection highlighted, press **e**, then use arrow keys to navigate to the line that starts with **kernel** and hit **e** again to edit it.  Put the flags at the end of the line, separated from each other and from prior material on that line by space or spaces.  Hit Enter to accept, then b to boot.

To confirm you got the flags entered properly, you should see them if you type
```

dmesg | grep 'Kernel command line'

```
after you boot.

The flags will only apply to that one boot.

**Making the flags permanent**

To make flags permanent (apply to all boots), you need to edit the file **/boot/grub/menu.lst** and find the kernel line corresponding to the boot menu entry you are using and add the options there.  Note that there will typically be some kernel lines that are commented out (preceded by # signs).  You can ignore those.

I suggest that you do not edit this file until after trying boot flags using the one-time per-boot method and establishing that they work and solve an issue.

You will need to be root or use sudo to start your editor.  

**Be careful editing the file**, because editing errors may get you stuck in a situation where you can't boot.   In most situations, you can fix minor errors with a one-time edit for one boot as above.  In the worst case you would have to fix this by booting from the LiveCD, mounting the hard drive, and editing the file.

Looks like I am a wake-on-lan victim. Thanks noob12!

---

### Post by kes.eclipse on 2007-10-21
I had the same problem. The solution how I fixed that:
1. ```
rmmod 8139cp
```
2. ```
nano -w /etc/network/interfaces
```
Here add:
```
auto lo **eth0**
iface lo inet loopback

[B]iface eth0 inet static
                 address xxx.xxx.x.x
                 netmask xxx.xxx.xxx.x
                 gateway xxx.xxx.x.x[/B] #Where xxx.xxx.x.x are your settings of internet connection

```
3. ```
nano -w /etc/resolv.conf
```
Here add:
```

**nameserver xxx.xxx.xxx.x** #Where xxx.xxx.xxx.x is IP of your dns-server
**nameserver xxx.xxx.xxx.x** #Add this for each dns-server

```
4. ```
ifup -a
```

It works for me.
P.S. Sorry for my English. I think it's understandable anyway. :)

---

### Post by Roturgo on 2007-10-21
First off, thanks everyone for your help!  I appreciate all the feedback and suggestions!

Now, for a long story made short:  
I also was a (partial) victim to the Wake on Lan issue.

Longer version:
I did check and double check that everything on the hardware end was working fine - card seated properly, patch cable good, no dead ports on the router, etc.  But like I said, this card is currently working just fine with Windows, Slackware, and older versions of Ubuntu (I could boot up a Live CD of 7.04 or 6.10, etc. and networking works great.  It's only with the new version of Ubuntu and openSUSE that it doesn't function.

I tried the pci=noacpi boot flag as suggested, but that didn't work.  I then took a look at the Wake on Lan issue and once I enabled that in Windows, I finally was getting a link light when I booted up Ubuntu (on both ends of course).  I still wasn't able to pull down an address from DHCP, but desperately I set a static IP outside of my DHCP pool range, set up DNS in /etc/resolv.conf, and killed off dhclient.  Lo and behold, I have full connectivity!

Now the question I have...why have I never encountered this issue before?  How come distributions that ship with a kernel version prior to 2.6.22.x (or 2.6.21.3 per the WOL issue thread) work fine?  Was there a regression in the rtl8139too driver that made the kernel unable to wake the NIC out of its disabled state?  It worked fine previously.  I guess ultimately, how do we get this issue resolved so that others don't encounter this issue?  It seems to be above just Ubuntu -- it's at the kernel developer level.

---

### Post by skillshot on 2007-10-22
Hi all,

i have an old Notebook with a realtek 8139 onboard which worked fine up to Ubuntu 7.04. After the upgrade to 7.10 it stoped working. I tried all of the known fixes, dhcp, static, everything but i still can not use my network.

ethtool shows an active link but i cant connect to any ip/address, neither extern nor on my lan.

I could fix a similar issue on a desktop pc with the wake-on-lan workaround ... 

Are their any other "tricks" i could try?

Thx, SKillshot

---

### Post by Ehtetur on 2007-10-22
Just got my Realtek 8139 eth card working after having no network connection during **or** after installing Gutsy.
I knew the card itself wasn't the problem because I got on the network booting with Dapper live CD

I had to disable ipv6 in gutsy, just to be able to see my linksys WRT54GL router... Not a big since I'm happy w/ ipv4.
sudo vim /etc/modprobe.d/aliases
added the word off to this line: alias net-pf-10 ipv6
```
alias net-pf-10 off ipv6
```
Had me a working network connection after a reboot.... it worked fine 'til the next boot when again I had no network connectivity... :mad:
Everytime I disabled/enabled eth0, ifconfig would show eth0:avah

Finally, I took a look at System --> Preferences --> Sessions... Bluetooth Manger was enabled... my desktop doesn't have bluetooth so I disabled it.. 
After rebooting, I got on the network fine.

---

