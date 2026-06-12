---
title: "Unstable Broadcom BCM43142 [14e4:4365] (rev 01) on Ubuntu 14.04"
date: 2016-02-01
forum: Networking &amp; Wireless
---

### Post by Y4kuzi on 2016-02-01
[EDIT] Fresh installation of Ubuntu 15.10.

Hello, 
 
I know that there are tons of topics out there regarding the same issue. 
None of the solutions work for me. I've been trying to fix this problem for a while now. 
Let me start by making clear that the WiFi works perfectly fine on both Windows 8.1 and Windows 10, 
so I'm positive we can rule out a hardware fault. 
 
I just did a fresh installation of Ubuntu 15.10 using this guide: 
[http://www.linuxandubuntu.com/home/dual-boot-ubuntu-15-04-14-10-and-windows-10-8-1-8-step-by-step-tutorial-with-screenshots](http://www.linuxandubuntu.com/home/dual-boot-ubuntu-15-04-14-10-and-windows-10-8-1-8-step-by-step-tutorial-with-screenshots)
 
Everything works perfect, no errors during installation. I did not install anything, except for updates. 
 
 
After the first boot, my WiFi works fine. However, at random times, it suddenly drops. 
This can be anywhere between 1 or 10 hours, and I have not seen a pattern. 
Also, when I close my laptop lid, my WiFi connection gets extremely slow/laggy even though I told 
it to do nothing in System Settings > Power > When lid is closed > Do nothing. 
But the latter might be fixed during the process. (unless I am missing something?)
 
 
I have included the output of the wireless info script below:
[http://pastebin.com/SD9G42Gy](http://pastebin.com/SD9G42Gy)

---

### Post by Hadaka on 2016-02-02
Hi, there are a few things you can adjust that will hopefully improve
your wifi connection.
From a working wired connection open a terminal crtrl/alt/t then copy and paste.
```
sudo apt-get update
sudo iw reg set NL
sudo sed -i 's/^REG.*=$/&NL/' /etc/default/crda
```
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install bcmwl-kernel-source
sudo rm -rf wl
sudo modprobe wl
```
Then please edit your network connection and set your IPV4 and IPV6 like the attached.
[ATTACH=CONFIG]267072[/ATTACH][ATTACH=CONFIG]267073[/ATTACH]
  Next access your router settings and i would suggest a different SSID than "Linksys" as there are
many with the same name, hidden and visable, and hopefully you set your own password. Your
wireless  report showed you were "roaming" so this should help. Also in the router settings please
remove TKIP and replace with WPA2 AES CCMP.
remove wired connection,boot and test wireless
thanks.

---

### Post by Y4kuzi on 2016-02-02
Thanks for the reply.

I cannot find any TKIP option in my router. Under what section should I look?

And in the meanwhile, what can I do about the WiFi dropping when I close my lid or when the screen turns "off"?
I already changed the power settings but it doesn't help, unless I am doing something wrong.

Also, I will save the SSID change for the last resort because there are more people currently connected to it, meaning they will drop
and need to re-enter the password etc. Does it help to set the BSSID in the network connection to the MAC address?

---

### Post by Hadaka on 2016-02-02
Hi the TKIP setting would be under security in your router's wireless
settings where you choose WEP..WPA/WPA2 WPA2 whatever, with the
exception of WEP any WPA2 choice without TKIP  should help. The closed
lid problem I would suggest to search 'ubuntu 14.04 wifi disconnect when lid closed'
Dig deep enough and you should find an answer. Yes setting the BSSID to the mac
address will also help.You stated your wifi drops from an hour to 10 hours at times,
this is very odd, with multiple users and the ssid of linksys and probably the default
router password of admin/admin,it is possible someone is controlling your router.
Other than what i have suggest,I dont have any other ideas.
good luck .

---

### Post by Y4kuzi on 2016-02-03
There is no TKIP setting in my router, so I think it is already disabled.
Security mode is set as "WPA2-Personal" and encryption as "AES".
There is another security mode I can pick, which is "WPA or WPA2-Personal". I will try that out but I highly doubt it will improve anything.

The odd thing is that it only happens on Ubuntu. On Windows and Android everything works just fine, no connection drops/lag.
Thanks again for the help.

---

### Post by Hadaka on 2016-02-03
Here is your ssid=linksys connection

```
wlan0     Scan completed :

           Cell 01 - Address: <MAC 'Linksys' [AC1]>
                     Channel:12
                     Frequency:2.467 GHz (Channel 12)
                     Quality=57/70  Signal level=-53 dBm  
                     Encryption key:on
                     ESSID:"Linksys"
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                               9 Mb/s; 12 Mb/s; 18 Mb/s
                     Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                     Mode:Master
                     Extra:tsf=0000000000000000
                     Extra: Last beacon: 20ms ago
                     IE: IEEE 802.11i/WPA2 Version 1
                         Group Cipher : [COLOR=#ff0000]TKIP[/COLOR]

                         Pairwise Ciphers (1) : CCMP
                         Authentication Suites (1) : PSK
                     IE: WPA Version 1
                         Group Cipher : [COLOR=#ff0000]TKIP[/COLOR]

                         Pairwise Ciphers (1) : [COLOR=#ff0000]TKIP[/COLOR]

                         Authentication Suites (1) : PSK
```
To view --do..
```
iwlist wlan0 scan
```
*Note windows/cell phone apps arent linux.
Next time your connection drops, power off your router then back on..
if it clears, you might want to consider restricting shared use to known mac addresses or accounts
and log them.

---

### Post by Y4kuzi on 2016-02-03
I understand, but because other devices experience no problems on the same router, I do not think it is a router issue.
But I don't know. I also see the TKIP in the terminal, but I can't find anything in the router, I triple checked.

Also some interesting thing I found today; when I USB tether my connection via my Android phone, the connection seems to be stable, even when the lid is closed.
I get an average of 30-40ms ping reply via IRC, and also 0% packet loss with 200 transmitted packets to Google.com. The Android device is connected to the same Linksys router.

---

### Post by Hadaka on 2016-02-03
If your Ubuntu machine runs fine...lid closed..whatever with the android phone tethered to the same router.
that proves the problem isnt with the ubuntu software but with the way you have your ac point configured.
the android phone doesnt use the same bits as the ubuntu machine does, because its not ubuntu linux.
you can clearly see in your report that TKIP is being used...only  you can change those settings.Sorry I
am not able to help you.

---

### Post by Y4kuzi on 2016-02-04
No problem. Thanks for all the help, I appreciate it :).
I keep this thread updated, hoping someone will reply with more answers.

I decided to try Ubuntu 15.10 so I did a fresh installation following with the latest upgrades.
The wireless connection seems to be improved, but the lid close problem still persists.
I  did a full factory reset on my router, but already changed all  necessary settings. I noticed the TKIP thing is gone in the  wireless-info.
Some experiments show that my connection stays alive when my screen turns off, and when I lock my screen.
It is only happening on lid close.

New wireless-info.txt: [http://pastebin.com/SD9G42Gy](http://pastebin.com/SD9G42Gy)

Some other info that might be useful; when I close the lid and re-open it, this is what shows in the **dmesg** and **syslog**:
[http://pastebin.com/c4BxAjeh](http://pastebin.com/c4BxAjeh)
I'm not sure if that is relevant for my WiFi connection, but I thought I'd include it anyway.

Hoping someone knows a fix :)

---

### Post by Hadaka on 2016-02-04
Hi, your latest wireless report shows you have bluetooth device being blocked.
```
2: hci0: Bluetooth
     Soft blocked: yes
```
Please do..
```
sudo rfkill unblock all
```
You also have a module loading that may or may not be involved with your "lid closed" issue
let's remove that and see if it makes a difference...please do..
```
sudo rm -rf hp_wmi
```
this is only good to the first boot so dont boot after you remove the module.  If it shows
an improvement we can make it permanant.
Here is some info on that module and the lid hinge for an hp.
[https://answers.launchpad.net/magick-rotation/+faq/1346](https://answers.launchpad.net/magick-rotation/+faq/1346)
report back if removing that module helps.
thanks.

---

### Post by Y4kuzi on 2016-02-04
Thanks for replying. I ran those commands, and then I tried to see if it improved by pinging google.com
Here is the output with the lid closed: [http://pastebin.com/nnA8KTe7](http://pastebin.com/nnA8KTe7)

---

### Post by Hadaka on 2016-02-04
Looks like the pings came and went, but the wifi stayed alive.
do you want to make that change to hp_wmi permanent?

---

### Post by Y4kuzi on 2016-02-04
As long as it doesn't have any negative side effects, sure. Unfortunately it didn't help anything with my WiFi though :(
I tried Googling some more, but none of the results are related to my issue. It's hard to understand why this issue occurs.

---

### Post by Hadaka on 2016-02-04
Hi, this removes the module hp_wmi and then blacklists it..
```
sudo modprobe -rf hp_wmi
echo "blacklist hp-wmi" | sudo tee -a  /etc/modprobe.d/blacklist.conf
```

should you want to restore it as before...this removes it from the blacklist file and restores it.
```
sudo sed -i '/^hp_wmi/ d' /etc/modprobe.d/blacklist.conf
sudo modprobe -v hp_wmi
```

---

