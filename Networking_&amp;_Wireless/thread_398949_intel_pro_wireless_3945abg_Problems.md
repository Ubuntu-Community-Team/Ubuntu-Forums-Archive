---
title: "intel pro wireless 3945abg Problems"
date: 2007-04-01
forum: Networking &amp; Wireless
---

### Post by nessle on 2007-04-01
Hi

i am a very competent with windows but get very board with it so i have been playin with linux on and off, mostly suse. i am currently using and new to unbuntu 6.10 the problem i am having is my intel pro wireless 3945abg which is suppose to be supported is having problems. it can see my wireless networks but will not let me connect. i am using:

Ubuntu 6.10 with gnome
IBM thinkpad x60
intel pro wireless 3945abg
networking tools to connect (also tried kwifi manager and wifi radar)
connecting to a linksys Wireless-G router WRT54G
using a 64bit 10hex WEP key

it connects alright with my ethernet but not wireless which worked fine in suse 9 and open suse 10.2 couldnt find much help on this as the card is suppose to be supported any ideas anybody??

Thanks

Elliott

---

### Post by chili555 on 2007-04-01
Please go to System -> Administration -> Synaptic. Open Settings -> Repositories and check everything in sight. Close Settings and press Reload. This will take a few moments. Search for *linux-restricted-modules* and mark the box for installation. After this finishes, your ipw3945 should spring to life. Post back if you need more help.

---

### Post by nessle on 2007-04-01
hi i had all ready selected them when i was installing gdesklets and i have searched for linux-restricted-modules and it comes up with about a dozen in the search window, do i install all of them??

Thanks for the reply

---

### Post by chili555 on 2007-04-01
Please open a terminal and type *uname -r*. This gives you the version of your running kernel. Install the restricted-modules that matches. Synaptic will probably give you a couple of more and click apply and you should see your card.

FWIW, I am answering this on a T60, using ipw3945 connecting to a Linksys WRT54G!

---

### Post by angrymartian on 2007-04-02
I have the same wireless card and I went into the Synaptic manager and clicked all the things in repositories, then hit reload and i got a message that says " Could not download all repository indexes"

i suppose this is something that i am supposed to download off the internet or something? this is my first day on Ubuntu too so i dont even know what phrases like "Please open a terminal and type uname -r." even mean. can someone explain how i can get my drivers up and runnin

---

### Post by chili555 on 2007-04-02
Please go to Applications -> Accessories -> Terminal. At the blinking cursor, type *uname -r*. Press Enter. A string of text will return like on my machine:```
chili@LAPTOP60:~$ uname -r
2.6.17-11-generic

```2.6.17-11 is the version of my running kernel. 

You may, in fact, have the restricted modules installed now. In the same terminal, type:```
iwconfig
iwlist eth1 scan
```and post the results.

---

### Post by nessle on 2007-04-02
HI 

updated my changed from 2.6.17.11-generic to 2.6.17.11-386 but wireless will still not connect posting results from the commands you gave me:

nessle@Thinkpad-x60:~$ iwconfig
lo        no wireless extensions.

irda0     no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"AIRSPACE"  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:173   Missed beacon:0

sit0      no wireless extensions.

nessle@Thinkpad-x60:~$ iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:12:17:C7:AF:C8
                    ESSID:"Airspace"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:9
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=97/100  Signal level=-28 dBm  Noise level=-28 dBm
                    Extra: Last beacon: 520ms ago
          Cell 02 - Address: 00:14:7F:94:83:FA
                    ESSID:"BTHomeHub-E16C"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=38/100  Signal level=-86 dBm  Noise level=-86 dBm
                    Extra: Last beacon: 660ms ago
          Cell 03 - Address: 00:18:4D:01:03:06
                    ESSID:"SKY85670"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=65/100  Signal level=-68 dBm  Noise level=-68 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 688ms ago
          Cell 04 - Address: 00:14:7F:7C:56:94
                    ESSID:"BTHomeHub-77AE"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=28/100  Signal level=-92 dBm  Noise level=-92 dBm
                    Extra: Last beacon: 6028ms ago

nessle@Thinkpad-x60:~$ 

I am trying to connect to airspace if i open wifiradar it says i am already connected to it but over programs like kwifimanager says i am not and web pages does not load.

Thanks for all the help

---

### Post by chili555 on 2007-04-02
So far, we have AIRSPACE, airspace and Airspace. These are all different. Let's try, in a terminal:```
sudo iwconfig eth1 essid Airspace
sudo iwconfig eth1 ap 00:12:17:C7:AF:C8
```I notice the scan says the encryption key is on, so we'll also need:```
sudo iwconfig eth1 key <your_key_here>
```I assume you have the hex key, if it is ASCII, prepend it with *s:*.Then do:```
sudo dhclient eth1
```Please let us know.

---

### Post by nessle on 2007-04-02
Hi 

It now says connected and in connecting properties it says receveing and signal strength is full, it also lets me choose eth1 or eth0 which was available before but web pages still do not load and i also tried connecting to my router 10.0.0.2 and it will not connect to that either.

nessle@Thinkpad-x60:~$ sudo iwconfig eth1 essid Airspace
Password:
nessle@Thinkpad-x60:~$ sudo iwconfig eth1 ap 00:12:17:C7:AF:C8
nessle@Thinkpad-x60:~$ sudo iwconfig eth1 key ABAF068766
nessle@Thinkpad-x60:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:13:02:b8:83:08
Sending on   LPF/eth1/00:13:02:b8:83:08
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 10.0.0.2
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPNAK from 10.0.0.2
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPNAK from 10.0.0.2
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 10.0.0.2
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 10.0.0.2
bound to 10.0.0.8 -- renewal in 36845 seconds.

---

### Post by chili555 on 2007-04-02
Well, you are certainly connected:```
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 10.0.0.2
bound to 10.0.0.8 -- renewal in 36845 seconds.
```Let's try *sudo gedit /etc/modprobe.d/blacklist* to add this on its own line, at the end:```
blacklist  ipv6
```Reboot. Then, you might have to repeat the commands in my previous post to get connected again. Then do:```
ping -c3 10.0.0.2
ping -c3 www.google.com
```

---

### Post by nessle on 2007-04-02
I couldnt get the gedit /etc/modprobe.d/blacklist command to work but i realized from your post i didnt restart so i done that and a asif by magic i got a response from my ping and all is working.
thanks so much for the full i found linux rather complicated at first esp installing beryl and gdesklets etc. but the linux community is so helpfull!!! i still need to setup my sleep mode, fingerprint and bluetooth but that can be done another day my wireless was the main thing.

Once again thanks so much for your time and knowledge

---

### Post by tuaranoi on 2007-04-09
thanks for the answer chili555!! manage to get it done with your guide!

btw, if i goto other network, do i need to do it again? or it can automatic detect the network around?:KS

---

### Post by chili555 on 2007-04-09
If you want to roam from network to network, you will need to detect and direct your card to connect to the specific network you want. All this can be automated with wifi-radar, which is available in Synaptic, or Wicd [http://compwiz18.blackhole.cx/wicd/wb/](http://compwiz18.blackhole.cx/wicd/wb/) I prefer Wicd.

---

### Post by tuaranoi on 2007-04-09
ok. will try that out! thanks again!:popcorn:

---

### Post by tuaranoi on 2007-04-10
hi chili555,

i downloaded the software, it seems work fine, thanks!
but one more problem, when i restart ubuntu, my wifi cannot logon anymore, i have to do the steps you told in order to get it up again, is that right?

---

### Post by baxterdog on 2008-03-01
I have to move from roaming to a static IP all the time at work. (I'm trying to use only this one laptop to do everything!) When it runs as a server, to run python scripts, it needs to be a 10.xxx.xxx.1 machine, but I need to move to other lan's throughout the day and at home.

Simply said, All I do is change the settings, then;

<code>sudo ifdown eth0</code>
<code>sudo ifup eth0</code>

to reset as I move between the networks.

---

