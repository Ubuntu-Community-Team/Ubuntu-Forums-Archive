---
title: "wireless network lost after short time"
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by happytechie on 2008-07-02
Hi All,

I'm seeing odd behavior from my wireless.  It works on bootup, continues to work for a while but after a period of time the connection is lost?  A reboot means it comes back and is available again but will still be lost after a period of time.

I've gone into the Edit wireless information window and it's all correct, the wireless net is available from my wife's laptop.

Any ideas or troubleshooting that I can do when it drops again?  I'm a technical person but very new to linux and ubuntu.

Default Hardy 8.0.4 install on a cheep PC-World laptop, I don't know what brand the wireless adapter is I'm afraid.

Thanks in advance for your help

---

### Post by happytechie on 2008-07-05
OK, so it seems to happen afterthe update manager has run and completed.

The settings below are unchanged after it's gone down, any ideas or other troubleshooting commands would be great:

paul@paul-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"electric fence"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:12:17:07:7C:7C   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=55/64  Signal level=39/65  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

paul@paul-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:19:21:a2:e1:64
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:15:af:0a:6e:5f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.100 multicast=yes wireless=IEEE 802.11g

---

### Post by happytechie on 2008-07-07
OK, It'sjust happened again and as far as I can tell there is nothing wrong with it except I can't get to the internet.  Can anyone suggest any other diagnostics that I can run when it goes down?  What confuses me is that it comes back after a re boot?

---

### Post by happytechie on 2008-07-14
OK I've tried all of the things that I can think of from reading the documentation but the problem clearly isn't that I need to install a new driver or change a config as it all works fine for a while.

There isn't a problem with my wireless (I'm posting this using it and my other laptop has no problems).

After a little while of use the connection just drops...  No change to the output from the network config type commands  If I right click the little network icon in the system bar it says that I am still connected BUT if I disable wireless and then re-enable wireless and I can re connect to the network just fine.

Has anybody got any suggestions before I just give up?

---

### Post by Loukisgr on 2008-07-14
why don't you change your router's wireless speed? From g make it b and try again.

---

### Post by happytechie on 2008-07-14
Thanks for the suggestion I'll try it later, why do you think this will make a difference?

---

### Post by happytechie on 2008-07-14
I don't seem to be able to connect to my wireless in B mode at all.  I've reset it back to mixed mode and I have some connectivity back again.  Any other sugestions?

I have WEP encryption turend on with a long alphanumeric pre shared key thing.  It's a linksys wireless router going to a cable modem that's a couple of years old.  All the other computers in the house are fine.

Any other suggestions?

---

