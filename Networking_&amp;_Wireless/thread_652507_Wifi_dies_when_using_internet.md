---
title: "Wifi dies when using internet"
date: 2007-12-28
forum: Networking &amp; Wireless
---

### Post by WillThePlank on 2007-12-28
Hello

i am not a new Ubuntu user but i am not a Very experienced one

i know a few terminal commands and how to get around the system and install stuff but thats it

my problem is that i am using a usb wifi adaptor and it connects fine but as soon as i open an app that uses the internet like pidgin or firefox my wireless connection dies

ive made a youtube video about it with more details and heres the link

[http://uk.youtube.com/watch?v=Jg8-VQIqAoc](http://uk.youtube.com/watch?v=Jg8-VQIqAoc)

any help would be widley appreciated

thanks from Will

---

### Post by tinycamp on 2007-12-28
post the output for this commands:

```
ifconfig  <------ so we can check if you're losing your IP
iwconfig <-------- so we can check if you're actually losing wifi link
ps xa |grep dhclient <------- so we can check if your dhcp client is working fine

```

do this before and after the link loss

are you using any kind of wireless security?, if so, tell me wich, and try working without any for a few minutes.

it might be that your wireless signal is so weak that when you try to actually transport data on it, the link goes down. it could also be an interference, try changing the channel, and also try placing the adaptor on a different place, maybe with a small usb extension, maybe on the top of your desk.

THE VIDEO WAS A GOOD IDEA!

---

### Post by Digger78 on 2007-12-28
Try ndiswrapper with the windows XP driver 

Ndiswrapper - [http://ndiswrapper.sourceforge.net]("http://ndiswrapper.sourceforge.net")

ps. get a haircut! :p

---

### Post by WillThePlank on 2007-12-28
right this is what comes up

i have tried moving the adaptor aroudn and i get 76% signal and 3 bars

so heres what it told me

before drop out 

ifconfig

william@Time-Machine:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:A0:C9:8B:0B:37  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:0E:2E:C0:FA:F3  
          inet addr:192.168.0.9  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:2eff:fec0:faf3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4852 (4.7 KB)  TX bytes:4734 (4.6 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-0E-2E-C0-FA-F3-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

william@Time-Machine:~$ 


iwconfig

william@Time-Machine:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Bonner House"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:4D:D1:91:92   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

william@Time-Machine:~$ 

ps xa |grep dhclient

william@Time-Machine:~$ ps xa |grep dhclient
 6235 ?        S      0:00 /sbin/dhclient -1 -lf /var/lib/dhcp3/dhclient.wlan0.leases -pf /var/run/dhclient.wlan0.pid -q -e dhc_dbus=31 -d wlan0
 6335 pts/0    R+     0:00 grep dhclient
william@Time-Machine:~$ 

after drop out

ifconfig

william@Time-Machine:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:A0:C9:8B:0B:37  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wmaster0  Link encap:UNSPEC  HWaddr 00-0E-2E-C0-FA-F3-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

william@Time-Machine:~$ 


iwconfig

william@Time-Machine:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

william@Time-Machine:~$ 

ps xa |grep dhclient

william@Time-Machine:~$ ps xa |grep dhclient
 6430 pts/0    R+     0:00 grep dhclient
william@Time-Machine:~$

---

### Post by WillThePlank on 2007-12-28
> **Digger78 said:**
> Try ndiswrapper with the windows XP driver 

Ndiswrapper - [http://ndiswrapper.sourceforge.net]("http://ndiswrapper.sourceforge.net")

ps. get a haircut! :p


dude thanks for the info but i used ndiswrapper before 

and i came here to fix my wireless not be told to cut my hair

its my hair ill do what i want with it

god its 1:49 am and im cranky

i need coffie



sorry if it seems im lashin out but...gah *gets coffie*

---

### Post by tinycamp on 2007-12-29
what module are u using for the card?, what card is it?

for this, try:
```

lsmod <----- to see the kernel modules that are loades

dmesg <---- to see kernel messages about that module, or anything wireless

less /var/log/messages < ---- look for weird errors near the link loss

lsusb -v <----- helps identify the chipset of your adaptor


```

your last post tells me that you're losing the link completely, what do you have to do to bring it back up?

---

