---
title: "network issues"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by trinidadflores on 2009-08-07
I'm having the same type of problem here but mine is with my net work (both ethernet and wireless) it says tht my network adapters are disconnected. I did have it working and it works fine in windows. I did nothing to the setting but now my networking is totally disabled. how do i get this back. When it comes to networking with Ubuntu i am ignorent. I need help.

1) To tell if your wireless card is even recognized and working, the output of
Code:

sudo ifconfig

yes the card is working it is what I am using to connect to the network as we speak in windows. and it works fine when i run ubuntu off of the live disk.
2) If your wireless card is internal, the output of
Code:

lspci | grep Wireless

02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AGN [Kedron] Network Connection (rev 61)

Trinidad

---

### Post by trinidadflores on 2009-08-07
anyone with any clue as to how to fix this one??

---

### Post by trinidadflores on 2009-08-07
??????

---

### Post by trinidadflores on 2009-08-08
> **trinidadflores said:**
> I'm having the same type of problem here but mine is with my net work (both ethernet and wireless) it says tht my network adapters are disconnected. I did have it working and it works fine in windows. I did nothing to the setting but now my networking is totally disabled. how do i get this back. When it comes to networking with Ubuntu i am ignorent. I need help.

1) To tell if your wireless card is even recognized and working, the output of
Code:

sudo ifconfig

yes the card is working it is what I am using to connect to the network as we speak in windows. and it works fine when i run ubuntu off of the live disk.
2) If your wireless card is internal, the output of
Code:

lspci | grep Wireless

02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AGN [Kedron] Network Connection (rev 61)

does anyone possible know how to fix this one without reinstalling the os?

Trinidad

---

### Post by Iowan on 2009-08-08
[http://ubuntuforums.org/showpost.php?p=7750593&postcount=3]("http://ubuntuforums.org/showpost.php?p=7750593&postcount=3")

---

### Post by trinidadflores on 2009-08-08
> **Iowan said:**
> [http://ubuntuforums.org/showpost.php?p=7750593&postcount=3]("http://ubuntuforums.org/showpost.php?p=7750593&postcount=3")

Here is the read out of the following ifconfig -a, iwconfig, and lshw -C network done in this order.

Trinidad


trinidad@user:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1b:24:ae:e2:95  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:250 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1392 (1.3 KB)  TX bytes:1392 (1.3 KB)

pan0      Link encap:Ethernet  HWaddr 3e:61:08:a3:9f:08  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:e7:d4:c3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:13:e8:e7:d4:c3  
          inet addr:169.254.11.184  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-E7-D4-C3-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

trinidad@user:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

trinidad@user:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:e7:d4:c3
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:24:ae:e2:95
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 3e:61:08:a3:9f:08
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by trinidadflores on 2009-08-09
one thing i just noticed that when you go to the network applet it says that its not being monitored.

---

### Post by Iowan on 2009-08-09
What is in */etc/network/interfaces*? (Shouldn't be much)

---

### Post by trinidadflores on 2009-08-09
> **Iowan said:**
> What is in */etc/network/interfaces*? (Shouldn't be much)

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp

---

### Post by trinidadflores on 2009-08-10
does anyone have any ideas as to what could be done other than to reinstall?

---

### Post by trinidadflores on 2009-08-10
does anyone have any ideas as to what could be done other than to reinstall? that does not solve the main issue nor helps when this happens again to me or anyone else for that matter.

---

### Post by trinidadflores on 2009-08-10
SOLVED this problem via the IRC chat channel in a matter of minutes.

---

### Post by Iowan on 2009-08-10
Can you summarize the solution for the benefit of others with similar problems? :P

---

### Post by trinidadflores on 2009-08-11
In Terminal copy and paste this command this will open the text file in gedit you can use your favorite text editor jsut by replacing gedit 

```
sudo gedit /etc/network/interfaces
```
you should see
```

auto lo
iface lo inet loopback 
auto wlan0
iface wlan0 inet dhcp

```
replace the above with following line

```


auto lo
iface lo inet loopback 
#auto wlan0
#iface wlan0 inet dhcp

```

save the changes
reboot

---

