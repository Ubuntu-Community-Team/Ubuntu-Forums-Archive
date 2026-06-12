---
title: "Jumbo Frames - How To ?"
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by drsox1899 on 2008-05-12
I've looked through the forums and I can find no clear How-To about setting Jumbo frames.  I'm running 7.10 at the moment.

Here's what I know about this :

1. I have had a look at ifconfig -a, which tells me what my two NIC cards are set to.  

One (eth0) is a USRobotics 7902 and is not used in Ubuntu (it's used in my WinXp partition and can't phone home due to an IP ban from my router).
It's trying to get a DHCP address in Ubuntu and it being refused by my router. 

The other (eth2) is used in Ubuntu and is a Realtek 8169 Gigabit NIC that I have tried unsuccessfully to set to a MTU of 7000. (Max setting for this chip is 7422).

2. I have set the MTU to 7000 but it doesn't stick !

I am trying to set a standard MTU setting across my network of 7000 for all devices but mainly to allow fast access to my Infrant ReadyNAS RAID boxes that can go up to a MTU of 9000.

What should I be doing to get a permanent MTU and (if not covered by just the MTU setting) enable Jumbo Frames (and disable to see the benefit)

Here's my ifconfig - file :

eth0      Link encap:Ethernet  HWaddr 00:14:C1:32:28:39  
          inet6 addr: fe80::214:c1ff:fe32:2839/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:43 errors:0 dropped:0 overruns:0 frame:0
          TX packets:75 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5683 (5.5 KB)  TX bytes:12318 (12.0 KB)
          Interrupt:20 Base address:0x2800 

eth2      Link encap:Ethernet  HWaddr 00:1D:0F:BE:11:42  
          inet addr:192.168.123.30  Bcast:192.168.123.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:fff:febe:1142/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2194 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1855 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2065060 (1.9 MB)  TX bytes:310740 (303.4 KB)
          Interrupt:19 Base address:0xc00 

eth0:avah Link encap:Ethernet  HWaddr 00:14:C1:32:28:39  
          inet addr:169.254.2.120  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:20 Base address:0x2800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4950 (4.8 KB)  TX bytes:4950 (4.8 KB)


Thanks

---

### Post by drsox1899 on 2008-05-13
Repeat

---

### Post by njparton on 2008-05-13
Just add mtu 9000 to the appropriate section of your /etc/network/interfaces file.
 
Replace the 9000 with whatever framesize you're tying to set.
 
That's mtu not MTU :wink:
 
Restart networking or reboot.

---

### Post by drsox1899 on 2008-05-13
> **njparton said:**
> Just add mtu 9000 to the appropriate section of your /etc/network/interfaces file.
 
Replace the 9000 with whatever framesize you're tying to set.
 
That's mtu not MTU :wink:
 
Restart networking or reboot.


Thanks.

FYI here's a copy of my /etc/network/interfaces file - pretty sparse I'd say.  What's missing ????


Quote " ....


auto lo
iface lo inet loopback







iface eth0 inet dhcp
netmask 255.255.255.0
gateway 192.168.123.250

auto eth0


....  """" Unquote

Regards

---

### Post by njparton on 2008-05-13
That is sparse if you have more than one nic?
 
Here's how you specify the mtu:
 
[B]auto lo
iface lo inet loopback

iface eth0 inet dhcp
netmask 255.255.255.0
gateway 192.168.123.250
[COLOR=red]mtu 9000[/COLOR]
auto eth0[/B]

---

### Post by drsox1899 on 2008-05-13
> **njparton said:**
> That is sparse if you have more than one nic?
 
Here's how you specify the mtu:
 
[B]auto lo
iface lo inet loopback

iface eth0 inet dhcp
netmask 255.255.255.0
gateway 192.168.123.250
[COLOR=red]mtu 9000[/COLOR]
auto eth0[/B]

Thanks.

Actually eth0 is the one I don't want to use in Ubuntu (used in WinXP).  eth2 is the one for Ubuntu.  
SO am I correct if I leave the eth0 alone and add the following for eth2 (mtu for the Realtek is limited to 7000) so that the whole file now looks like :

Quote """  ...

auto lo
iface lo inet loopback

iface eth0 inet dhcp
netmask 255.255.255.0
gateway 192.168.123.250
auto eth0

iface eth2 inet dhcp
netmask 255.255.255.0
gateway 192.168.123.250
mtu 7000
auto eth2

....   """"  Unquote


What should I change if I wanted to disable eth0 ?

---

### Post by njparton on 2008-05-13
Don't add the eth2 section if it's not there by default, it will screw everything up.

I did this in hardy and everything went haywire and I had to reinstall.

I currently don't have any ethX settings in my interface file at all and I can't work out why.

---

### Post by drsox1899 on 2008-05-13
> **njparton said:**
> Don't add the eth2 section if it's not there by default, it will screw everything up.

I did this in hardy and everything went haywire and I had to reinstall.

I currently don't have any ethX settings in my interface file at all and I can't work out why.

Thanks.  I only did what you suggested, rebooted and, according to my ifconfig -a file, the mtu's for eth0 and eth2 are still set to 1500 !

---

### Post by clarknova on 2008-10-05
If Network Manager is managing your connections and roaming mode is enabled, then those interfaces won't appear in /etc/network/interfaces.

I'm not aware of any way to change your mtu via network manager. So click on your network status icon and choose "manual configuration". Set a static IP for the interface in question and then close the dialog box. Now you should see an entry for your interface in /etc/network/interfaces and you can set your mtu.

I've read that your mtu setting won't work if you're using dhcp, but I've never tried. If it gives you trouble, try setting a static IP on the interface that you want jumbo frames on.

db

---

### Post by cariboo on 2008-10-05
You can also use ethtool to set the mtu of your network card. Ethtool is available in the repositories.

There is nothing wrong with your /etc/network/interfaces file except for the eth1 entry.

Here's mine: :)

```
auto lo
iface lo inet loopback
```

I'm running the Intrepid beta.

Jim

---

### Post by BrainwreckedTech on 2009-05-20
If you're looking to keep DHCP in /etc/network/interfaces, add the line ```
pre-up /sbin/ifconfig $IFACE mtu {size}
``` instead of just ```
mtu {size}
``` in the appropriate section of the file.

Taken from [http://ubuntuforums.org/showthread.php?t=3985](http://ubuntuforums.org/showthread.php?t=3985)

Jim, I don't know what your fascination is with ethtool in this thread and [here]("http://ubuntuforums.org/showthread.php?t=972612"), but could you tell us how to use it to set the MTU?  The man pages aren't very human-readable.

---

