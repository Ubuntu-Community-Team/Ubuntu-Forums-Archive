---
title: "Another intel 2200bg problem"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by Deegan on 2008-05-23
i just installed ubuntu 8.04 and im not quite sure whats wrong with my setup. i can see wireless networks available. i just read about 50 posts and none of them seem to help. im on a dell inspiron 9300. i have also tried to install wcid but it wont let me because it says it interferes with the network manager. what should i try now folks?

---

### Post by chili555 on 2008-05-23
If Network Manager is not performing as expected, you could certainly open Synaptic and uninstall it, along with its henchman, dhcdbd. Then install Wicd and see if you can then connect.

---

### Post by Deegan on 2008-05-23
just did that and still a no go. it stays on obtaining ip address. there are a few open non passworded and non encrypted networks i cant even connect to. ive been reading posts for about 6 hours maybe i should take a break. any other suggestions? do you think if i downloadd a different older version it would get rid of the problem. mant people have said that this version dosent like my card. i just took a look in Devices-Network Tools and eth1 or eth0 will not let me configure them and eth1 which should be my wireless card has no protocol information or anything but packets are being revieved and sent. is this normal? lshw -C network shows me this

bdk@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:e8:d9:7b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth1
       version: 05
       serial: 00:16:6f:01:b8:6d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated
bdk@ubuntu:~$

---

### Post by chili555 on 2008-05-23
> about 6 hours maybe i should take a break.Yes.> do you think if i downloadd a different older version it would get rid of the problemNot yet. May we take a look at:```
sudo iwconfig eth1
sudo iwlist eth1 scan
```Your *lshw* looks pretty healthy to me so I am not ready to throw in the towel yet.

---

### Post by Deegan on 2008-05-23
ok not sure what i did here but here is my new lshw with the other 2 things you asked for. i had to reinstall ubuntu cause i messed up the partition from windows. 

bryan@deegan:~$ sudo lshw -C network
[sudo] password for bryan: 
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:e8:d9:7b
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth1
       version: 05
       serial: 00:16:6f:01:b8:6d
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off

bryan@deegan:~$ sudo iwconfig eth1
eth1      radio off  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


bryan@deegan:~$ sudo iwlist eth1 scan
eth1      No scan results


hope this is what you wanted

---

### Post by chili555 on 2008-05-23
From *lshw:*> wireless=radio offFlip that switch or key combination on your laptop and see if you don't get back in the race.

---

### Post by Deegan on 2008-05-23
i cant it dosent work every other function that uses the function key does except that one. i have just noticed when i look at network/interfaces it says im using a wext driver but i thought i need to use ipa driver. either way it says i dont have permission to change it. in my device network tools i also have a device called eth1:avahi that seems to be doing something. it has an ip address broadcast address etc.. but i cant configure anything it says interface does not exsist

---

### Post by chili555 on 2008-05-23
Let's tackle the switch first and then move to the next issue. Please try:```
sudo rmmod -f ipw2200
sudo modprobe ipw2200 disable=0
sudo lshw -C network
```Is the *wireless=radio off* message gone? Can you connect?

---

### Post by Deegan on 2008-05-23
it says wireless 802.11g now instead but i still cant connect to anything

---

### Post by chili555 on 2008-05-23
Is the *wireless=radio off* message gone?

---

### Post by Deegan on 2008-05-23
yeah its not there anymore

---

### Post by chili555 on 2008-05-23
Excellent. Now let's create a file, if it's not already there:```
sudo gedit /etc/modprobe.d/ipw2200
```Put in the following:```
options ipw2200 disable=0
```Save and close gedit. Reboot. Any changes in your ability to connect?

---

### Post by Deegan on 2008-05-23
no sir no changes. i looked at iwconfig it says unassociated ESSID off/any.  more ideas? im know im a pita but i gotta keep trying i hate to give up when i know its just something dumb

---

### Post by Deegan on 2008-05-23
i have no idea what i did but i am connected now. internet works nice. i was messing with the network settings and enabled the ehternet jack and saved it. then the net started working. im rbooting now to see if it stays. nevermind it didnt seem to stick. i know it works now somehow. just gotta nail it down

---

### Post by Deegan on 2008-05-25
ok after reading tons and tons more threads and posts i have figured out what is happening. i have to manually set up the network settings and retype my networks password after every reboot. even if i save the settings they dont stick for some odd reason. i just overwrite the location everytime. at least im typing this from the laptop that is having the problem. at least i have gotten somewhere. anyone have a fix for the not saving my settings problem?

---

### Post by sewmyheadon on 2008-05-28
Hi Deegan,

I'm using the same laptop and I advocate replacing Network Manager with [Wicd]("http://wicd.sourceforge.net/download.php").  It does a good job of saving settings and offering more configurability than Network Manager.

Hope that helps.

---

