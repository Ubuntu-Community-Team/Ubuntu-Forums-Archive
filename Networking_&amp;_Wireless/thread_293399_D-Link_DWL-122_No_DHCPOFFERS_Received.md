---
title: "D-Link DWL-122 No DHCPOFFERS Received"
date: 2006-11-05
forum: Networking &amp; Wireless
---

### Post by simeli on 2006-11-05
i got my edgy eft up and running in no time at all. i figured out pretty soon that i needed the linux-wlan-ng packge to get the dwl-122 ubs link working. so i installed the package. the device was properly recognised and reception is fine. now the problem started. no matter what i tried i couldn't get an ip-adress from the dhcp server (ifconfig, dhclient, etc....). 

all i get is: No DHCPOFFERS Received

i found that other people seem to have the same problem. anyone know the answer?

thanks a bunch in advance
s

---

### Post by FrodoB on 2006-11-05
Could you post the output of iwconfig, ifconfig, and netstat -rn please?

---

### Post by simeli on 2006-11-05
there you are.

**ifconfig:**
lo        Protokoll:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6 Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:1284 (1.2 KiB)  TX bytes:1284 (1.2 KiB)

wlan0     Protokoll:Ethernet  Hardware Adresse 00:13:46:95:60:C1  
          inet6 Adresse: fe80::213:46ff:fe95:60c1/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 b)  TX bytes:15888 (15.5 KiB)



**iwconfig:**
wlan0     IEEE 802.11-DS  ESSID:"antenne"  Nickname:"antenne"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:90:4B:33:44:7E   
          Bit Rate:2 Mb/s   Tx-Power:18 dBm   
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Link Quality=25/92  Signal level=-67 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


**netstat -rn:**
Kernel IP Routentabelle
Ziel            Router          Genmask         Flags   MSS Fenster irtt Iface


thank you.

---

### Post by FrodoB on 2006-11-05
So running dhclient wlan0 does not yield an offer and acceptance of an ip address? You have verified that your access point or router has dhcp server turned on I suppose.

When I invoke dhclient I get this:

user@whitebox:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:11:50:b4:47:f1
Sending on   LPF/wlan0/00:11:50:b4:47:f1
Sending on   Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.2
bound to 192.168.0.246 -- renewal in 272212 seconds.

What does your output?

---

### Post by simeli on 2006-11-06
yes, i do have a dhcp server running on my wireless router, and i obtain a valid ip adress for my windows computer. 
this is the console trace:

sudo dhclient wlan0
Password:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:13:46:95:60:c1
Sending on   LPF/wlan0/00:13:46:95:60:c1
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.



thanks for your help
/s

---

### Post by lssl on 2006-11-06
Hi simeli!

Try this

edit interfaces
```
sudo nano /etc/network/interfaces
```

and change your wlan0 settings to

```
auto wlan0
iface wlan0 inet dhcp
wireless_essid <your_essid>
wireless_mode managed
wireless_enc on #(or off)
wlan_ng_key0 xx:xx:xx:xx:xx
wlan_ng_authtype opensystem #(or sharedkey)

```
ctrl+o 
"enter" to save
ctrl+x to quit

then in terminal
```
sudo ifdown wlan0
sudo ifup wlan0
```

it works fine for me

---

### Post by Swab on 2006-11-06
Normally when there is a connection but you can't get an IP it's because the key is wrong...

---

### Post by simeli on 2006-11-08
no luck, this is what i get:

**sudo ifdown wlan0**
```
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:13:46:95:60:c1
Sending on   LPF/wlan0/00:13:46:95:60:c1
Sending on   Socket/fallback
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not supported.
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Operation not supported.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not supported.
```


**sudo ifup wlan0**
```
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not supported.
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Operation not supported.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not supported.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:13:46:95:60:c1
Sending on   LPF/wlan0/00:13:46:95:60:c1
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```


any ideas?

thank you for your help,
/s

---

### Post by arphe_el on 2006-11-08
i'm planning to built up a computer with wireless connection i'm using the linksys usb type 54GC for all desktop computers five of them. 

My question is what distro or version is good to install so as not to give me a headache. On hand i have my breezy. Any ideas?

---

### Post by lssl on 2006-11-08
> **simeli said:**
> no luck...

Did you wrote your key correctly? 
for example if your key is 1234567890 it should looks like this 12:34:56:78:90

You can also try nidswrapper, but don't use ubuntu packages. Use the latest version from [http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/) or use debian packages [http://ftp.gva.es/mirror/debian/pool/main/n/ndiswrapper/](http://ftp.gva.es/mirror/debian/pool/main/n/ndiswrapper/) 

Remove linux-wlan-ng and install ndiswrapper-common and ndiswrapper-utils.

Download latest dwl-122 driver from [ftp://ftp.dlink.com/Wireless/dwl122/Driver/](ftp://ftp.dlink.com/Wireless/dwl122/Driver/) (v. 102) and unzip 

now install driver with
```
ndiswrapper -i /path/to/downloaded/driver/NETPRISM.inf
```

To see the status of your installed drivers run
```
ndiswrapper -l
```
If you have installed the correct driver you should see something like this
```
Installed ndis drivers:
NETPRISM driver present, hardware present
```

now
```
sudo nano /etc/network/interfaces
```
```
iface wlan1 inet dhcp
wireless_keymode open
wireless_key xxxxxxxxx
wireless_mode managed
wireless_essid <your_ESSID>
auto wlan1
```
ctrl+o
"enter"
ctrl+x 
```
sudo ifdown wlan1
sudo ifup wlan1
```

---

### Post by animammal on 2006-11-08
I've got exactly the same issue! have you solved it?

---

### Post by simeli on 2006-11-09
all the answers put together finally solved the problem. thanks a million!

---

### Post by simeli on 2006-11-09
i have solved it. disable wep encryption. configure the /etc/networking/interfaces manually and you're up and running

---

### Post by DavidTangye on 2006-11-10
I have had the same problem.

The front end network-admin, run from System -> Administration -> Networking, does not set up /etc/networking/interfaces correctly. You can get a line 
> wireless-key s: in there if you set the Password type to Ascii but then do not put a password in there, eg if you remove WPA/WEP from your wireless setup. I think that line should be removed from /etc/networking/interfaces if you have nothing set in the Password field.

It seems to me that you need to set up /etc/networking/interfaces manually, and not use network-admin.

---

### Post by olafbujak on 2006-12-06
> **simeli said:**
> i have solved it. disable wep encryption. configure the /etc/networking/interfaces manually and you're up and running

Hello, I've got simillar situation :/

```
root@Bestyjka:/home/olaf# ifup wlan0
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not supported.
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Operation not supported.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFFLAGS: No such device
SIOCSIFFLAGS: No such device
Listening on LPF/wlan0/00:00:00:00:00:00
Sending on   LPF/wlan0/00:00:00:00:00:00
Sending on   Socket/fallback
receive_packet failed on wlan0: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
```


Can I kindly ask you for help with that? I'm using ndiswrapper just like lssl wrote [http://ubuntuforums.org/showpost.php?p=1731884&postcount=10](http://ubuntuforums.org/showpost.php?p=1731884&postcount=10). And:

```
root@Bestyjka:/home/olaf# ndiswrapper -l
Installed drivers:
netprism                driver installed, hardware present 
```

```
root@Bestyjka:/home/olaf# lsmod |grep ndis
ndiswrapper           208656  0 
usbcore               134912  5 ndiswrapper,prism2_usb,ehci_hcd,uhci_hcd
```

```
root@Bestyjka:/home/olaf# lsmod |grep prism
prism2_pci             74752  0 
prism2_usb             79236  0 
usbcore               134912  5 ndiswrapper,prism2_usb,ehci_hcd,uhci_hcd

```

```
root@Bestyjka:/home/olaf# cat /etc/network/interfaces 
auto lo
iface lo inet loopback


face wlan0 inet dhcp
wireless_keymode open
wireless_key anitakasia
wireless_mode managed
wireless_essid figlemigle
auto wlan0
```

```
root@Bestyjka:/home/olaf# lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 2001:3700 D-Link Corp. [hex] DWL-122 802.11b
```



What should I do? Can you advice me anything?

---

### Post by anunn2001 on 2006-12-06
For what it is worth, I recently set up a Compaq Laptop using a DWL-122 Rev B USB network dongle. I found that it works fine after loading Linux-wlan-ng but will not work if I load Network-Manager. With just the Edgy install and Linux-wlan-ng it will connect and disconnect just fine even if I unplug that dongle while this system is running. The only way to get it to work if Network-Manager was loaded was to hard code everything in the interfaces file, which as I understand keeps Network-Manager from managing the interface. 

I have also loaded wlan assistant but I have never invoked it so it probably doesn't enter into the issue unless the fact it is loaded has some effect.

---

### Post by olafbujak on 2006-12-06
Ok, so I'm back to the first way with linux-wlan-ng - after cleanup and ndiswrapper deinstalation I've got:

```
root@Bestyjka:/home/olaf# cat /etc/network/interfaces 
auto lo
iface lo inet loopback

iface eth0 inet dhcp
auto eth0

auto wlan0
iface wlan0 inet dhcp
wireless_essid figlemigle
wlan_ng_key0 c951f58915c8fb532f32e5c9f2
wlan_ng_authtype opensystem
wireless_mode infrastructure
```

and


```

root@Bestyjka:/home/olaf# ifup wlan0
Error for wireless request "Set Mode" (8B06) :
    invalid argument "infrastructure".
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not supported.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:13:46:6b:c6:6d
Sending on   LPF/wlan0/00:13:46:6b:c6:6d
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
root@Bestyjka:/home/olaf# 
```

---

### Post by olafbujak on 2006-12-10
****. I was trying several other solutions with linux-wlan-ng-build-firmware-deb included and right now I've got real mess in my system :/

I'm going to try Dapper instead Edgy or... I'll switch into opensuse where everything is running correctly from the fair beginning.

---

### Post by olafbujak on 2006-12-10
DONE! ;] My way is:

apt-get remove --purge linux-wlan-ng linux-wlan-ng-doc
and then use Ndiswrapper
[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29)

reboot

check *iwlist scanning* and if it's working install **wifi-radar** - configure your connection.

---

### Post by dbw on 2006-12-23
*problem*
I have some notes on this topic.  Using various computers, I was formerly able to connect to my parent's wifi router.  On my last visit, I set up encryption for them, and I can no longer connect with any of my Linux machines (breezy, dapper, and edgy), and receive the "no dhcpoffers received, no working leases" error message

*password?*
Some have said that this comment indicates an improper password.  I use the same 10 digit hex password on both windoze and Linux partitions, copied from a the same text file.  I can implement it on their windoze boxes, but not in Linux.  

*range*
I think this is related to range issues in the madwifi drivers:  sometimes when I do iwlist wlan0 scan, I get no networks found.  This symptom is sporadic, however.  I am only ~15 ft from the router, and in easy range - signal is amazing in windoze.  I would also like to point out that after booting to Linux, when I restart in Windows, the networks are not detected until I manually request a network search - a step that is not necessary when I simply reboot windoze.

*password format note*
A further note.  Someone said earlier that it is necessary to input the password as 12:34:56:..., but when I use
```
sudo iwconfig wlan0 key xx:xx:xx:xx:xx
```
it is saved in the interfaces file in plain text as xxxxxxxxxx .

---

### Post by dbw on 2006-12-28
bump.

---

### Post by sgornick on 2007-01-22
I'm finding that (in Dapper) when I change settings to /etc/network/interfaces that the new values aren't taking effect even though I restart network services.  But then when I reboot, the new settings work fine. Alternatively, if I manually do iwconfig and explicitly set essid, channel, and key -- then the next time I restart network services, the new settings will take effect and will connect just fine.

I filed a bug report that has not yet been confirmed, but maybe something from that report will help you with this issue.  This forum thread was initially discussing a problem on Edgy so if what I experienced is also occuring for anyone on Edgy, please add mention of problem occuring with that release as well to the bug report:
[https://launchpad.net/ubuntu/+source/netbase/+bug/80499](https://launchpad.net/ubuntu/+source/netbase/+bug/80499)

---

### Post by olskar on 2007-07-19
I to have this problem..on two computers..with different cards..so it must be ubuntu.. :(

---

