---
title: "Wireless wont work."
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by adden93 on 2008-05-31
Hi all.

Im new to Ubuntu and cant get my wireless internet to work. I followed the Unencrypted steps in this thread

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

But i get the error message

"no workin leases in persistant database - sleeping"

at the very end. Any help would be appreciated but im thinking of going back to XP cause this is too complicated.

It'll work wired sometimes and my connection definatly works as it works on my XP desktop.

I have a Toshbia 2000  and im using eth1.

Adden

---

### Post by Sam Lars on 2008-05-31
What kind of wireless card do you have?

---

### Post by adden93 on 2008-06-01
I i have an intel network card, im not sure of the exact model tho. Erm if theres a line i can put into terminal that will help you please say, but im brand new to ubuntu nd have always been a windows person

Thanks 
Adden

---

### Post by cjbarrow on 2008-06-01
> **adden93 said:**
> I i have an intel network card, im not sure of the exact model tho. Erm if theres a line i can put into terminal that will help you please say, but im brand new to ubuntu nd have always been a windows person

Thanks 
Adden

open a terminal window and type lspci you should be able to find your card listed in the output

---

### Post by adden93 on 2008-06-02
Hi 

Intel 82557/8/9/0/1 ethernet pro 100

Is there a way i can check if a driver is installed...?

Thanks for your time

---

### Post by Sam Lars on 2008-06-02
> **adden93 said:**
> Hi 

Intel 82557/8/9/0/1 ethernet pro 100

Is there a way i can check if a driver is installed...?

Thanks for your time

Is that an ethernet card or a wireless card?
Is it working?  What is the output of the following commands?
```
ifconfig
iwconfig
```

---

### Post by adden93 on 2008-06-03
Hi i think the driver is installed right...

ifconfig...

adden@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:39:13:12:a5  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::200:39ff:fe13:12a5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1228 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:874318 (853.8 KB)  TX bytes:140657 (137.3 KB)

eth1      Link encap:Ethernet  HWaddr 00:02:2d:46:3e:38  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0x100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:480 errors:0 dropped:0 overruns:0 frame:0
          TX packets:480 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24000 (23.4 KB)  TX bytes:24000 (23.4 KB)

iwconfig...

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:""  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=134/153  Noise level=134/153
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Some more info...

ip address: 192.168.0.1
Router:  Netgear DG834GT
ISP: Sky Broadband
At present: Wired network using a cat5 eth cable (on laptip that wireless dosent work)

Thanks, and im now getting quite desperate, as i need this for work
Adden

---

### Post by Sam Lars on 2008-06-03
It looks like it's working, a driver is definitely installed, it's just not associated with the access point.  Are you configuring it through network manager or manually?

---

### Post by adden93 on 2008-06-04
Ive tried configuring it both ways but remember I was using it then wired is it defiantly set up right for Wireless. ?

---

### Post by chili555 on 2008-06-04
It is not going to work with Network Manager as long as the wire is connected and you have an IP address, which you do:> eth0 Link encap:Ethernet HWaddr 00:00:39:13:12:a5
inet addr:192.168.0.3 Bcast:192.168.0.255 Mask:255.255.255.0If you reboot without the wire, can you now configure your wireless?

[https://help.ubuntu.com/community/NetworkManager?action=show&redirect=WifiDocs%2FNetworkManager](https://help.ubuntu.com/community/NetworkManager?action=show&redirect=WifiDocs%2FNetworkManager)

I'd love to see:```
sudo lshw -C network
```Is this a PCMCIA card?

---

### Post by adden93 on 2008-06-04
Hi and Thabks I will try out your suggestion.

Here is that command you asked for.

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: 0d
       serial: 00:00:39:13:12:a5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:02:2d:46:3e:38
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 8.10 multicast=yes wireless=IEEE 802.11b



Many thanks
Adden

---

### Post by chili555 on 2008-06-04
May I assume this is, indeed, a PCMCIA card? One of those separate cards you can slide in a slot on the side of a laptop? If so, please *sudo gedit /etc/pcmcia/config.opts* and add a new line:```
exclude irq 3
```Save and close gedit. Reboot without the wire and do:```
sudo iwconfig eth1 essid <your_essid>
sudo dhclient eth1
```Do you connect?

---

### Post by AznPat on 2008-06-04
i have the same problem to i cant get wireless.can i get some help please

---

### Post by adden93 on 2008-06-04
Hi its not a PCMCIA card its a built in Intel wirless card. Should have said. I have tred connecting with that link again but still no luck. im now getting Network Monitor poping up in my notifications area with a error:

Could not find information on interface 'eth1:avahi' in /proc/net/dev

Any more of your suggestions would be great...Is there a way i can totaly reset everything and start from scratch or is that not a good idea...?

---

### Post by Sam Lars on 2008-06-04
AznPat please post the output of
```
lspci
```
in a terminal.

adden93, could you post the output of iwconfig again?
When you use Network Manager, does it see wireless networks?  Can it connect?

---

### Post by adden93 on 2008-06-05
Hi everyone. I would just like ton say thanks very nuch for your help and I turned my Lapi on this morning to find it all working again. Im not sure what done the trick exactly but i went through the post chilli555 gave me about network manager and found it working after I re-booted this morning. Many thanks again Im very happy.

Adden

---

