---
title: "Ubuntu 16.04 Dell XPS 13 wifi speed limited 6Mb/s"
date: 2017-03-03
forum: Networking &amp; Wireless
---

### Post by bhmth on 2017-03-03
Hi,

i have the following Problem i have a new Dell XPS 13 and i am connected to my local wifi but the speed is imited to 6mb/s.

On my second Laptop also running ubuntu 16.04 i have 135Mb/s withe the same Wifi.

[http://paste.ubuntu.com/24101646/](http://paste.ubuntu.com/24101646/) here is the script

Thanks in advance for any help

---

### Post by Hadaka on 2017-03-03
Hi, Let's start by cleaning up some possible issues.
If possible..from a working wired connection please do..
```
sudo apt-get update
sudo apt-get dist-upgrade
```
*Power mgmt. should be OFF.
wlp58s0   IEEE 802.11abgn  ESSID:"SKYNET" 
Power Management on
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
*Chose only ONE manager for your network.
##### network managers ##################
Installed:
    NetworkManager
    Wicd

SKYNET <MAC 'SKYNET' [AC1]>  Infra 40 5200 MHz 54 Mbit/s 61 &#9602;&#9604;&#9606;_ WPA1 WPA2 yes *
```
*WPA2/AES is perfered not mix...please reconfigure the router setting.
```

```
*TKIP needs to be removed. Please reconfigure your router settings.
```
wlp58s0   Scan completed :
          Cell 01 - Address: <MAC 'SKYNET' [AC1]>
                    Channel:40
                    Frequency:5.2 GHz (Channel 40)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"SKYNET"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000127f1fcb72e
                    Extra: Last beacon: 3652ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

**  Region: Europe/Berlin (based on set time zone)
```
*Is this your correct region, if not please set your clock time
and zone correctly.
```

*If after completing these changes, you still have issues, post back
with a FRESH wireless diagnostic report...wireless-info
Thanks.

---

### Post by bhmth on 2017-03-03
since the laptop was brandnew i made a reset to default settings
after that still the same problems Wifi is connected and very slow and after a few minutes it stop working
new data here
different router and wifi now
[http://paste.ubuntu.com/24105082/](http://paste.ubuntu.com/24105082/)

---

### Post by Hadaka on 2017-03-03
Hi,resetting the computer and changing access points didnt help and most of the
same type problems are still there...
*I have no idea what this is...did you add this parameter ?
```
Parameters  locale=de_DE
```
open a terminal then Copy and Paste...
```
sudo iw reg set DE
sudo sed -i 's/=.*/=DE/' /etc/default/crda
```
*Power mgmt is still on and needs to be off....please do..
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
*Your access point has multiple spaces in the ssid name, Ubuntu prefers no spaces...
please rename or remove the spaces.
```
it hurts when IP
```
perhaps add underscore   it_hurts_when_IP

---

### Post by bhmth on 2017-03-04
> **Hadaka said:**
> Hi,resetting the computer and changing access points didnt help and most of the
same type problems are still there...
*I have no idea what this is...did you add this parameter ?
```
Parameters  locale=de_DE
```
open a terminal then Copy and Paste...
```
sudo iw reg set DE
sudo sed -i 's/=.*/=DE/' /etc/default/crda
```


nope didn't change a thing since the reset

> **Hadaka said:**
> 
*Power mgmt is still on and needs to be off....please do..
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```

if i run this command i get the following reply
```
sed: Kann /etc/NetworkManager/conf.d/ nicht bearbeiten: Das ist keine normale Datei

```

in english i think it means something like  
```
sed: Can not edit /etc/NetworkManager/conf.d/ : not a normal file

``` 
EDIT: i tried my other ubuntu Laptop with the wifi works perfectly

---

### Post by Hadaka on 2017-03-04
Hi,Did you include the  " * " in this command ?

if i run this command i get the following reply
 	Code:
 	sed: Kann /etc/NetworkManager/conf.d/ nicht bearbeiten: Das ist keine normale Datei 
Please Copy and Paste..
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
*If you get the same error message please do and post the output of..
```
cat /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
thanks

---

### Post by bhmth on 2017-03-04
Hey i tried the command no error message

i can connect to my wifi and browse the web ( slow) but as soon as i start a download it seems to crash...
newest paste
[http://paste.ubuntu.com/24112842/](http://paste.ubuntu.com/24112842/)

thank you very much for your help

---

### Post by jeremy31 on 2017-03-04
Post the result of ```
cat /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

These cards have issues with Power Management enabled, the last wireless report still showed it being on, you can check it with
```
iwconfig
```

---

### Post by bhmth on 2017-03-04
```
mai@mai-XPS-13-9360:~$ cat /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf[connection]
wifi.powersave = 2mai@mai-XPS-13-9360:~$ iwconfig
lo        no wireless extensions.


wlp58s0   IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
bnep0     no wireless extensions.
```

Here you go

EDIT:
i reconnected to my wifi

and i get this result

```
iwconfiglo        no wireless extensions.


wlp58s0   IEEE 802.11abgn  ESSID:"it hurts when IP"  
          Mode:Managed  Frequency:5.2 GHz  Access Point: 1C:C6:3C:AF:D9:8B   
          Bit Rate=6 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8   Missed beacon:0


bnep0     no wireless extensions.
```

Power Management is on again i dont get it if i run your command and it is still on

---

### Post by Hadaka on 2017-03-05
Hi, you state..
"Power Management is on again i dont get it if i run your command and it is still on" 

It is not "still on" you have only turned one connection off ...because
You have both your 2.4Ghz and 5.2GHz named exactly the same...'it hurts when IP'

<MAC 'it hurts when IP'[AC2]> Infra 11 2462 MHz 54 Mbit/s 100 &#9602;&#9604;&#9606;&#9608; WPA2 no        
<MAC 'it hurts when IP'[AC1]> Infra 40 5200 MHz 54 Mbit/s 84  &#9602;&#9604;&#9606;&#9608; WPA2 no

wlp58s0   IEEE 802.11abgn ESSID "it hurts when IP"
          Power Management off <<---

wlp58s0   IEEE 802.11abgn ESSID"it hurts when IP"  
          Mode:Managed  Frequency:5.2 GHz
          Power Management on <<---

The wifi card is roaming between two 2 connections...as shown in your dmesg of the report.
To stop the roaming you might want to consider renaming the connection...it_hurts_5G  it_hurts_2.4

Then turn power mgmt. off on the 5GHz connection with..
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
``` 
       
You have your Time zone set to DE per the wireless report..
DE    +5230+01322    Europe/Berlin    Germany (most areas)

Your system connection wants to set it to...
IE    +5320-00615    Europe/Dublin

Is your system originally from Dublin ?

---

### Post by bhmth on 2017-03-05
hi the timezone is set to Berlin, which is my actual timezone it was never set to another zone since it is brandnew

i ran your command and renamed my wifi also i switched the 5Ghz LAN off in the router no change except now the speed is at 1Mb/s on still not working

---

### Post by Hadaka on 2017-03-05
Hi, please post a fresh wire report so we may verify changes and look
for additional causes of your issue.
Thanks.

---

