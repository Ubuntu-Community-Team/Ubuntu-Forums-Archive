---
title: "Wireless cant get Access Point"
date: 2007-10-17
forum: Networking &amp; Wireless
---

### Post by Frijole on 2007-10-17
```
frijole@theBean:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     802.11b/g  ESSID:"KLABO"  
          Mode:Managed  Frequency=2.472 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   
          Retry:on   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I cannot get this card to work, I have used ndiswrapper and still wont connect, need help please.

---

### Post by jbaerbock on 2007-10-18
What type of card do you have? Once we know that then we can help.

---

### Post by Frijole on 2007-10-18
Airlink + 101 802.11G Wireless PCI adapter AWLH3028

---

### Post by jbaerbock on 2007-10-18
Ok with my broadcom card I have to type in the following for it to connect to an access point:

sudo iwconfig wlan0 mode auto

For some reason by forcing it to go to auto instead of mode manages as is usual works. at least in my case. your problem sounds just like what mine was though. If you want that command to run at startup so you do not have to type it in everytime you restart follow the following thread:

[http://www.linuxmint.com/forum/viewtopic.php?t=5454](http://www.linuxmint.com/forum/viewtopic.php?t=5454)

What is in that thread applies to ubuntu as well as mint. Try the command in the terminal first then try and connect to make sure it works before you add it to the file listed on that thread.

---

### Post by Frijole on 2007-10-18
I doesn't seem to be doing the trick, here is the code:

```
frijole@theBean:~$ sudo iwconfig wlan0 mode auto
frijole@theBean:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     802.11b/g  ESSID:"KLABO"  
          Mode:Auto  Frequency=2.472 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   
          Retry:on   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by Oraclegol on 2007-10-18
a what channel is the AP on
using iwlist [interface] freq
i get 2.472 is channel 13

---

### Post by Frijole on 2007-10-18
```
frijole@theBean:~/Desktop/driver$ iwlist wlan0 freq
wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Channel=5
```

---

### Post by Oraclegol on 2007-10-18
really you still are getting 

Mode:Auto  Frequency=2.472 GHz  Access Point: Not-Associated   
when you type in iwconfig

btw have you tried
ifconfig wlan0 up
and
iwconfig wlan0 essid 'KLABO'

---

### Post by Frijole on 2007-10-18
```
frijole@theBean:~$ sudo ifconfig wlan0 up
[sudo] password for frijole:
frijole@theBean:~$ iwconfig wlan0 essid 'KLABO'
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not permitted.
frijole@theBean:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     802.11b/g  ESSID:"KLABO"  
          Mode:Managed  Frequency=2.484 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   
          Retry:on   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by Oraclegol on 2007-10-18
hmm try it with the sudo command with infront of the set essid

---

### Post by Frijole on 2007-10-18
```
frijole@theBean:~$ sudo iwconfig wlan0 essid 'KLABO'
frijole@theBean:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     802.11b/g  ESSID:"KLABO"  
          Mode:Managed  Frequency=2.467 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   
          Retry:on   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by Oraclegol on 2007-10-18
hmm k try this

```

sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode managed
sudo iwconfig wlan0 channel #
sudo iwconfig wlan0 essid 'KLABO'
sudo iwconfig wlan0 key '$$$$$$$$$'
sudo ifconfig wlan0 up
sudo dhclient wlan0

```
hopefully that works note
#= your channel number of your ap
$= your wep code
note: if you don't have a wep code you don't need to use that line
also i have no idea how to put in a wpa code

---

### Post by Frijole on 2007-10-18
what is my channel number?

---

### Post by Oraclegol on 2007-10-18
it is the channel that your ap broadcast's it's signal on 
im able to find this using
iwlist wlan0 scan

---

### Post by Frijole on 2007-10-18
```
frijole@theBean:~$ iwlist wlan0 scan
wlan0     No scan results

```

---

### Post by Oraclegol on 2007-10-18
hmmmm

If the scan does not find your AP, try issuing the command iwconfig wlan0 essid ESSID before using the command iwlist wlan0 scan. If this lists your AP, you can continue. Otherwise, you may have one of two problems: Your AP doesn’t broadcast SSID. See the FAQ for more information, or if the radio of the card is off again, see the FAQ for details.

off the NDISwrapper site
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)

---

### Post by Frijole on 2007-10-18
```
frijole@theBean:~$ sudo iwconfig wlan0 essid ESSID
[sudo] password for frijole:
frijole@theBean:~$ iwlist wlan0 scan
wlan0     No scan results

```


I know it broadcasts because I was using it previously

---

### Post by Oraclegol on 2007-10-18
hm have you tried doing the commands jsut with out the channel line

---

### Post by Frijole on 2007-10-18
```
frijole@theBean:~$ sudo ifconfig wlan0 down
[sudo] password for frijole:
frijole@theBean:~$ sudo iwconfig wlan0 mode managed
frijole@theBean:~$ sudo iwconfig wlan0 essid 'KLABO'
frijole@theBean:~$ sudo iwconfig wlan0 up
iwconfig: unknown command "up"
frijole@theBean:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:18:e7:28:0b:7d
Sending on   LPF/wlan0/00:18:e7:28:0b:7d
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

### Post by Oraclegol on 2007-10-19
its ifconfig wlan0 up not wlanconfig

---

### Post by Frijole on 2007-10-19
```
frijole@theBean:~$ sudo ifconfig wlan0 up
frijole@theBean:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     802.11b/g  ESSID:"KLABO"  
          Mode:Managed  Frequency=2.484 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   
          Retry:on   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by Frijole on 2007-10-19
are there any other options?

---

### Post by manbou on 2007-10-29
bump. any luck? can you see your network or other network? I'm wondering if ndiswrapper not working for this wireless card? Had problems with another wireless but I could see my network and other networks.

---

