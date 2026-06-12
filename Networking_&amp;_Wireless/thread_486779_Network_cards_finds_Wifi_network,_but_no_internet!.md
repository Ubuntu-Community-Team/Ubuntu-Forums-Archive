---
title: "Network cards finds Wifi network, but no internet!"
date: 2007-06-28
forum: Networking &amp; Wireless
---

### Post by Riel on 2007-06-28
SOLVED, TOPIC CAN BE CLOSED:

What was wrong, stupid for some, but not for me.

I contacted the adsl-modem to see if my WEPkey was ok.
I saw, it used a WPA key
I set it on the modem to WEP, entered a key, entered that key in Ubuntu network manager

and voila, my first wireless ubuntu post!

Silly maybe, but I really had no idea of WEP and WPA, i just used one (now i know, WPA) number.

--------------------------------------------------


hi all.

First of all, i'm so damn new to this, I can't do anything than annoy you guys with a new post. First of all, because I can't really find my exact problem (because the ESSID is found, it say's 'wireless active' and all of that, just internet doesn't work), I open this new Thread. Please, link me to another topic or just remove this one with a PM if this tread is not usefull to anyone.

What I know:

Wireless card is Ath0, I also have an Eth0.
Eth0 works with internet, perfectly! Then I just use the cable and plug it into the same router. But when I remove the cable, and set Ath0 on active, it finds and connects to the wifi-adsl-modem, but no internet.

Where should I look, i think it is about gataways or routes or something like that, but I really don't know where to start, or how this stoff works.

I cán use the terminal ;) so some commands like iwconfig i used that. But things like sudo (i know it's for doing something, but whát exactly??)


Thanx.

Anyway, with the cable, Ubunto works perfect! I starting my own project-office in one month, so I needed some software. I used openoffice lately and it was very satisfying. So now let's go all Linux!

I have a self-built PIII1600 mhz with some 512mb ram and a nvidia geforce 3Ti , not a new system but ok, I can make my proforma's on it :p

---

### Post by Riel on 2007-06-28
Some trying, maybe someone sees what's wrong?

Access Point: Not-Associated ??




riel@noname:~$ iwconfiglo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Frtizboxriel"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:9 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=45/94  Signal level=-51 dBm  Noise level=-96 dBm
          Rx invalid nwid:9476  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



riel@noname:~$ sudo iwconfig ath0 essid Fritzboxriel
riel@noname:~$ sudo iwconfig ath0 mode ad-hoc
Error for wireless request "Set Mode" B06
   ** SET failed on device ath0 ; Invalid argument.**


riel@noname:~$ iwconfig
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Fritzboxriel"  Nickname:""
          Mode:Managed  Frequency:2.442 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:9 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=34/94  Signal level=-61 dBm  Noise level=-95 dBm
          Rx invalid nwid:14122  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


riel@noname: wlanconfig ath0 create wlandev wifi0 wlanmode sta
wlanconfig: ioctl: Operation not permitted

riel@noname:





Does nothing, wants nothing. I tried a lot of commands out of tutorials...

---

