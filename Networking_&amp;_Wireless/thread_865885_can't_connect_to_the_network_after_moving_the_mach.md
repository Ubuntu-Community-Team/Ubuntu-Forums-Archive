---
title: "can't connect to the network after moving the machine"
date: 2008-07-21
forum: Networking &amp; Wireless
---

### Post by henryfeifei on 2008-07-21
My computer is moved from 6th floor to the 5th floor

when it was on 6th, everything is OK

but after i move it to 5th floor. it can't connect to the network.

when i enter ifconfig, the results are:

eth0      Link encap:Ethernet  HWaddr 00:11:25:ED:B3:A4  
          inet6 addr: fe80::211:25ff:feed:b3a4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6614 errors:0 dropped:0 overruns:0 frame:0
          TX packets:594 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:640382 (625.3 KB)  TX bytes:57377 (56.0 KB)
          Base address:0x4000 Memory:d0080000-d00a0000 

eth0:avah Link encap:Ethernet  HWaddr 00:11:25:ED:B3:A4  
          inet addr:169.254.219.38  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Base address:0x4000 Memory:d0080000-d00a0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:165 errors:0 dropped:0 overruns:0 frame:0
          TX packets:165 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 


i know i don't get the proper ip address...
i examined the calbe and the network port several times and found them works ok,because my another computer with xp can use that port and cable to connect to the network.
so i'm totally confused now...i don't know the difference between 5th floor and 6th floor

my /ect/network/interface is :
auto lo
iface lo inet loopback

in the network manager i choose the wired connection and click the properties and choose enable roaming mode .(because the the other people can connect to the network by choosing this) but i cant .any one to help me.thanks a lot

---

### Post by henryfeifei on 2008-07-21
i'm a newer of linux.  Hope someone can give me some advice so i can have more confidence!

---

### Post by henryfeifei on 2008-07-21
if you want any more information .just told me what to do.

---

### Post by ELGL on 2008-07-21
it seems you aren't getting an ip address from a dhcp server. 

To start with you can try this,

```
sudo /etc/init.d/networking restart
```

This should make it request a new address.

If that doesn't work, edit your /etc/network/interfaces to look like this

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```
sudo /etc/init.d/networking restart
```

and try again. 

If it fails again, try these commands

```
sudo ifdown eth0
sudo ifup eth0
```

if that still fails, reboot your machine and check if it gets an address.

When even that doesn't work, if you have access to it, logon to the device or server giving out the addresses and manually remove the dhcp lease for your machine and then try all the above commands again.

---

### Post by superprash2003 on 2008-07-21
go to system->admin->network and set eth0 to DHCP.. and then reboot.. then type ifconfig and see if you are getting an ip.. if you still arent then try using Static ip

---

### Post by henryfeifei on 2008-07-21
to ELGL
thanks a lot for you answer!
the third step in your replay makes my computer can connect to the network again,that's great.

Though i still don't know the reasons, i feel happy. 

Thanks a lot

Wish you all the best!


to superprash2003

thanks for you replay too...you are so kind and wish you all the best too!

---

