---
title: "Cannot get D-link WNA-2330 to work"
date: 2007-03-27
forum: Networking &amp; Wireless
---

### Post by UberIcarus on 2007-03-27
okay, so I upgraded to feisty....which was a nightmare in itself, but everything's running. Since this laptop has a built in broadcomm that breaks every upgrade, I figured I'd finally go down, and buy a card that worked well. So I went and bought a WNA-2330, which supposedly works "out of the box".


Not only does it not work out of the box, but I had to install linux-restricted-modules, and it still doesn't work. It does some of the strangest nonsense instead:

Here's my output from ifconfig:

jackfrost@jackfrost-laptop:~$ sudo nano /etc/network/interfaces
jackfrost@jackfrost-laptop:~$ sudo ifconfig
ath0      Link encap:Ethernet  HWaddr 00:15:E9:74:34:A1  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

ath0:avah Link encap:Ethernet  HWaddr 00:15:E9:74:34:A1  
          inet addr:169.254.7.57  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:C0:9F:5B:6A:6B  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fe5b:6a6b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1633 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1562 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:996338 (972.9 KiB)  TX bytes:175970 (171.8 KiB)
          Interrupt:10 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:168 (168.0 b)  TX bytes:168 (168.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-15-E9-74-34-A1-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:256 errors:0 dropped:0 overruns:0 frame:24946
          TX packets:753 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:21266 (20.7 KiB)  TX bytes:35368 (34.5 KiB)
          Interrupt:11 

okay, see that ath0:avah and wifi0? well ath0:avah appears if you monkey around with ath0 with iwconfig. It'll let you do whatever you'd like with iwconfig, except change the bitrate to anything but 1mb/s. and dhclient wont work naturally. the ath0:avah then appears, and you cannot ifup nor ifdown either ath0 nor ath0:avah.

wifi0 is completely a mistery, it's obviously doing something, but running iwconfig on it gives: no wireless extensions.

using network-admin on the ath0 device, drops me off the ethernet device (eth0) tries to log in with ath0, fails, then plugs me back in with eth0.

I seriously am at my wits end, I just want a working wireless card.

---

### Post by chili555 on 2007-03-27
Feisty, by default, installs NetworkManager. This is from [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager) > The computer should use the wired network connection when its plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has has been managed for them; they should simply see uninterrupted network connectivity.So, as long as the ethernet cable is plugged in, NM will ignore your wireless and give you a connection on eth0. Looks like it's working!```
eth0 Link encap:Ethernet HWaddr 00:C0:9F:5B:6A:6B
inet addr:192.168.1.105 Bcast:192.168.1.255 Mask:255.255.255.0
```Try disconnecting the ethernet cable and see if your wireless comes to life.

---

### Post by UberIcarus on 2007-03-27
No, it doesn't work if I shutdown eth0 either. in nm-applet it shows ath0:avahi, but doesn't know what to do with it. If I manually change it to ath0, it'll show the signal bar for my wireless connection, but will not connect.

If I run dhclient, the first thing I get is: wifi0 protocol not recognized 801 (paraphrasing)

It appears to be directing all traffic through wifi0, indeed if I use 

ifconfig wifi0 down, and also bring down ath0:avahi,  then it tells me that the network for ath0 is down.

So  as of right now the card neither works through nm-applet, nor command line, nor network-admin.

---

### Post by UberIcarus on 2007-03-27
bump

---

### Post by UberIcarus on 2007-03-28
Still not working after updating the avahi-daemon and such today, submitted a bug to launchpad as well: [https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/97685](https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/97685)

---

