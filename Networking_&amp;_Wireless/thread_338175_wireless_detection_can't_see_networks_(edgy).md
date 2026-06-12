---
title: "wireless detection: can't see networks (edgy)"
date: 2007-01-14
forum: Networking &amp; Wireless
---

### Post by moon_dog on 2007-01-14
i'm on edgy and i can't see any wireless networks.  i can connect if i manually enter the name of the network, but this doesn't help me in cafes or airports when my system can't see the network and i don't know the network details.  does anyone have a fix for this?  i've done a search and haven't found anyone else with this problem.

---

### Post by maxamillion on 2007-01-14
$WLAN-CARD  will refer to what your machine sees the interface as (ei- eth1, wlan0, etc.)

```
sudo iwlist $WLAN-CARD scan
```

replace $WLAN-CARD with what your interface is called and post the results of that command here

---

### Post by moon_dog on 2007-01-16
Cell 01 - Address: 00:14:78:E9:64:FA
                    ESSID:"Jin0704"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:5
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=25/100  Signal level=-84 dBm  
                    Extra: Last beacon: 104ms ago
          Cell 02 - Address: 00:0D:08:01:34:C5
                    ESSID:"CTC"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=67/100  Signal level=-53 dBm  
                    Extra: Last beacon: 20ms ago
          Cell 03 - Address: 00:15:E9:0E:95:7C
                    ESSID:"default"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=41/100  Signal level=-76 dBm  
                    Extra: Last beacon: 92ms ago

---

### Post by corax on 2007-01-16
I think there is all the data you need :-). It is not a shiny GUI but the data is there...

you can connect to a wireless network with iwconfig

for example if you want to connect to the netwok "CTC" on your list you should type this:

```
sudo iwconfig $WLAN-CARD essid "CTC" key off channel 11 mode managed
```

if you have right to connect to that network (for example your WLAN card's MAC address is registered... ) then if you type:

```
iwconfig
```

you should see something like this:
```
eth1      IEEE 802.11g  ESSID:"CTC"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:0D:08:01:34:C5   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=87/100  Signal level=-42 dBm  Noise level=-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:1
```

it is from my command line my network card is eth1 and I replaced the network ESSID and Access Point 

if you see something similar (Look for Link Quality if that is not 0/100 then it should be good :-)  ) type this:

```
sudo dhclient $WLAN-CARD
```
then you will get your IP address 

you can check that (IP address) via ifconfig :

```
ifconfig $WLAN-CARD
```

I think that's all. If something is not working post it. :-)

bye & good luck

---

### Post by moon_dog on 2007-01-16
cool, but how do you get it working on the GUI? not that i don't use the command line, but i just hate it when things don't work as they're supposed to.  i always end up losing sleep cuz i try to make it work the way it's supposed to.

---

### Post by corax on 2007-01-16
I must disagree with you it works well ! You can connect to any network you want !
(My personal opinion is that the command line is much faster, easier, cleaner and configurable than any GUI ever will be :-) )

If you like GUI try these (I don't know anything about them because I don't use them :-) ):

for Gnome:
wifi-radar
network selector

for KDE:
Kwifimanager
Kwlan
kwireless monitor

all available through synaptic just do some digging :-)

good luck :-)

---

### Post by moon_dog on 2007-01-20
how do you enable/activate your wireless connection through the command line?  the above commands only work if i have already enabled my wireless connection through the GUI (system-->networking-->wireless connection), otherwise the above commands don't do anything.

---

### Post by corax on 2007-01-20
you can switch on your network card with :

```
sudo ifconfig eth1 up
```

(if eth1 is your wireless interface if not replace it with yours  :-) )

you can switch it off with :

```
sudo ifconfig eth1 down
```

hope this helps :-)

bye

---

### Post by moon_dog on 2007-01-29
i've come across an instance when i managed to connect to a network via iwconfig, but dhclient couldn't give me an ip.  it was an ad-hoc network.  what can i do in these instances?  also, a few times iwlist scan gave me a list of wireless networks but i couldn't connect to any of them (encryption key was off).  what gives?

---

### Post by moon_dog on 2007-01-30
bump

---

### Post by corax on 2007-01-30
If you make Ad-hoc networks and none of your computers is a DHCP server then you won't get any IP :-)

You have to give IP each machine manually for example:

```
sudo ifconfig eth1 192.168.1.X netmask 255.255.255.0
```

(X = an integer number between 2 and 254 must be different on each machine)

Sorry it is not clear for me you can't connect to an Access point or can't connect Ad-hoc ?

Despite an access point is open it can still use MAC filter and allow only certain ethernet cards to connect.

If it is ad-hoc I don't have any idea :-)

I made ad-hoc networks 3 only times every time managed to connect ... (I read through the manual of iwconfig) I can't remember exact details because all of the 3 was more then a half year ago :)

---

### Post by moon_dog on 2007-01-30
the network at the cafe is an ad-hoc network.

```
sudo iwconfig eth1 essid "xxx" channel xxx mode ad-hoc key off
``` would connect me but ```
sudo dhclient
``` wouldn't give me an IP address, it just said the there wasn't any DHCPOFFER.

i tried using mode managed but i couldn't connect to the network, only when i used mode ad-hoc.  so i assume it's an ad-hoc network.

---

### Post by spd106 on 2007-01-30
**sudo iwlist eth1 scan** will tell you if it is an ad-hoc network.

Ubuntu doesn't fall back to link-local addresses like Windows or OS X does, at least not until Feisty. So you will have to assign the address manually.

**sudo ifconfig eth1 169.254.x.x** should do it, replace the x with any number (1-255), just be sure not to use the same one as someone else. 

This won't be particularly useful though, unless you know the ip addresses of the machine you want to connect to. Turning on Service Discovery under the general tab in the network-admin capplet might help.

---

