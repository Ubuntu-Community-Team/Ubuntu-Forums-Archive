---
title: "Wireless Problem"
date: 2007-03-25
forum: Networking &amp; Wireless
---

### Post by VitaliyNYC on 2007-03-25
Hello,

I just installed Ubuntu on one of my laptops (Sharp RD20), got Automatix and installed NetworkManager but my wireless card does not appear under it. Here is the card information for lspci ```
00:0a.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
```I am not sure what other information is needed but does anyone know how to get this card working?

Thanks.

EDIT: I followed the instructions posted at [http://www.ubuntuforums.org/showthread.php?t=288649](http://www.ubuntuforums.org/showthread.php?t=288649) and the card appears in iwconfig but it still does not work with NetworkManager.

---

### Post by chili555 on 2007-03-25
Please check here: [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager) .I was especially drawn to: > Any already configured devices that you want to be available in Network Manager will need to de-configured, as otherwise they will be ignored.

The easiest way to do this is by going to System -> Administration -> Networking and then going to "Properties" of each connection. In Properties, just untick the "Enable this connection" checkbox. Logout then log back in again. These connections should now be available in Network Manager.

OR, the harder way, is to backup and then edit the /etc/network/interfaces file to remove the configuration of these devices (except for lo which is needed for the loopback interface). You will have to save the file and reboot for the changes to take effect (or don't reboot and run /etc/init.d/networking restart instead). For example, if you wanted Network Manager to be able to control all of your devices, your /etc/network/interfaces file would look somewhat like the following:```

auto lo
iface lo inet loopback
```
Please post back and let us know.

---

### Post by VitaliyNYC on 2007-03-26
I have tried both ways just now without any success.

I opened System -> Administration -> Networking and disabled all connections, I logged out, and logged back in. Same issue.

I then edited /etc/network/interfaces, removed all the devices but lo, and rebooted. Same issue.

```
vitaliy@sharp:~$ sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:40:D0:3D:D2:AF  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:d0ff:fe3d:d2af/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:327 errors:0 dropped:0 overruns:0 frame:0
          TX packets:335 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:263397 (257.2 KiB)  TX bytes:52350 (51.1 KiB)
          Interrupt:11 Base address:0xe400 

eth2      Link encap:Ethernet  HWaddr 00:02:8A:9E:5D:C4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Memory:a0000000-a0000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:41 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2527 (2.4 KiB)  TX bytes:2527 (2.4 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vitaliy@sharp:~$ sudo iwconfig
lo        no wireless extensions.

eth2      IEEE 802.11b  ESSID:""  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity:1/3  
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/92  Signal level=-68 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.
```

---

### Post by chili555 on 2007-03-26
Your card is clearly working, but will not get an IP address with the wired connection attached, which it obviously is:```
eth0      Link encap:Ethernet  HWaddr 00:40:D0:3D:D2:AF  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
```Please disconnect the wire from the ethernet jack, issue a command:```
sudo ifconfig eth0 down
```And then go into NetworkManager and see if you don't connect with your wireless.

Sometimes, these cards load too many drivers and they fight for control. If your card still won't come up, issue another command:```
lsmod | grep prism
```If an entry comes back, we'll need to blacklist the offender. sudo gedit /etc/modprobe.d/blacklist to add the following:```
blacklist prism2_xyz
```Save and close gedit. Substitute the module you found, such as prism2_cs or prism2_pci and leave off the .ko extension. You may have to reboot.

---

### Post by VitaliyNYC on 2007-03-28
I disconnected the wired connection and still nothing. After doing lsmod I found that it was loading prism2_pci and I have added it to /etc/modprobe.d/blacklist. I rebooted and still nothing.

---

