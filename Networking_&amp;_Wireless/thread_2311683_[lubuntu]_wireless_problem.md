---
title: "[lubuntu] wireless problem"
date: 2016-01-29
forum: Networking &amp; Wireless
---

### Post by guido96 on 2016-01-29
before the last upgrade i have no problem with wifi connession, now i can see my home connession but can't connect to it
someone help pls?:confused:

---

### Post by chili555 on 2016-01-29
Please check here: [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by guido96 on 2016-01-30
thw wireless info script doesn't work but 

```

guido@ubuntu:~/Scrivania$ sudo lshw -C network
[sudo] password di guido: 
  *-network:0             
       description: Ethernet interface
       product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 10
       serial: 00:11:d8:f2:58:b1
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.9 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:18 ioport:c800(size=256) memory:feaffc00-feaffcff
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: wlp2s4
       version: 05
       serial: 00:12:f0:6a:d9:63
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:feafe000-feafefff

```

---

### Post by chili555 on 2016-01-30
> **guido96 said:**
> thw wireless info script doesn't work but 

<snip>The wireless script isn't supposed to magically fix your wireless. It is supposed to gather all the diagnostics we need in just one try so that we can hopefully see what went wrong and suggest a fix. 

Please run the script and post the result. We need to see the details.

---

### Post by guido96 on 2016-01-31
yep i now that... the script doesn't run. it gives me the error 404 page not found when runned by terminal

---

### Post by chili555 on 2016-01-31
> **guido96 said:**
> yep i now that... the script doesn't run. it gives me the error 404 page not found when runned by terminalAre you connected to the internet by ethernet, tethered or whatever means possible?

It works perfectly for me.

---

### Post by guido96 on 2016-01-31
i'm connected with ethernet

---

### Post by chili555 on 2016-01-31
Please try one step at a time:```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info
```Does the script download or not? If not, what is the error? If so, proceed to the next step:```
chmod +x wireless-info
```And then the next:```
./wireless-info
```It should end with:> Results also archived in "/home/chili/[COLOR="#FF0000"]wireless-info.tar.gz[/COLOR]"Find the file and post it here as an attachment.

---

### Post by guido96 on 2016-02-01
```

guido@ubuntu:~/Scrivania$ wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info
--2016-02-01 13:18:04--  https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info
Risoluzione di github.com (github.com)... non riuscito: Connessione scaduta.
wget: impossibile risolvere l'indirizzo dell'host "github.com"


```

i don't know why.. web browsing and others internet features work

---

### Post by chili555 on 2016-02-01
That's weird!

Please try:```
wget https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info
```If that succeeds, then proceed as before.

---

### Post by guido96 on 2016-02-02
yep without the option it works but with doesn't

Code:
 	wget [https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info)

it works


 	Code:
 	wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) 
it not

---

### Post by chili555 on 2016-02-02
Wonderful. So now where is the report that it produced so that we may finally begin to diagnose and fix your problem?

---

### Post by guido96 on 2016-02-02
here

---

### Post by chili555 on 2016-02-02
> **guido96 said:**
> hereYou posted the script itself, not the resulting data.

Please make the script executable:```
chmod +x wireless-info
```And then run it so that it gathers all the information we need to see at one time and in one place:```
./wireless-info
```And then post the result.

---

### Post by guido96 on 2016-02-03
here

---

### Post by guido96 on 2016-02-04
I need to connect to "andrea"

---

### Post by chili555 on 2016-02-04
> Cell 03 - Address: <MAC 'ANDREA' [AC3]>
                    ESSID:"ANDREA"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    [COLOR="#FF0000"]Channel:0[/COLOR]
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=78/100  Signal level=-51 dBm  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 12ms ago
                    Extra: [COLOR="#FF0000"]Channel flags: INVALID[/COLOR] I suggest that you check the settings in the router. Please select a fixed channel; I suggest channel 1, 6 or 11.

I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor. Reboot and tell us if the connectivity is improved.

---

### Post by guido96 on 2016-02-05
I changed the domain from 00 to my country one's but it don't want connect to anyway. Yet channel flags invalid

---

### Post by chili555 on 2016-02-05
This is from your very latest wireless info:> Cell 07 - Address: <MAC 'ANDREA' [AC7]>
                    ESSID:"ANDREA"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    [COLOR="#FF0000"]Channel:0[/COLOR]
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=65/100  Signal level=-61 dBm  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 8288ms ago
                    Extra: [COLOR="#FF0000"]Channel flags: INVALID[/COLOR] I don't know what is set incorrectly in the router or what is possibly wrong; however, your wireless card is not going to connect to channel 0. 

The card itself says it does the following channels:> wlp2s4    11 channels in total; available frequencies :
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
          Channel 11 : 2.462 GHzChannel 0 is not among them. 

I strongly suspect, as I said before, that the solution is a setting in the router.

---

### Post by guido96 on 2016-02-05
Changed the channel in the router config. Now it works thanks a lot

---

