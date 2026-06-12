---
title: "Problems accessing internet through 2WIRE wireless dsl gateway"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by pmpedraza on 2007-03-19
Installed Ubuntu 6.10 and my only problems seems to be with wireless setup. I'll also admit that some of this has been self-inflicted - I'm certainly not an expert at Linux, but not necessarily a novice, just know enough to be dangerous and break things.:roll: 

I'm using the infamous Broadcom 4318 wireless card on a Compaq Presario v2000 latop. I THINK I have this set up correctly, but not after a lot of heartache. 

Under Administration->Networking, my wireless connection is configured correctly. I have my 'blue' wireless light on my laptop that is working/activated. I've also installed the Wifi-radar which recognizes all ap's in my area, including my own -> "2WIRE086".

When I try to connect through Wifi-radar I receive message "Working - Acquiring IP Address" and then nothing occurs other than the default message on the Wifi-radar screen which says "Connected to None ip(None)".

The following commands also seem to report the correct information:
$ iwlist scanning
$ iwconfig


Any thoughts, hints, tests, and suggestions would be appreciated to get me to the next level and have internet access.  :)

---

### Post by chili555 on 2007-03-19
> The following commands also seem to report the correct information:
$ iwlist scanning
$ iwconfig
Mind if we have a look-see? 

Any WEP or WPA? Any MAC filtering on the DSL modem or router? 

Let us know.

---

### Post by pmpedraza on 2007-03-19
WEP enabled, have the ten digit hex number entered under Network Setting-Wireless connection (also under Wifi-radar). No WPA as far as I know, not sure about MAC filtering.

A few other random things. I tried to force the connection with:
$ iwconfig eth1 ap xx:xx:xx:xx:xx 
The command worked but no joy.

Also this is configured under device 'eth1' which is what it installed as no 'wlan0'. Not sure if this is a factor but want to give you as much information.

---

### Post by chili555 on 2007-03-19
Mind if we have a look at: ```
iwconfig
sudo iwlist eth1 scan
```Thanks.

---

### Post by pmpedraza on 2007-03-19
**Output**

pmpedraza@pmpedraza-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  Nickname:"2WIRE086"
          Mode:Auto  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:25 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

pmpedraza@pmpedraza-laptop:~$ sudo iwlist eth1 scan
Password:
eth1      Scan completed :
          Cell 01 - Address: 00:0D:72:A3:19:71
                    ESSID:"Sacramento"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-67 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:14:95:53:C9:82
                    ESSID:"2WIRE086"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-60 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:0F:66:D7:58:00
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-85 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 00:30:BD:C2:80:C6
                    ESSID:"DM1"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-77 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

pmpedraza@pmpedraza-laptop:~$

---

### Post by chili555 on 2007-03-19
Please do:```
sudo iwconfig eth1 mode managed
sudo iwconfig eth1 ap 00:14:95:53:C9:82
sudo iwconfig eth1 key <your_double_checked_10_character_key_NOT_password>
sudo dhclient eth1
```

Let us know.

---

### Post by pmpedraza on 2007-03-19
Output:

[COLOR="Navy"]pmpedraza@pmpedraza-laptop:~$ sudo iwconfig eth1 mode managed

pmpedraza@pmpedraza-laptop:~$ sudo iwconfig eth1 ap 00:14:95:53:C9:82

pmpedraza@pmpedraza-laptop:~$ sudo iwconfig eth1 key 0716993967

pmpedraza@pmpedraza-laptop:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 13760
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:14:a5:2a:9d:74
Sending on   LPF/eth1/00:14:a5:2a:9d:74
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
pmpedraza@pmpedraza-laptop:~$ 
pmpedraza@pmpedraza-laptop:~$ [/COLOR]

---

### Post by chili555 on 2007-03-19
> No DHCPOFFERS receivedI hate it!

Let's see if these settings have made their way into /etc/network/interfaces. Let's also try to skip a round of posts. If these are NOT in interfaces, please sudo gedit to add under eth1.```
wireless-ap 00:14:95:53:C9:82
wireless-mode managed
wireless-key 0716993967
```Save and close. Restart networking:```
sudo /etc/init.d/networking restart
```and let us hear the news.

---

### Post by cckid on 2007-03-19
Hey there -
I had a similar problem and this is what I do to connect to my wireless router:
```
sudo iwconfig eth1 essid XXX
sudo iwconfig eth1 key open XXX
sudo iwconfig eth1 channel X
sudo dhclient eth1
```

Notice the "open" setting in the second line - this was key for me.

Good luck!

---

### Post by pmpedraza on 2007-03-19
Wow, complete success (almost). I added the requested lines to /etc/network/interfaces  -> no joy.

I added entry, see below, from *cckid* and this woked. The 'open' parameter seems to be key. 

Thank you both, *chili555* and *cckid* for hanging with me. I'm sending from my Compaq right now. My wife thanks you, she's wondering when I'm "getting off of my computer."

** Follow up question(s). I rebooted and wasn't able to connect without entering the commands again. How can I make this more permanent? Can I add to the /etc/network/interfaces  file?


[COLOR="Navy"]pmpedraza@pmpedraza-laptop:~$ sudo iwconfig eth1 essid "2WIRE086"
pmpedraza@pmpedraza-laptop:~$ sudo iwconfig eth1 key open 0716993967
pmpedraza@pmpedraza-laptop:~$ sudo iwconfig eth1 channel 6
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device eth1 ; Invalid argument.
pmpedraza@pmpedraza-laptop:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 5246
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:14:a5:2a:9d:74
Sending on   LPF/eth1/00:14:a5:2a:9d:74
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.1.254
bound to 192.168.1.66 -- renewal in 40422 seconds.
[/COLOR]

---

### Post by chili555 on 2007-03-19
Amend your interfaces file to add:```
auto eth1
```above all the other stuff, like this:```
auto eth1
iface eth1 inet dhcp
etc
etc
wireless-key open 0716993967
etc
```I wouldn't worry about channel. Reboot and you should be all good.

---

