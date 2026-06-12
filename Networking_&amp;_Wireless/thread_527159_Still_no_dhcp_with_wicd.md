---
title: "Still no dhcp with wicd"
date: 2007-08-16
forum: Networking &amp; Wireless
---

### Post by caricc on 2007-08-16
I found wicd last night. My continuing problem is trying to setup wireless with dhcp.  

I have the broadcom 4306 wireless nic. I am using ndiswrapper with wicd. This is on a compaq v2000 laptop. 


I am using wpa-psk on a 2wire wireless dsl modem. 

I can see my essid. I put in the encryption key. Both with and without the "" "".

The problem is that if I try and connect with dhcp I can't get connected. 

If I use static ip and put in my ip address, gateway, etc...I show in the wicd manager that I get an ip address,  The same ip address that I manually input. 

But it shows that I have no internet connection. 

Wicd has gotten me the closest to getting connected wirelessly. If I go wired to the modem then I have no problems. 

I really would like to ditch my windows partition but not until the wireless is more stable in linux.

Your help will be very much appreciated. 

Thanks in advance.

---

### Post by kevdog on 2007-08-16
Can you connect without encryption (no wpa, wep, MAC filtering)??

Can you post
lshw -C network
route
ifconfig
iwlist scan

---

### Post by caricc on 2007-08-16
lshw:
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:87:dd:3c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.4.87 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:3000-30ff iomemory:e0208800-e02088ff irq:18
  *-network:1
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@02:06.0
       logical name: wlan0
       version: 03
       serial: 00:90:4b:a8:6d:33
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.47+Broadcom,04/21/2005, 3.100. latency=64 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:e0204000-e0205fff irq:20

route:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.4.0     *               255.255.255.0   U     0      0        0 wlan0
default         192.168.4.1     0.0.0.0         UG    0      0        0 wlan0

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:87:DD:3C  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:42825 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11585 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22374747 (21.3 MiB)  TX bytes:1454445 (1.3 MiB)
          Interrupt:18 Base address:0xa800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2198 (2.1 KiB)  TX bytes:2198 (2.1 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:90:4B:A8:6D:33  
          inet addr:192.168.4.87  Bcast:192.168.4.255  Mask:255.255.255.0
          inet6 addr: fe80::290:4bff:fea8:6d33/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:75 errors:0 dropped:0 overruns:0 frame:0
          TX packets:174 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8475 (8.2 KiB)  TX bytes:16244 (15.8 KiB)
          Interrupt:20 Memory:e0204000-e0206000 

iwlist scan:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:50:BF:B1:D9:DC
                    ESSID:"Motorola"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:37/100  Signal level:-72 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  

This is to a wireless network here at work. I will post my results from home later tonight.

---

### Post by kevdog on 2007-08-16
We can automate the following process later but the commands below will at least tell us if you can get a connection and associated (so dont think this is a permanent solution):

Manual WPA setup -- some tips:

Make sure wpa_supplicant package is installed.  If it is not then at command line:
```

sudo aptitude install wpasupplicant

```

Next we are going to create a wpa_supplicant.conf file
```

gksu gedit /etc/wpa_supplicant.conf

```

Contents of the wpa_supplicant.conf file are the following:
This example is assuming WPA (not WPA2) with TKIP cipher
```

ctrl_interface=/var/run/wpa_supplicant
ap_scan=1

network={
       ssid="<your networks essid in quotes>"
       scan_ssid=0
       proto=WPA
       key_mgmt=WPA-PSK
       pairwise=TKIP
       group=TKIP
       psk="<ASCII password in quotes>"
}

```


At command line then try to connect to your network using these commands.  This is assuming your interface name is wlan0. If it is something different then make the appropriate changes.  A lot of debugging output will be given (the whole purpose of this exercise) This example also assumes your wireless driver to be wext=ndiswrapper. (See man wpa_supplicant for alternative choices):

```

sudo ifconfig wlan0 down
sudo ifconfig wlan0 0.0.0.0
sudo killall dhclient wpa_supplicant dhclient3
sudo rm /var/run/dhclient.pid
sudo wpa_supplicant -w -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd 
sudo ip route flush dev wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 mode managed
sudo dhclient wlan0

```

---

### Post by caricc on 2007-08-16
kevdog this WORKED. I followed all of your instructions to a T.  Now not only do I have wireless but it will connect up every time I boot the system.  This is EXACTLY what I have been looking.  
The Ubuntu developers need to include WICD into the next kernel upgrade. I have always been weary of performing a kernel update because I loose my wireless connection. 

My recommendation is to use the above process to get wicd and ndiswrapper to work for fiesty. 

I have put in so man hours and  days trying to make wireless work. now I have a plan. 

Thanks again a WHOLE lot. 

If the wicd guys are reading this. I used the 1.3.3 version. IT ROCKS!!!   <img>http://ubuntuforums.org/images/smilies/guitar.gif<img>

---

### Post by imdano on 2007-08-16
Good to hear wicd did the trick for you.  Was wpasupplicant not installed, or did just entering those commands lead to it working?

---

### Post by caricc on 2007-08-17
I believe editing the wpa_supplicant.conf did the trick.  The commands didn't really do much. I did have wpa_supplicant installed.  but the conf file wasn't set right. I ren the original file then copy/pasted the above wpa_supplicant.conf into its place. edited it to match my setup at home. Then put the same info into the wicd manager.

---

### Post by soulbreak on 2007-09-01
how would I get this to work with wep instead of wpa and "tkiP" <- I don't even know what that is...

---

### Post by caricc on 2007-09-04
I don't know if this will work, but give it a try....

in the wpa_supplicant.conf
pronto=wep
pairwise=open
groupwise=open
If you're not using a password then I think you should leave it blank after the = . 

otherwise follow the above instructions from kevdog.

---

### Post by caricc on 2007-09-04
sorry that would be group=open

---

### Post by kevdog on 2007-09-04
Here is how to do it with WEP although its a little bit cumbersome, since these steps are really overkill.  

Just the basics
64 bit WEP = 10 character HEX key
128 bit WEP = 24 character HEX key
If you dont know the hex key but the ascii key you can use the following format: s:ASCII_KEY

You dont need the wpa supplicant package installed for wep, are the wpa_supplicant.conf file.  
You basically need to do something like this:

```

sudo ifconfig wlan0 down
sudo ifconfig wlan0 0.0.0.0
sudo killall dhclient dhclient3
sudo rm /var/run/dhclient.pid
sudo ip route flush dev wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid <ESSID_OF_NETWORK_IN_QUOTES>
sudo iwconfig wlan0 mode managed
sudo iwconfig wlan0 key HEX_KEY 
sudo dhclient wlan0

```

---

