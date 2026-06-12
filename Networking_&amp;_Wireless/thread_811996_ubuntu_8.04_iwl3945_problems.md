---
title: "ubuntu 8.04 iwl3945 problems"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by sander demeester on 2008-05-29
hello, aim just working with linux for 6 mounths now and i just instald ubuntu 8.04 and i have some problems with me wifi card for 2 mounth now and i realy want to solve it

here is all the info i could find:
wifi card:
 dmesg | grep Wireless
[   27.576663] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   27.682135] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection

kernel
 uname -r
2.6.24-17-386

if you need some more information about me system. just ask

i hope you can help me.
Sander

---

### Post by chili555 on 2008-05-29
We'd love to see these terminal commands:```
dmesg | grep wlan0
iwconfig
sudo iwlist wlan0 scan
```Thanks.

---

### Post by sander demeester on 2008-05-29
first, thanks for the fast replay. 
Here are the commands:

dmesg | grep wlan0
[   53.648432] ADDRCONF(NETDEV_UP): wlan0: link is not ready


iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sudo iwlist wlan0 scan
wlan0     No scan results

---

### Post by chili555 on 2008-05-29
Have you done:```
sudo apt-get install linux-backports-modules-hardy-generic
```What are your specific issues? Just unable to connect?

---

### Post by sander demeester on 2008-05-29
output command : 

sudo apt-get install linux-backports-modules-hardy-generic

[sudo] password for sander: 
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
Reading state information... Klaar
linux-backports-modules-hardy-generic is reeds de nieuwste versie.
The following packages were automatically installed and are no longer required:
  x11proto-kb-dev mesa-common-dev libxdmcp-dev xtrans-dev x11proto-core-dev
  libglu1-mesa-dev x11proto-input-dev libpthread-stubs0-dev libxau-dev
  libpthread-stubs0 libgl1-mesa-dev libx11-dev libxcb-xlib0-dev libxcb1-dev
Use 'apt-get autoremove' to remove them.
0 pakketten opgewaardeerd, 0 pakketten nieuw geïnstalleerd, 0 te verwijderen en 0 niet opgewaardeerd.


well, i cant see me wifi network (wpa protecetd) i cant configure me wireless network card, and i cant connect to it. i cant do anything with me wifi card. ive read about a bug in the kernel that iwl3945 module cant load, i tought it had something do to with that.

---

### Post by chili555 on 2008-05-29
> that iwl3945 module cant loadI doubt it, but I guess anything is possible. Let's check to be sure:```
lsmod | grep iwl3945
```If a lot of text comes back, like this:```
iwl3945                93940  0 
iwlwifi_mac80211      219108  1 iwl3945
led_class               6020  1 iwl3945
```Then it's loaded.

Do you have an active wired ethernet connection? Network Manager will not activate wireless, if wired is available: [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager) If you reboot with the wire detached, is your wireless available to be configured?

May we please see:```
sudo cat /var/log/messages | grep switch
```> i have some problems with me wifi card for 2 mounth nowPlease do not wait two months before you consult us. We are here to help.

---

### Post by jli4000 on 2008-05-29
i have the exactly same problem with same outputs from those commands you have given in this thread, except for
sudo iwlist wlan0 scan
i got list of all the wlans here that i can see with vista but not in ubuntu..

[http://ubuntuforums.org/showthread.php?t=812058](http://ubuntuforums.org/showthread.php?t=812058) i dont have network cable on when i boot so it can't be that either



```
jli@tibidabo:~$ lsmod | grep iwl3945
iwl3945                93940  0 
iwlwifi_mac80211      219108  1 iwl3945
led_class               6020  2 iwl3945,acer_acpi

jli@tibidabo:~$ sudo cat /var/log/messages | grep switch
May 28 22:50:05 tibidabo kernel: [   19.606037] SMP alternatives: switching to UP code
May 28 22:50:05 tibidabo kernel: [   20.010966] SMP alternatives: switching to SMP code
May 28 22:50:05 tibidabo kernel: [   20.276191] ACPI: EC: non-query interrupt received, switching to interrupt mode
May 28 23:14:52 tibidabo kernel: [   20.410077] SMP alternatives: switching to UP code
May 28 23:14:52 tibidabo kernel: [   20.838349] SMP alternatives: switching to SMP code
May 28 23:14:52 tibidabo kernel: [   21.104263] ACPI: EC: non-query interrupt received, switching to interrupt mode
May 28 23:15:25 tibidabo kernel: [   69.783339] Kill switch must be turned off for wireless networking to work.
May 28 23:15:32 tibidabo kernel: [   70.204929] Kill switch must be turned off for wireless networking to work.
May 28 23:17:16 tibidabo kernel: [   92.004292] Kill switch must be turned off for wireless networking to work.
May 29 19:40:36 tibidabo kernel: [   30.509626] SMP alternatives: switching to UP code
May 29 19:40:36 tibidabo kernel: [   30.924635] SMP alternatives: switching to SMP code
May 29 19:40:36 tibidabo kernel: [   31.223253] ACPI: EC: non-query interrupt received, switching to interrupt mode
May 29 20:26:42 tibidabo kernel: [  588.502898] Kill switch must be turned off for wireless networking to work.
May 29 21:42:36 tibidabo kernel: [ 2147.489908] Kill switch must be turned off for wireless networking to work.
May 29 21:42:55 tibidabo kernel: [ 2166.616339] Kill switch must be turned off for wireless networking to work.
May 29 21:46:49 tibidabo kernel: [ 2387.439492] Kill switch must be turned off for wireless networking to work.
May 29 22:20:01 tibidabo kernel: [   79.294613] SMP alternatives: switching to UP code
May 29 22:20:01 tibidabo kernel: [   79.695538] SMP alternatives: switching to SMP code
May 29 22:20:01 tibidabo kernel: [   79.994650] ACPI: EC: non-query interrupt received, switching to interrupt mode
May 29 23:40:59 tibidabo kernel: [   18.084351] SMP alternatives: switching to UP code
May 29 23:40:59 tibidabo kernel: [   18.479321] SMP alternatives: switching to SMP code
May 29 23:40:59 tibidabo kernel: [   18.742769] ACPI: EC: non-query interrupt received, switching to interrupt mode
May 30 00:04:57 tibidabo kernel: [   14.963223] SMP alternatives: switching to UP code
May 30 00:04:57 tibidabo kernel: [   15.360066] SMP alternatives: switching to SMP code
May 30 00:04:57 tibidabo kernel: [   15.625412] ACPI: EC: non-query interrupt received, switching to interrupt mode
May 30 00:07:31 tibidabo kernel: [   13.490163] SMP alternatives: switching to UP code
May 30 00:07:31 tibidabo kernel: [   13.900366] SMP alternatives: switching to SMP code
May 30 00:07:31 tibidabo kernel: [   14.200233] ACPI: EC: non-query interrupt received, switching to interrupt mode
May 30 00:12:51 tibidabo kernel: [   14.028755] SMP alternatives: switching to UP code
May 30 00:12:51 tibidabo kernel: [   14.437382] SMP alternatives: switching to SMP code
May 30 00:12:51 tibidabo kernel: [   14.739415] ACPI: EC: non-query interrupt received, switching to interrupt mode
```

---

### Post by jli4000 on 2008-05-29
i just notice that 
```
sudo apt-get install linux-backports-modules-hardy-generic
```
made the kill switch led work as was promised somewhere, but that was all.

```
sudo iwlist wlan0 scan
```
lists all networks and infos, but i cant find a way to see any network in the network manager or anywhere else so i could connect to them

---

### Post by chili555 on 2008-05-29
Do you see your wireless interface in System -> Administration -> Network after you unlock? Is the Enable this connection box checked? It needs to be *unchecked* for Network Manager to manage your connection.

---

### Post by jli4000 on 2008-05-29
> **chili555 said:**
> Do you see your wireless interface in System -> Administration -> Network after you unlock? Is the Enable this connection box checked? It needs to be *unchecked* for Network Manager to manage your connection.

i noticed that. i've tried with roaming mode (wireless interface unchecked) and with configuring my wlan by checking the interface and giving ssid/password there. neither works..

---

### Post by sander demeester on 2008-05-30
tanks for the help
and no when the i connect to me router with or without cable i still cant configure my wifi.
and in network settigns the wireless conection stands on : this network interface is not configure
here is the ouput of the commands:

 sudo cat /var/log/messages | grep switch
[sudo] password for sander: 
May 28 13:30:21 green kernel: [   37.363184] SMP alternatives: switching to UP code
May 28 13:30:21 green kernel: [   37.762283] SMP alternatives: switching to SMP code
May 28 13:30:21 green kernel: [   40.686118] ACPI: EC: non-query interrupt received, switching to interrupt mode
May 28 13:34:17 green kernel: [   13.024475] SMP alternatives: switching to UP code
May 28 13:34:17 green kernel: [   13.423120] SMP alternatives: switching to SMP code
May 28 13:34:17 green kernel: [   16.353629] ACPI: EC: non-query interrupt received, switching to interrupt mode
May 28 15:08:39 green kernel: [   23.872774] SMP alternatives: switching to UP code
May 28 15:08:39 green kernel: [   24.272221] SMP alternatives: switching to SMP code
May 28 15:08:39 green kernel: [   27.194508] ACPI: EC: non-query interrupt received, switching to interrupt mode
May 28 15:44:39 green kernel: [   11.017673] SMP alternatives: switching to UP code
May 28 15:44:39 green kernel: [   11.416615] SMP alternatives: switching to SMP code
May 28 15:44:39 green kernel: [   14.336810] ACPI: EC: non-query interrupt received, switching to interrupt mode
May 28 16:05:30 green kernel: [   10.883805] SMP alternatives: switching to UP code
May 28 16:05:30 green kernel: [   11.283334] SMP alternatives: switching to SMP code
May 28 16:05:30 green kernel: [   14.209094] ACPI: EC: non-query interrupt received, switching to interrupt mode
May 28 17:16:00 green kernel: [   20.165089] SMP alternatives: switching to UP code
May 28 17:16:00 green kernel: [   20.564942] SMP alternatives: switching to SMP code
May 28 17:16:00 green kernel: [   23.493626] ACPI: EC: non-query interrupt received, switching to interrupt mode
May 28 17:21:58 green kernel: [   18.411163] SMP alternatives: switching to UP code
May 28 17:21:58 green kernel: [   18.811842] SMP alternatives: switching to SMP code
May 28 17:21:58 green kernel: [   21.735157] ACPI: EC: non-query interrupt received, switching to interrupt mode
May 28 21:52:56 green kernel: [   11.382632] SMP alternatives: switching to UP code
May 28 21:52:56 green kernel: [   11.782419] SMP alternatives: switching to SMP code
May 28 21:52:56 green kernel: [   14.722086] ACPI: EC: non-query interrupt received, switching to interrupt mode
May 28 22:15:08 green kernel: [   21.194554] ACPI: EC: non-query interrupt received, switching to interrupt mode
May 28 22:32:40 green kernel: [   30.373474] ACPI: EC: non-query interrupt received, switching to interrupt mode
May 29 18:19:43 green kernel: [   24.530336] ACPI: EC: non-query interrupt received, switching to interrupt mode
May 29 20:42:58 green kernel: [   22.385175] ACPI: EC: non-query interrupt received, switching to interrupt mode
May 29 20:55:21 green kernel: [   13.365841] ACPI: EC: non-query interrupt received, switching to interrupt mode
May 30 16:14:04 green kernel: [   21.267806] ACPI: EC: non-query interrupt received, switching to interrupt mode
sander@green:~$ 

and : 

lsmod | grep iwl3945
iwl3945                90228  0 
iwlwifi_mac80211      215652  1 iwl3945

and i have network manager running.

and again thanks!

---

### Post by jli4000 on 2008-05-30
ok, it's working now. installing wicd and removing the default network admin did the trick (i suspected this since iwlist wlan0 scan could see all the networks) 

i think you, chili, suspected in some thread that the problem could be in the netadmin.. although when it works for someone and for someone not.. it might be just partial truth. i sure hope it'll be found..

thanks for all help.

sander: check this [http://ubuntuforums.org/showthread.php?t=765647&page=3](http://ubuntuforums.org/showthread.php?t=765647&page=3)

---

### Post by sander demeester on 2008-05-30
ok so i removed  network manager and instald Wicd. still the same. he cant see any wireless networks at all.

---

### Post by chili555 on 2008-05-30
What does:```
sudo iwlist wlan0 scan
```tell us? If you do:```
sudo rmmod -f iwl3945
sudo modprobe iwl3945  disable_hw_scan=1
```and then you run scan again, does anything change?

---

### Post by sander demeester on 2008-05-30
first scan : 
sudo iwlist wlan0 scan
wlan0     No scan results

i execute the commands

second scan :
sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down


a edit : 

i did ifconfig wlan0 up
and third scan is : 
wlan0     Scan completed :
          Cell 01 - Address: 00:18:39:2B:2D:3A
                    ESSID:"Lierman"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=96/100  Signal level=-30 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=0000008c12bd8161
          Cell 02 - Address: 00:11:50:4E:37:15
                    ESSID:"Maurice"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=54/100  Signal level=-76 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000002f46178c188

but when i reboot its just like the first scan, but when i execute the commands again i can see me wifi network with iwlist scan and with Wicd Manager

---

### Post by chili555 on 2008-05-30
I assume 'Lierman' is your router, since it's signal level is the highest. Can you now connect through Network Manager, supplying your WPA details? 

You can make the change permanent with:```
sudo su
echo -e 'alias wlan0 iwl3945 \noptions iwl3945 disable_hw_scan=1' > /etc/modprobe.d/iwl3945
reboot
```

---

### Post by sander demeester on 2008-05-30
ok, the changes are permanent, and when i reboot i can see my wifi network. and yes lierman is me router :)

i use Wicd as network manager but i cant connect to it. i fill in the correct details for my wpa.

what should i do now?
Sander

---

### Post by sander demeester on 2008-05-31
does some one know how i can connect?

---

