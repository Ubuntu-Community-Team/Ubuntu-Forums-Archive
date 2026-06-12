---
title: "3945ABG Wireless, Ubuntu doesnt find my card!"
date: 2006-11-15
forum: Networking &amp; Wireless
---

### Post by neobonzi on 2006-11-15
I'm on edgy right now and have been struggling with my wireless card for days.

When i look in my device manager - under 82801G(ICH7 Family) PCI Express Port 1 i see my wireless card listed as PRO/Wireless 3945ABG Network Connection.

I installed the linux driver from sourceforge (used [http://ipw3945.sourceforge.net/INSTALL](http://ipw3945.sourceforge.net/INSTALL) step by step) but when i type in ./load debug=0 to see if its running i get this message:

```
neobonzi@neobonzi-laptop:~/Desktop/wireless/ipw3945-1.1.2$ sudo ./load debug=0
No modules unloaded.
insmod: error inserting './ipw3945.ko': -1 Unknown symbol in module
Load failed.
ipw3945d - regulatory daemon
Copyright (C) 2005-2006 Intel Corporation. All rights reserved.
version: 1.7.22
2006-11-15 14:38:11: ERROR: Could not find Intel PRO/Wireless 3945ABG Network Connection
..done.
neobonzi@neobonzi-laptop:~/Desktop/wireless/ipw3945-1.1.2$ 
```

How do i get edgy ubuntu to match the wireless card It obviously detects in the device manager with the driver i installed? Thanks for the help in advance!

-James

---

### Post by hasplu on 2006-11-21
I have the same problem on my BENQ R55! I've been struggling from 2 weeks and I can't find a solution! Since I was on drapper, everything was OK, but on edgy can't load my wireless 3945!

dmesg reports the following:  

[17179586.928000] ipw3945: disagrees about version of symbol ieee80211_wx_get_encodeext
[17179586.928000] ipw3945: Unknown symbol ieee80211_wx_get_encodeext
[17179586.928000] ipw3945: disagrees about version of symbol ieee80211_wx_set_encode
[17179586.928000] ipw3945: Unknown symbol ieee80211_wx_set_encode
[17179586.928000] ipw3945: disagrees about version of symbol ieee80211_wx_get_encode
[17179586.928000] ipw3945: Unknown symbol ieee80211_wx_get_encode
[17179586.928000] ipw3945: disagrees about version of symbol ieee80211_txb_free
[17179586.928000] ipw3945: Unknown symbol ieee80211_txb_free
[17179586.928000] ipw3945: disagrees about version of symbol ieee80211_wx_set_encodeext
[17179586.928000] ipw3945: Unknown symbol ieee80211_wx_set_encodeext
[17179586.932000] ipw3945: disagrees about version of symbol ieee80211_wx_get_scan
[17179586.932000] ipw3945: Unknown symbol ieee80211_wx_get_scan
[17179586.932000] ipw3945: disagrees about version of symbol ieee80211_freq_to_channel
[17179586.932000] ipw3945: Unknown symbol ieee80211_freq_to_channel
[17179586.932000] ipw3945: disagrees about version of symbol ieee80211_set_geo
[17179586.932000] ipw3945: Unknown symbol ieee80211_set_geo
[17179586.932000] ipw3945: disagrees about version of symbol ieee80211_rx
[17179586.932000] ipw3945: Unknown symbol ieee80211_rx
[17179586.932000] ipw3945: disagrees about version of symbol ieee80211_get_channel
[17179586.932000] ipw3945: Unknown symbol ieee80211_get_channel
[17179586.932000] ipw3945: disagrees about version of symbol ieee80211_channel_to_index
[17179586.932000] ipw3945: Unknown symbol ieee80211_channel_to_index
[17179586.932000] ipw3945: disagrees about version of symbol ieee80211_rx_mgt
[17179586.932000] ipw3945: Unknown symbol ieee80211_rx_mgt
[17179586.932000] ipw3945: disagrees about version of symbol ieee80211_get_geo
[17179586.932000] ipw3945: Unknown symbol ieee80211_get_geo
[17179586.932000] ipw3945: disagrees about version of symbol free_ieee80211
[17179586.932000] ipw3945: Unknown symbol free_ieee80211
[17179586.932000] ipw3945: disagrees about version of symbol ieee80211_tx_frame
[17179586.932000] ipw3945: Unknown symbol ieee80211_tx_frame
[17179586.932000] ipw3945: disagrees about version of symbol ieee80211_is_valid_channel
[17179586.932000] ipw3945: Unknown symbol ieee80211_is_valid_channel
[17179586.932000] ipw3945: disagrees about version of symbol ieee80211_get_channel_flags
[17179586.932000] ipw3945: Unknown symbol ieee80211_get_channel_flags
[17179586.932000] ipw3945: disagrees about version of symbol alloc_ieee80211
[17179586.932000] ipw3945: Unknown symbol alloc_ieee80211

In my network manager there is no eth0, but eth1 is presented by Wired connection (my Ethernet adapter)

ifconfig shows the following:

hasplu@hasplu:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:16:36:5A:10:5B  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe5a:105b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10756 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10563 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7207070 (6.8 MiB)  TX bytes:1822300 (1.7 MiB)
          Interrupt:185 

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:192.168.68.1  Bcast:192.168.68.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:192.168.217.1  Bcast:192.168.217.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)





I tried everything posted in [http://www.ubuntuforums.org/showthread.php?t=140085](http://www.ubuntuforums.org/showthread.php?t=140085) but can't find a solution!!!

Please, help, getting desperate!!!!!!

---

### Post by ktrauberman on 2006-11-21
I too, am having a similar problem.  I installed network-manager-gnome, and the applet doesn't even detect that I have a wireless card.  I'm running ubuntu on my IBM T60p (2007-93U).

Any suggestions?

---

### Post by hasplu on 2006-11-24
Anybudy? help on my case? Please.....:)

---

### Post by clydegoffe on 2006-11-24
I'm not sure whether or not this will help but the way I got mine working was by renaming /sbin/ipw3945d-2.6.17-10-generic to ipw3945d-2.6.17-10-server

The ipw3945 drives should automatically be installed with 6.10 edgy but if you're using the server version then you need to change that file name to match the name of your kernel release.

For example if you type "uname -r" at the command prompt what's outputted is the name of your kernel release.  The name of my kernel release is 2.6.17-10-server and that's what I renamed the file to match.  I then installed network manager by doing a "apt-get install network-manager-gnome".

Doing this worked for me.  I hope this helps.

Clyde

---

### Post by hasplu on 2006-11-25
Thanks Clyde, but the problem still exists:(
I tried everything, now I'm using evan a 2.6.18-2 custom, but can't load the wireless. The network manager can't find the ipw3945, but the most interesting thing is, that i delited all the information in /etc/networking/interfaces leaving it empty and still have wired network after the reboot. It seems senceless, but I think somehow the network manager does't refer to the networking interfaces at all.........

anyone any idea please?

thanks in advance

---

### Post by suoko on 2006-11-27
I have problems with that card too although different problems.

The card is correctly recognized in network-admin but unfortunately it doesn't show any network.
However if I manually insert the name of my wireless network everything works correctly.

Odd thing: the command "iwconfig scanning eth1" shows wireless networks !! it's a network-admin problem I guess.(I have this problem with an USB wireless adapter as well)

second problem: if I encrypt my network I can't connect to it anymore

---

### Post by dbott67 on 2006-11-29
@hasplu:

I do not have any experience with the 3945ABG, but it looks like many are experiencing this problem.

It appears [this thread]("http://www.ubuntuforums.org/showthread.php?p=1673142") has worked for a few people.

Can you post the output of:
```
route -n
```
```
ifconfig -a
```
```
cat /etc/network/interfaces
```
```
iwlist scanning
```
```
sudo lshw -C network
```

If all else fails, you could always try ndiswrapper.

**_Sidenote:_**

When troubleshooting wireless problems, WEP, WPA and other security mechanisms can add a layer of complexity that can make it difficult to determine exactly where the problem lies.  Normally, I recommend disabling encryption to eliminate WEP (or WPA) as the problem.  Disable it on the router & remove the 'wireless-key' line from /etc/network/interfaces and try to connect.  If you are able to connect, then we can focus on WEP.

**_Re-enabling WEP:_**

If you are able to connect without WEP, try turning it back on in the router and use 128-bit encryption with a simple 13-character password (such as 'wepencryption')

In your **/etc/network/interfaces** try changing the line to:

```
wireless-key s:wepencryption
```
The preceding 's:' indicates that the key is in plain ASCII text & should be 13 characters long (assuming you're using 128-bit).

'sudo ifdown wlan0', 'sudo ifup wlan0', 'sudo dhclient wlan0' and see what happens.

If it works, then change the WEP key to something more difficult and repeat the above steps.

---

### Post by hasplu on 2006-11-29
Thank you very much for the reply:)
here are the posts:
```

hasplu@hasplu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.68.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.217.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1


```



```
hasplu@hasplu:~$ ifconfig -a
eth1      Link encap:Ethernet  HWaddr 00:16:36:5A:10:5B  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe5a:105b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7093 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7197 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7311514 (6.9 MiB)  TX bytes:1246569 (1.1 MiB)
          Interrupt:185 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:232 errors:0 dropped:0 overruns:0 frame:0
          TX packets:232 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21126 (20.6 KiB)  TX bytes:21126 (20.6 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:192.168.68.1  Bcast:192.168.68.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:192.168.217.1  Bcast:192.168.217.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b
```)


about the network interfaces I have to admit, that I manually add all the info in the file.....just for the experiment. But even if there is no text in it, the wired Ethernet still works...


```
hasplu@hasplu:~$ cat /etc/network/interfaces
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
wireless-mode managed
wireless-key1 abcdef0123456789
wireless-defaultkey 1
wireless-keymode open
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid any    
wireless-mode managed
wireless-key1 abcdef0123456789
wireless-defaultkey 1
wireless-keymode open
```


```
hasplu@hasplu:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

vmnet8    Interface doesn't support scanning.

vmnet1    Interface doesn't support scanning.

```

```

hasplu@hasplu:~$ sudo lshw -C network
Password:
  *-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945
       resources: iomemory:d8000000-d8000fff irq:169
  *-network
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@04:00.0
       logical name: eth1
       version: 10
       serial: 00:16:36:5a:10:5b
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=sky2 driverversion=1.6.1 duplex=full firmware=N/A ip=192.168.1.2 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:da000000-da003fff ioport:4000-40ff irq:58

```





About the WEP, I'm trying to connect to an unsecure router!!!



> If all else fails, you could always try ndiswrapper.


I tryed ndiswrapper - still no rezult:(


```
hasplu@hasplu:~$ ndiswrapper -l
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_BG:",
        LC_ALL = (unset),
        LANG = "en_US.ISO-8859-15"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Installed drivers:
netw39x5                driver installed, hardware present 
```





take a look at this:
```
hasplu@hasplu:~$ dmesg | grep ipw3945
[17179588.492000] ipw3945: no version for "ieee80211_wx_get_encodeext" found: kernel tainted.
[17179588.496000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.1.0d
[17179588.496000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[17179588.536000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[17179589.412000] ipw3945: Radio Frequency Kill Switch is On:

```


the geography of the card is not recognized! 

and the kill switch is on, but I can find no way to turn it off....



Thank you very much again for your reply:)))

best regards:
hasplu

---

### Post by dbott67 on 2006-11-29
I think post # 12 of this thread may be the answer:
[http://www.ubuntuforums.org/showthread.php?t=286188&page=2&highlight=intel+3945](http://www.ubuntuforums.org/showthread.php?t=286188&page=2&highlight=intel+3945)
(reference from [here]("http://kubuntuforums.net/forums/index.php?topic=10787.msg42733"))

-Dave

-Dave

---

