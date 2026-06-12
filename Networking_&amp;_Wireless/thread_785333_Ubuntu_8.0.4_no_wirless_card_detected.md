---
title: "Ubuntu 8.0.4 no wirless card detected"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by principe on 2008-05-07
First sorry if this issue is already solved, but couldn't find on forums.

I've downloaded vmware Ubuntu 8.04 Hardy and running great.
On my laptopo IBM T60 I have Intel Pro 3495ABG wireless card, but haven't detected by Ubuntu

jars@jars-desktop:/$ ifconfig
eth2      Link encap:Ethernet  HWaddr 00:0c:29:4e:c3:c4  
          inet addr:192.168.10.29  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe4e:c3c4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28338 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3325 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11236699 (10.7 MB)  TX bytes:404037 (394.5 KB)
          Interrupt:18 Base address:0x1400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3542 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3542 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:177100 (172.9 KB)  TX bytes:177100 (172.9 KB)

And after iwconfig run:
jars@jars-desktop:/$ iwconfig
lo        no wireless extensions.

eth2      no wireless extensions.


It seems that my wireless card isnt detected by Ubuntu. 

Please, as i'm new on this how to manage this issue?

Regards.

---

### Post by chili555 on 2008-05-07
Network Manager, which is installed by default, will not activate your wireless as long as you have a good, working IP address with your wired interface, which you do:```
eth2 Link encap:Ethernet HWaddr 00:0c:29:4e:c3:c4
inet addr:192.168.10.29
```Please detach the wire, restart networking:```
sudo /etc/init.d/networking restart
```Does your wireless come to life?

---

### Post by mapes12 on 2008-05-07
Probably doesn't work as there may not be a Linux driver for the wireless card. If you can locate the windoze driver for it then there is a utility called ndiswrapper ([http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/)) which configures the windoze driver so that Ubuntu can use it.

I've tried it and it worked for a while but then started devolping problems. To solve the problem I bought a PCMCIA wifi card that I new worked straight out of the box. It cost me £10 but saved a mutitude of grief. 

Supported wireless card links are here: [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

The one I got was a Comtrend RT2500 54 Mbps Wireless PCMCIA card from these guys: [http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/) and it worked as soon as I inserted into my laptop (IBM Thinkpad 23). All I had to do was to enter my router SSID and encryption key. It's been fine for a couple of months now.

---

### Post by chili555 on 2008-05-07
> Probably doesn't work as there may not be a Linux driver for the wireless card. With all due respect, there most certainly is: iwl3945. It seems to work a bit better with:```
sudo apt-get install linux-backports-modules-hardy-generic
```

---

### Post by principe on 2008-05-07
> **chili555 said:**
> With all due respect, there most certainly is: iwl3945. It seems to work a bit better with:```
sudo apt-get install linux-backports-modules-hardy-generic
```

Have tried to install bacports, and restart networking but no luck.

i canot see wireless card detected. I've read on some other posts that this Intel Pro 3945 should be automatically detected??

Please advise, what else can i check.

Regards

---

### Post by chili555 on 2008-05-07
And you detached the wire before you restarted networking? I know, I'm a worry-wart. May I please see:```
sudo lshw -C network
sudo cat /var/log/messages | grep Kill
```> Intel Pro 3945 should be automatically detected?Yes, exactly.

Thanks

---

### Post by principe on 2008-05-07
> **chili555 said:**
> And you detached the wire before you restarted networking? I know, I'm a worry-wart. May I please see:```
sudo lshw -C network
sudo cat /var/log/messages | grep Kill
```Yes, exactly.

Thanks

Thanks on tracking this issue.

i'm not on wire, my laptop is connected to internet through wireless card the intel above, but on vmware ubuntu machine the same one cannot be detected.

here are the outputs on your commands:

jars@jars-desktop:~$ sudo lshw -C network
[sudo] password for jars: 
  *-network               
       description: Ethernet interface
       product: 79c970 [PCnet32 LANCE]
       vendor: Advanced Micro Devices [AMD]
       physical id: 11
       bus info: pci@0000:00:11.0
       logical name: eth2
       version: 10
       serial: 00:0c:29:4e:c3:c4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical logical
       configuration: broadcast=yes driver=pcnet32 driverversion=1.34 ip=192.168.137.129 latency=64 link=yes maxlatency=255 mingnt=6 module=pcnet32 multicast=yes
jars@jars-desktop:~$ 

jars@jars-desktop:~$ sudo cat /var/log/messages |grep Kill
jars@jars-desktop:~$ 


Regards.

---

### Post by Roadcrew on 2008-05-07
Chili555

:) I've been trying to get my Intel 3945abg working for multiple days now. I've lost track of the varying things I've tried (but I still have the links to numerous pages). Something you've said in this particular post seems to make all the difference for me. 

**sudo /etc/init.d/networking restart**

First time I setup the wireless connection after install, I connected to my ap with the password just fine. Every single subsequent re-boot, I was unable to connect to the ap. Was driving me nuts (being a noob and all). The 3945 has been detected without problem. 

Now, once I log in I just do the netwoking restart command and wireless starts to work. Should I need to do this every time or is my noob-nish getting in the way of something I should know.

Thanks alot for responding to posts in this forum. You and others are really helping me make the transition from the *dark side*

---

### Post by WkenCouser on 2008-05-07
Hello,
I had installed Ubuntu Gutsy Gibson from scratch and updated the wireless connection. I am using WPA2 personal for the wireless security. All was working OK.
I upgraded to Ubuntu Hardy Heron using the update path using a wires connection. I lost my wireless connection and nothing I did helped.
Finally I downloaded the .iso full version install, burnt it to a cd and did  a clean install. After the install I updated the packages from the repository and voila the wireless connection reappeared and I am now using it again. 
Ken :)

---

### Post by idoisler on 2008-05-08
i tried it but i still dont get wireless to work here is what i got

sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:a0:d1:85:51:24
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=192.168.1.3 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1c:bf:0e:70:ca
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
phoedo@phoedo-laptop:~$ sudo cat /var/log/messages | grep Kill
May  8 12:48:00 phoedo-laptop kernel: [   33.806016] iwl3945: Radio Frequency Kill Switch is On:
May  8 12:48:00 phoedo-laptop kernel: [   33.806019] Kill switch must be turned off for wireless networking to work.
May  8 13:51:54 phoedo-laptop kernel: [ 1653.367550] iwl3945: Radio Frequency Kill Switch is On:
May  8 13:51:54 phoedo-laptop kernel: [ 1653.367557] Kill switch must be turned off for wireless networking to work.
May  8 13:57:32 phoedo-laptop kernel: [ 1990.755176] iwl3945: Radio Frequency Kill Switch is On:
May  8 13:57:32 phoedo-laptop kernel: [ 1990.755182] Kill switch must be turned off for wireless networking to work.
May  8 14:04:01 phoedo-laptop kernel: [   33.027416] iwl3945: Radio Frequency Kill Switch is On:
May  8 14:04:01 phoedo-laptop kernel: [   33.027419] Kill switch must be turned off for wireless networking to work.
May  8 14:09:17 phoedo-laptop kernel: [  439.834137] iwl3945: Radio Frequency Kill Switch is On:
May  8 14:09:17 phoedo-laptop kernel: [  439.834144] Kill switch must be turned off for wireless networking to work.
May  8 14:11:45 phoedo-laptop kernel: [  586.853275] iwl3945: Radio Frequency Kill Switch is On:
May  8 14:11:45 phoedo-laptop kernel: [  586.853281] Kill switch must be turned off for wireless networking to work.
May  8 14:16:11 phoedo-laptop kernel: [  853.452297] iwl3945: Radio Frequency Kill Switch is On:
May  8 14:16:11 phoedo-laptop kernel: [  853.452303] Kill switch must be turned off for wireless networking to work.
May  8 14:20:44 phoedo-laptop kernel: [ 1125.542972] iwl3945: Radio Frequency Kill Switch is On:
May  8 14:20:44 phoedo-laptop kernel: [ 1125.542978] Kill switch must be turned off for wireless networking to work.


the wireless button was off....
any ideas???

---

### Post by chili555 on 2008-05-08
> ip=192.168.1.3 latency=0 link=yes > Kill switch must be turned off for wireless networking to work.As outlined above, for Network Manager to activate wireless, you muct detach the wire and let NM relinquish your IP address. Then, obviously, you need to find the key combination or switch that turns the wireless on and push it. *Then* does the wireless come alive?

---

### Post by chili555 on 2008-05-08
> **Roadcrew said:**
> Chili555

:) I've been trying to get my Intel 3945abg working for multiple days now. I've lost track of the varying things I've tried (but I still have the links to numerous pages). Something you've said in this particular post seems to make all the difference for me. 

**sudo /etc/init.d/networking restart**

First time I setup the wireless connection after install, I connected to my ap with the password just fine. Every single subsequent re-boot, I was unable to connect to the ap. Was driving me nuts (being a noob and all). The 3945 has been detected without problem. 

Now, once I log in I just do the netwoking restart command and wireless starts to work. Should I need to do this every time or is my noob-nish getting in the way of something I should know.

Thanks alot for responding to posts in this forum. You and others are really helping me make the transition from the *dark side*First, thank you for your kind comments.

Are you letting Network Manager control your wireless connection, that is, have 'Roaming' enabled? If not, the directive to start your wireless automatically should be in the file */etc/network/interfaces.* For example, if your wireless interface is eth1, your *interfaces* file should include 'auto eth1,' like mine:```
auto lo
iface lo inet loopback

#auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid GBR919
wireless-key 096c7f280exxyyzz restricted
wireless-ap 99:9C:41:19:58:77
```Notice 'auto eth0' is commented out because I do not want it to start automagically; there is no wire connected.

Tell us a bit more about your setup.

---

### Post by Roadcrew on 2008-05-08
Hi Chili555

I have roaming unchecked. NetworkManager doesn't seem to work for me. I have a Manual Network Configuration icon where I configured the wireless connection.

**lshw returns this** 

  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:21:3f:8e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.109 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:05:0b.0
       logical name: eth0
       version: 10
       serial: 00:90:f5:4f:58:01
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=64 maxlatency=64 mingnt=32 module=r8169 multicast=yes


**My  /etc/network/interfaces contains:**

auto lo
iface lo inet loopback


auto wlan0
iface wlan0 inet dhcp
wpa-psk xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA2
wpa-ssid 3dragons

#auto wlan0



I added the auto wlano per your response. I get an ip 169.254 something.

Wired connection has worked ootb, currently not plugged in to wire.

This is a Sager 5460 laptop. I have Ubuntu 8.04 istalled on top of XP using WUBI. Initially was running Ubuntu in VirtualBox and the wireless just worked, but it wasn't defined as the intel 3945 wnic 



**ifconfig returns:**

eth0      Link encap:Ethernet  HWaddr 00:90:f5:4f:58:01  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0x4c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1431 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1431 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:72989 (71.2 KB)  TX bytes:72989 (71.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:de:21:3f:8e  
          inet addr:192.168.1.109  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:fe21:3f8e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:55333 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36639 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:73917207 (70.4 MB)  TX bytes:4220271 (4.0 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-21-3F-8E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


I don't know what lo & wmaster0 is.

I still needed to restart networking in order to connect.

This is kinda rambling, if there's something in particular you'd like to see just let me know.

Again , thanks for taking the time. I do appreciated it. :)

---

### Post by principe on 2008-05-09
**Is there any help for the first question here?** No wireless card device detected at all.

---

### Post by bogey100s on 2008-05-09
Hi,

I have a IBM T30 notebook and have tried for to get a Cisco Aironet 532 PCMCIA wireless card working for several days now. Nothing seems to work.  I've tried all the suggestions in this treat.  I then dug up and old 3Com wireless card and stuck it into my computer.  I rebooted the computer and immediately my 3Com card was recognized.  Can anyone help me to get my Cisco card working?  My computer does see the Cisco card when I run the lshw command.  See below.  

Thanks in advance!

--------------------------------------------------------

root@IBM-T30:/sbin# lshw -C network
  *-network               
       description: 3Com
       physical id: 0
       version: 3CRSHPW_96 Wireless LAN PC Card
       slot: Socket 0
       resources: irq:3
  *-network
       description: Cisco Systems
       physical id: 0
       version: 350 Series Wireless LAN Adapter
       slot: Socket 1
       resources: irq:4
  *-network
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:09:6b:d0:9c:77
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:04:75:bc:4c:ce
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.250.104 multicast=yes wireless=IEEE 802.11-DS
root@IBM-T30:/sbin# cat /var/log/messages | grep Kill
root@IBM-T30:/sbin#

---

### Post by chili555 on 2008-05-09
This: [http://ubuntuforums.org/showthread.php?t=409247&highlight=Aironet](http://ubuntuforums.org/showthread.php?t=409247&highlight=Aironet) specifically, post #9, is what got my Aironet working.

---

### Post by bogey100s on 2008-05-09
Thanks Chili555!  The additions to the blacklist file worked great.

---

### Post by NDAggie on 2008-05-09
> **principe said:**
> **Is there any help for the first question here?** No wireless card device detected at all.

Principe,

It sounds like you have the same problem I was recently having:

- I have a laptop with Windows as the primary operating system.
- I have the exact same Intel wireless card (3945ABG) as you.
- I run Ubuntu inside of Windows using VMWare.
- The Ubuntu session in VMWare appears to not detect any wireless card, no matter what you try in Ubuntu.

I suspect that the trouble does not lie in Ubuntu, but lies in one of your VMWare settings.  I found that I was able to get my wireless card to work in Ubuntu by changing a VMWare setting:

Look in the bottom right corner of your VMWare window where there are 5 icons shown.  The third icon from the right is the ethernet icon.  If you move your mouse over it it will probably say "Ethernet: Bridged".  If this is the case then try this:  Right click on the ethernet card icon and select "Edit...", then select the box that says "NAT: Used to share the hosts IP address".  If your wireless card is working in Windows, then this should get the wireless network going in Ubuntu.  

At least it worked for me, so hopefully it will work for you too.

---

### Post by principe on 2008-05-09
> **NDAggie said:**
> Principe,

It sounds like you have the same problem I was recently having:

- I have a laptop with Windows as the primary operating system.
- I have the exact same Intel wireless card (3945ABG) as you.
- I run Ubuntu inside of Windows using VMWare.
- The Ubuntu session in VMWare appears to not detect any wireless card, no matter what you try in Ubuntu.

I suspect that the trouble does not lie in Ubuntu, but lies in one of your VMWare settings.  I found that I was able to get my wireless card to work in Ubuntu by changing a VMWare setting:

Look in the bottom right corner of your VMWare window where there are 5 icons shown.  The third icon from the right is the ethernet icon.  If you move your mouse over it it will probably say "Ethernet: Bridged".  If this is the case then try this:  Right click on the ethernet card icon and select "Edit...", then select the box that says "NAT: Used to share the hosts IP address".  If your wireless card is working in Windows, then this should get the wireless network going in Ubuntu.  

At least it worked for me, so hopefully it will work for you too.

Yes, it's the same configuration as you have, but i've already try to change vmware ethernet device from bridge to nat and vice versa but no effect. 

This really desperate me, why is hard to get wireless working on linux systems :(

I would really appreciate some help on this newbie problem.

Thanks for your effort NDAggie.

Regards.

---

### Post by principe on 2008-05-12
Just for info, this Ubuntu 8.04 is vmware image and running under VMware workstation. Is VMWare here making problem not passing info for wireless device?

I know there is an option in vmware settings for mapping network pci devices to VMNet adapters.

Does this informations helps anyone to help me get my Intel 3945ABG wireless device recognized under Ubuntu vmware machine?

---

