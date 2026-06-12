---
title: "Ubuntu, US54G and WPA"
date: 2007-03-15
forum: Networking &amp; Wireless
---

### Post by Fedayki on 2007-03-15
Hi there, 

I have recently installed Edgy Ubuntu on my inspiron 5150 (quick hot by the way) , and I would like to make my wifi dongle (MSI US54G, MS6861) to work on it, with on the other side a Freebox HD witk a WPA(TKIP+AES) encryption. I installed network manager, and I tried to connected myself on my network, but the wifi is trying to connect to it and nothing happened and it switch to my wire connection.

I have followed some guide but it didn't help.

Some details seems strange. Under network manager when I left click, I don't see any strength signal next to each network(see screen shot below). And when I try to configure the network connection nm don't let me choose WPA encryption(see screen shot too). I tried WEP also but it didn't helped. And it seems I can't leave my freebox open.

Here are some command I ran on Ubuntu. I hope it can help :

```
[fedaykin]@[fedaykin-laptop]~ $ lsusb
Bus 004 Device 004: ID 0db0:6861 Micro Star International 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 045e:0084 Microsoft Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```
```
[fedaykin]@[fedaykin-laptop]~ $lsmod
usbcore               134912  5 rt2570,usbhid,ehci_hcd,uhci_hcd
```
```
[fedaykin]@[fedaykin-laptop]~ $lshw
*-network
       description: Wireless interface
       physical id: 1
       logical name: rausb0
       serial: 00:13:d3:7e:83:45
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RT2500U
```
```
[fedaykin]@[fedaykin-laptop]~ $ cat /etc/network/interfaces
auto lo
iface lo inet loopback

#auto rausb0
#iface rausb0 inet dhcp
#wireless-essid WANADOO-****
#wireless-key *****************************
#wireless-channel 1

#auto eth0
#iface eth0 inet dhcp
#address 192.168.0.101
#netmask 255.255.255.0
#network 192.168.0.0
#broadcast 192.168.0.255

#auto rausb0
#iface rausb0 inet dhcp
#wpa-conf managed
#wpa-ap-scan 1
#wpa-scan-ssid 1
#wpa-ssid yyyyyy
#wpa-key-mgmt WPA-PSK
#wpa-psk xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```
(I tried some things as you can see but i commented all to make nm work)

These are the to screen shot I talked about earlier.

First of all the blank line, without strength signal (whereas I'm next to my freebox) :

[img]http://fallengalaxy.com/~fedaykin/nm.png[/img]

And this is the impossibility to choose the WPA encryption:

[img]http://fallengalaxy.com/~fedaykin/nmkey.png[/img]

I would be glad if you can help me.

Have a good evening

---

### Post by handaxe on 2007-03-15
sudo iwconfig

sudo ifconfig please

HA

---

### Post by Fedayki on 2007-03-15
Here you are :

```
[fedaykin]@[fedaykin-laptop]~ $ sudo iwconfig
lo        no wireless extensions.

rausb0    RT2500USB WLAN  ESSID:"NETGEA"  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=11 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/70  Signal level:-89 dBm  Noise level:-200 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

```

and


```

[fedaykin]@[fedaykin-laptop]~ $ sudo ifconfig
eth0      Lien encap:Ethernet  HWaddr 00:0F:1F:1A:D5:4A  
          inet adr:192.168.0.4  Bcast:192.168.0.255  Masque:255.255.255.0
          adr inet6: fe80::20f:1fff:fe1a:d54a/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:4621 erreurs:0 :0 overruns:0 frame:0
          TX packets:3833 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:4707769 (4.4 MiB) Octets transmis:658322 (642.8 KiB)
          Interruption:177 

lo        Lien encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:46 erreurs:0 :0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:2580 (2.5 KiB) Octets transmis:2580 (2.5 KiB)

rausb0    Lien encap:Ethernet  HWaddr 00:13:D3:7E:83:45  
          adr inet6: fe80::213:d3ff:fe7e:8345/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:590435 (576.5 KiB) Octets transmis:23776 (23.2 KiB)

```

---

### Post by Austin_KW on 2007-03-15
I could not get the standard rtxx driver to work for wpa so I downloaded and built a later driver
See my post from eariler today [http://www.ubuntuforums.org/showthread.php?p=2303019#post2303019](http://www.ubuntuforums.org/showthread.php?p=2303019#post2303019)

After building this my interfaces file now includes
[INDENT]auto rausb0
iface rausb0 inet dhcp
#wireless-essid XxxxxNet
    pre-up ifconfig rausb0 up
    pre-up ifconfig rausb0 down
    pre-up ifconfig rausb0 up
    pre-up iwpriv rausb0 set AuthMode=WPAPSK
    pre-up iwpriv rausb0 set EncrypType=TKIP
    pre-up iwconfig rausb0 essid  XxxxxNet
    pre-up iwpriv rausb0 set WPAPSK="xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxcScq2Yb"
    pre-up ifconfig rausb0 up[/INDENT]
Not sure why I put all those up/downs/up, I think I had a race condition somewhere. Once in a while the if driver gets confused (when I powercycle my junk router) I pull and reinsert the adapter

---

### Post by handaxe on 2007-03-15
Hi,

Your signal strength is not being reported by the device so that is a direct problem and not with n-m. In fact, these chipsets have driver problems and there are many reports of issues. The advice from [Austin_KW]("http://ubuntuforums.org/member.php?u=255914") is one way to try and sort it out. 

Before you do that, try this: 

 Open System->Administration->Networking and deactivate the rausb0 connection and then re-activate it. This may hang the networking window. Next open a terminal window
and type ```
 sudo ifup rausb0
```.

Does this get the interface going?[FONT=monospace]

Another approach is to try and use the xp drivers under ndiswrapper, but then you must blacklist the rt2570 driver in /etc/modprobe.d/blacklist[/FONT]

Finally, for wpa encryption you need wpa_supplicant - network-manager should se to that but make sure.

HA

---

### Post by Fedayki on 2007-03-17
Sorry for responding this late.

I'll try these solution as soon as i will be at home, which is not the case at the moment.

See you soon

---

### Post by Fedayki on 2007-03-20
> **handaxe said:**
> Hi,

Your signal strength is not being reported by the device so that is a direct problem and not with n-m. In fact, these chipsets have driver problems and there are many reports of issues. The advice from [Austin_KW]("http://ubuntuforums.org/member.php?u=255914") is one way to try and sort it out. 

Before you do that, try this: 

 Open System->Administration->Networking and deactivate the rausb0 connection and then re-activate it. This may hang the networking window. Next open a terminal window
and type ```
 sudo ifup rausb0
```.

Does this get the interface going?[FONT=monospace]

Another approach is to try and use the xp drivers under ndiswrapper, but then you must blacklist the rt2570 driver in /etc/modprobe.d/blacklist[/FONT]

Finally, for wpa encryption you need wpa_supplicant - network-manager should se to that but make sure.

HA

Ok I'm back.

So I tried the desactivate et re-activate things but it didn't change anything. Then for the ndiswrapper I can't find out where I put my install cd for my dongle, and I don't know where can I find my drivers. should I go to the msi website and download one? But which one? XP, XP-64 or other?


For wpa supplicant I got it, but I didn't do anything with it. And I tried some command to test but I think it didn't because I don't know if there is a .conf file :( 

```

[fedaykin]@[fedaykin-laptop]~ $ wpa_supplicant -Drt2500 -irausb0 -c/etc/wpa_supplicant.conf -ptest
Unsupported driver 'rt2500'.

[fedaykin]@[fedaykin-laptop]~ $ wpa_supplicant -Drt2570 -irausb0 -c/etc/wpa_supplicant.conf -ptest
Unsupported driver 'rt2570'.

[fedaykin]@[fedaykin-laptop]~ $ wpa_supplicant -Drt73 -irausb0 -c/etc/wpa_supplicant.conf -ptest
Unsupported driver 'rt73'.

[fedaykin]@[fedaykin-laptop]~ $ wpa_supplicant -Drt73usb -irausb0 -c/etc/wpa_supplicant.conf -ptest
Unsupported driver 'rt73usb'.
```

And I finally tried the modprobe with the rt73 driver but when I had done make install nothing appear in interfaces file. So I tried to put, and correct, your interfaces file content, but It seemed to loop with no end.

So I'm still stuck at the same point so if somebody have an idea I would be grateful.

Thanks

---

### Post by Fedayki on 2007-04-02
Since it still didn't work I will try to update edgy to feisty in order to see if it will work better.

I'll tell you if I have any news.

---

### Post by handaxe on 2007-04-04
Doh, just noticed that:

wpa_supplicant -Drt2570 -irausb0 -c/etc/wpa_supplicant.conf 
Should be probably

wpa_supplicant **-D wext** -i rausb0 -c/etc/wpa_supplicant.conf 
HA

---

### Post by Fedayki on 2007-04-21
It still does not work.

Even with the brand new feisty. I will have to throw my dongle away it seems :lolflag:

---

