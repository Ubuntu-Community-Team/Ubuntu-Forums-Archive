---
title: "Cannot access network via wireless"
date: 2007-08-04
forum: Networking &amp; Wireless
---

### Post by yaustar on 2007-08-04
I have just configured the Wireless network settings and iwconfig says it has connected to the router:
```
eth1      IEEE 802.11g  ESSID:"XXXXXXXX"
          Mode:Managed  Frequency:2.472 GHz  Access Point: 00:11:50:92:DB:7F
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=91/100  Signal level=-38 dBm  Noise level=-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:126  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:1
```

However, I can't access any websites or shared folders. Have I missed something completely obvious?

---

### Post by smileypaul on 2007-08-04
hey man, you may be associated with it, but make sure you have an ip address by doing the following

ifconfig

this will tell you if you have an ip address, it should be something similar to 192.168.x.xxx .. of course, this all depends on your router..

if you do have a "VALID" ip address, then you should try pinging the router.. its address is the default gateway.. usually 192.168.x.1 .. where x =0, 1, or 2.. again, depends on router.

if you can't ping it, then you are not connected.. make sure you dont have a mac filter on the router, and that you can get on..

want to restart networking?

sudo /etc/init.d/networking restart

and then 

ifdown eth1

ifup eth1

and hopefully you can ge ton..

best of luck,

sorry, i dont check the forums very often

---

### Post by yaustar on 2007-08-04
Hmm, it actually looks like it can't resolve a connection with the router (no IP address). I tired setting up a static IP, the applet for Gnome says it has a strong signal and iwconfig thinks it is connected but I can't ping the router. Could this be a firewall problem?

---

### Post by kevdog on 2007-08-04
Can you tell us more about your card since I dont have enough information to help you.

If its a pci/pcmcia card please post
lspci -nn

If usb device
lsusb

For both also type at command prompt and post output
lshw -C network

Thank:)

---

### Post by yaustar on 2007-08-04
```
yaustar@yau-ulaptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0
       description: Wireless interface
       product: PRO/Wireless 2200BG
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@01:04.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:1b:66:6e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:ff7fd000-ff7fdfff irq:185
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@01:06.0
       logical name: eth0
       version: 10
       serial: 00:40:45:20:c2:09
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too ip=192.168.2.5 multicast=yes
       resources: ioport:c800-c8ff iomemory:ff7ffc00-ff7ffcff irq:209
```

```
yaustar@yau-ulaptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:45:20:C2:09
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::240:45ff:fe20:c209/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4293 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4448 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2506547 (2.3 MiB)  TX bytes:528956 (516.5 KiB)
          Interrupt:209 Base address:0xc00

eth1      Link encap:Ethernet  HWaddr 00:0E:35:1B:66:6E
          inet6 addr: fe80::20e:35ff:fe1b:666e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:152 errors:4 dropped:4 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:20428 (19.9 KiB)
          Interrupt:185 Base address:0x8000 Memory:ff7fd000-ff7fdfff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:123 errors:0 dropped:0 overruns:0 frame:0
          TX packets:123 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:10299 (10.0 KiB)  TX bytes:10299 (10.0 KiB)

```
```
yaustar@yau-ulaptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"XXXXXXXXX"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:11:50:D1:D4:4C
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=76/100  Signal level=-53 dBm  Noise level=-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:4  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:5

sit0      no wireless extensions.
```

---

### Post by kevdog on 2007-08-04
How are you trying to connect -- through network manager??

Is your router set for any type of encryption (WEP,WPA, MAC FILTERING)?
If it is can you deactivate the encryption so we can test for a basic connection.

For a basic command line, through the command line (good for testing, bad for everyday use), you can do the following:

sudo ifconfig eth1 down
sudo killall dhclient wpa_supplicant dhclient3
sudo ip route flush dev eth1
sudo ifconfig eth1 up
sudo iwconfig eth1 mode managed
sudo iwconfig eth1 essid <your network's essid>
sudo dhclient eth1

(Thats basically what network manager does in a nutshell -- kindof).  Anyway that would give us some good debugging output to see if you can connect.

Oh one other thing -- you cant run a wired and wireless connection at the same time -- I noticed you are running a wired connection.  Unplug the networking cable and reboot

---

### Post by yaustar on 2007-08-05
Fixed it. I have a feeling I got caught out by this before years ago. The WEP key has to be entered in a specific format:
NN:NN:NN:NN:NN

I had it as:
NNNNNNNNNN
or
NN-NN-NN-NN-NN

Cheers for the help :)

---

