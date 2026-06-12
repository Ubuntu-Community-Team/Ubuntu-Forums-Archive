---
title: "Enabling WEP"
date: 2007-03-06
forum: Networking &amp; Wireless
---

### Post by thedarkleaf on 2007-03-06
Hi,

I'm another newbie to Ubuntu, just installed it out-of-the-box. My wireless card is a Linksys WMP54G, and im using ndiswrapper to use the windows driver on it. The card seems to be working fine, but i can't enable the encryption key... I was having no luck with the GUI networking, so i've spent a few hours looking through forums but having no luck.
Here's what i've been able to achieve:

```
sudo iwlist wlan0 scan
```
which lists the two access points in my network, both with ESSID "WLAN" and Encryption key: on. I guess this means that the kernel is talking to the wireless card fine, and the card is working.

Then when i do ```
iwconfig wlan0 
```i get
```
wlan0     IEEE 802.11g  ESSID:"WLAN"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          RTS thr:off   Fragment thr=2346 B 
          Encryption key:off
```

So i do ```
iwconfig wlan0 key xxxxxxxxxx
``` (where the x's are my key)
which returns nothing (presumably that means it worked?)
 
But then if i do ```
iwconfig wlan0
``` again i get 
```
wlan0     IEEE 802.11g  ESSID:"WLAN"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          RTS thr:off   Fragment thr=2346 B 
          Encryption key:off
```

I've also tried the following with no luck: 
```
iwconfig wlan0 key xxxx-xxxx-xx
```
```
iwconfig wlan0 key open xxxxxxxxxx
```
```
iwconfig wlan0 key restricted xxxxxxxxxx
```
```
iwconfig wlan0 key on
```

But every time the encription key seems to stay off.

Any suggestions?

Thanks.

---

### Post by chili555 on 2007-03-06
Perhaps this will help you: [http://www.ubuntuforums.org/showthread.php?t=172810&page=2](http://www.ubuntuforums.org/showthread.php?t=172810&page=2)

---

### Post by thedarkleaf on 2007-03-06
thanks...
I tried all the tips in that post but still no luck. I think the main problem i'm having is that no matter how I specify the encryption key it always says Encryption key:off.
I've now tried putting it in through the gui interface, through sudo gedit /etc/network/interfaces and through sudo iwconfig wlan0 key xxxxxxxxxx with or without restricted.

Here's what i got in the console:

simon@superman:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:12:BF:23:C1:16
                    ESSID:"WLAN"
                    Mode:Master
                    Frequency:2.437 GHz
                    Encryption key:on
                    Extra:tsf=0000000b83aef86c
          Cell 02 - Address: 00:16:B6:52:5A:EC
                    ESSID:"WLAN"
                    Mode:Master
                    Frequency:2.437 GHz
                    Encryption key:on
                    Extra:tsf=00000004a188942d

simon@superman:~$ sudo iwconfig wlan0 key 5e89xxxxxx
simon@superman:~$ sudo iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:"WLAN"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          
simon@superman:~$ sudo iwconfig wlan0 key 5e89xxxxxx restricted
simon@superman:~$ sudo iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:"WLAN"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          Encryption key:off


The encryption key is remembered in the GUI and is listed in the /etc/network/interfaces file but why does it always say Encription key:off???

So confused...

---

### Post by chili555 on 2007-03-06
Once you see it correctly in /etc/network/interfaces, I suggest you restart networking to get the file read in again. I'd try it with and without 'restricted.' sudo /etc/init.d/networking restart

I just noticed this: > two access points in my network, both with ESSID "WLAN"
I think, once we get the settings right, you will connect, but I fear, unless the WEP keys are different, your machine may disconnect and reconnect to the stronger signal.

---

### Post by thedarkleaf on 2007-03-07
hi, thanks for the comment...
I've tried what you said, restarting the network interface after setting the key with sudo iwconfig wlan0 key xxxxxxxxxx (with or without restricted) , but it still gives the same result. 

It gets to the wireless card and starts doing:

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval x

a few times and then gives up after five attempts saying 
No DHCPOFFERS Recieved. 
No working leases in persistent database - sleeping.

I believe this is because the wireless key is not set... and when that's finished if i try sudo iwconfig wlan0  i still get "Encryption key: off"

Not sure why, but it just doesn't want to let me turn encryption on...

---

### Post by chili555 on 2007-03-07
May we please see cat /etc/network/interfaces?

---

### Post by thedarkleaf on 2007-03-11
hi, sorry for the late reply (big weekend...)

here's sudo cat /etc/network/interfaces:

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


iface wmaster0 inet dhcp
wireless-essid WLAN
wireless-key 5e89xxxxxx


iface wlan0 inet dhcp
wireless-essid WLAN
wireless-key 5e89xxxxxx



i noticed that here there are two wireless interfaces detected, but there is definately only one physical wireless device in the computer. iwlist scan only works on wlan0, and sudo iwconfig returns the following:

lo        no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"WLAN"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          
eth0      no wireless extensions.

sit0      no wireless extensions.





so i think wlan0 is the one i shoudl be using? (but i have been tryign both for all above suggestions)

---

### Post by thedarkleaf on 2007-03-11
sidenote: is there any way to force the smilies not to come up??

---

### Post by chili555 on 2007-03-11
Please sudo gedit /etc/network/interfaces to add the parts in bold:
```
**auto wmaster0**
iface wmaster0 inet dhcp
wireless-essid WLAN
wireless-key 5e89xxxxxx

**auto wlan0**
iface wlan0 inet dhcp
wireless-essid WLAN
wireless-key 5e89xxxxxx
```
 and then sudo /etc/init.d/networking restart and let us know.

Smileys: The output of commands that you copy and paste usually have no space between : and o. Like key:off. If you want to be neat, you can put a space in: key: off. We are so used to seeing it and knowing what it means, we kind of read right through it.:) :) :)

---

### Post by thedarkleaf on 2007-03-12
hey thanks again for the advice, but unfortunately still no luck. when i restarted networking i got exactly the same as before, only now wmaster0 was trying to connect first saying "network down", then wlan0 was trying to connect as before with the multiple DHCPDISCOVERs and finally no DHCP offers found. 
I tried changing the order (ie putting wlan0 before wmaster0) but it didn't solve anything.

if i try a different linux distro, is it likely that i will have the same problem? cause if i can't get this working i guess that will have be the next option...

---

