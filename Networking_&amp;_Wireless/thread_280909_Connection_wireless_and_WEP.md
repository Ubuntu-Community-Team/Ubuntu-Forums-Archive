---
title: "Connection wireless and WEP"
date: 2006-10-20
forum: Networking &amp; Wireless
---

### Post by Klifi on 2006-10-20
Hi,
Brand new in the lynux world, so please compassion.

I have drapper ubuntu on a dell laptop. My connection is working great on wifi where ther is no protection, no WEP key to introduce.
So Wifi-card is recognized.
As soon there is a WEP key to use, there is no connection anymore. The computer can collect the IP adress but not more. 

I've tried with network manager (open/shared), with wifi radar, it's always the same.

On the same network if i disable the security everything is perfect, i put it back nothing is working.

Please help but with solution like on a cooking book step by step (absolut beginner)spending a lot of night trying to understand lynux.

Best regards

Klifi ](*,)

---

### Post by wieman01 on 2006-10-20
Please uninstall any kind of tool such as Wifi-Radar or NetworkManager and post the contents of this:
> sudo gedit /etc/network/interfaces
Then also run this command & paste the output:
> iwlist scan
After that I'll help you to set up WEP. I take it you are running DHCP?

---

### Post by xmastree on 2006-10-20
> **wieman01 said:**
> Please uninstall any kind of tool such as Wifi-Radar or NetworkManager and post the contents of this:

sudo gedit /etc/networking/interfaces


Just tried this, shouldn't it be:
sudo gedit /etc/**network**/interfaces

It certainly is on mine, there's no /etc/networking

---

### Post by Klifi on 2006-10-20
Hi,
Thank you very much for this so quick answer.

When I do:  
sudo gedit /etc/networking/interfaces

It open a new window but there is nothing written on it completely empty


When I do:    
iwlist scan

This is the answer :
lo        Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:0F:3D:4C:C9:78
                    ESSID:"animalis"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 22 24 36 48 54
                    Quality=58/100  Signal level=-73 dBm  Noise level=-73 dBm
                    Extra: Last beacon: 28ms ago

---

### Post by Klifi on 2006-10-20
I saw a bit to late the difference between the two message so if I do the correction and write 

sudo gedit /etc/network/interfaces

I have a new window open and this is written on it

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


iface eth1 inet dhcp
wireless-essid animalis
wireless-key 1234567890ABCDEF0987654321

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth1



And effectively I'm using DHCP.

---

### Post by wieman01 on 2006-10-20
> **xmastree said:**
> Just tried this, shouldn't it be:
sudo gedit /etc/**network**/interfaces

It certainly is on mine, there's no /etc/networking
D@#$! it. Of course you're right.

---

### Post by wieman01 on 2006-10-20
Ok, first of all let's do some housecleaning. Please update "interfaces" so that it looks like this (delete all remaining lines):
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid animalis
[COLOR="Blue"]wireless-key[/COLOR] [COLOR="Red"]your_wep_key[/COLOR]
Now the important bit is that the [COLOR="Red"]your_wep_key[/COLOR] holds your WEP key (apparently). Basically you have 2 options to enter it:

a. As plain text.
b. In a hexadecimal format.

If you choose a. then it should look like this (add the little **"s:"** to the front):
> [COLOR="Blue"]wireless-key[/COLOR] **s:**your_plain_text_key
The HEX key (b.) would have a similar format to the one  you have provided:
> [COLOR="Blue"]wireless-key[/COLOR] 1234567890ABCDEF0987654321
Please make sure that WEP is turned on (router) and that both keys MATCH. That done you can restart the network this way:
> sudo /etc/init.d/networking restart
Please again - post the output.

---

### Post by Klifi on 2006-10-21
Ok I've done the cleaning,lokk as you said now and it's an hexadecimal key so no s:.

After that I've done the restarting of the network as you said and this is the answer:

klemmi@XPSKLLY:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:15:c5:52:3e:f3
Sending on   LPF/eth0/00:15:c5:52:3e:f3
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 10.1.1.11 port 67
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:18:de:67:dd:5c
Sending on   LPF/eth1/00:18:de:67:dd:5c
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:15:c5:52:3e:f3
Sending on   LPF/eth0/00:15:c5:52:3e:f3
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 10.1.1.11
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.1.1.11
bound to 10.1.1.101 -- renewal in 234452 seconds.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:18:de:67:dd:5c
Sending on   LPF/eth1/00:18:de:67:dd:5c
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         
[ ok ]


Have a very nice day.

---

### Post by Klifi on 2006-10-21
I've forgotten to take the ethernet cable away before trying the restart so should i do it again ?

---

### Post by wieman01 on 2006-10-21
Can you tell me exactly what the router is set to? Perhaps even attach a snapshot of your router windows (browser) so that I can see what is going on. That may help.

_**EDIT:**_
Have you got any other tool installed? E.g. Firestarter, Wifi-Radar (we've had that, I know), NetworkManager? Something that could interfere?

---

### Post by wieman01 on 2006-10-21
> **Klifi said:**
> I've forgotten to take the ethernet cable away before trying the restart so should i do it again ?
Yeah... Pull the cable and restart.

---

### Post by tturrisi on 2006-10-21
You can also try using a hyphen after every 4 characters in the wep key.  Some routers and cards need the hyphen, depending on the driver for the card.

1234-5678-abcd-efgh

---

### Post by wieman01 on 2006-10-21
> **tturrisi said:**
> You can also try using a hyphen after every 4 characters in the wep key.  Some routers and cards need the hyphen, depending on the driver for the card.

1234-5678-abcd-efgh
Is that really so? Good to know.

---

### Post by Klifi on 2006-10-24
Hi 3 days without internet but I survived.
Thank's for all the answer.

I'm home with the same problem for a couple of day so i write all the configuration from home.
eth1 is the wifi on my computer
eth0 is the ethernet

when I do

sudo gedit /etc/network/interfaces

I have this

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


iface eth1 inet dhcp
wireless-essid la maison de la planche
wireless-key 85e9e661ee9ef049516b096787


I manually changed the wep key and the essid

I tried with the hyphen no change. The only difference I can see between work and home is that at home the wifi green light icon on the computer is no more blinking at home ??

And when I do 


klemmi@XPSKLLY:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:15:c5:52:3e:f3
Sending on   LPF/eth0/00:15:c5:52:3e:f3
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 10.1.1.11 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:15:c5:52:3e:f3
Sending on   LPF/eth0/00:15:c5:52:3e:f3
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.33 -- renewal in 33450 seconds.

this the answer with the ethernet cable

and 

klemmi@XPSKLLY:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:15:c5:52:3e:f3
Sending on   LPF/eth0/00:15:c5:52:3e:f3
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:15:c5:52:3e:f3
Sending on   LPF/eth0/00:15:c5:52:3e:f3
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database – sleeping.

Without the ethernat cable.

Ierase the network manager and wifi radar with the help of the synaptic paquet manager in system/administration. If I try to find thoses programms it's written not install.

There is only in System/Administration/network a place where I could write something about wep or so.

Here to screen capture about my router and my account

I hope it can help you. I really appreciate your help. Have a very good day.

---

### Post by twade on 2006-10-24
I was having similar issues with a BCM4311 card using ndiswrapper.  It would work using the /etc/network/interfaces file with WEP at home, but at work and for some other wireless networks I would get the same error as you.  I found that if I issued the commands:

```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 essid XXXXX
sudo iwconfig wlan0 key open XXXXXXXXXX
sudo ifconfig wlan0 up
```

and then waited a LONG time (many minutes) it magically connected.  It's a less than ideal solution, and might be an issue of the card not being fully supported, but at least I have wireless.

Good Luck!

---

### Post by xmastree on 2006-10-24
> **twade said:**
> and then waited a LONG time (many minutes) it magically connected.

Try:
**sudo dhclient wlan0**
which I believe forces it to look for a dhcp server, rather than waiting many minutes.

---

### Post by wieman01 on 2006-10-24
One question... Is your wireless device a wireless B or G one?

---

### Post by wieman01 on 2006-10-24
Please also do this for us:
> iwconfig
Then... What key are you using in "interfaces"? Is it this one?
> 85e9e66...
This should be the one. Perhaps you are using the wrong one...

---

### Post by Klifi on 2006-10-25
Hello,

Don't ask me how it happen but without changing things it's working wireless now ????????????

Here the result of iwconfig

klemmi@XPSKLLY:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"la maison de la planche"
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:00:C5:B3:20:41
          Bit Rate:11 Mb/s   Tx-Power:15 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=98/100  Signal level=-25 dBm  Noise level=-26 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


I will try now at work.
I really don't understand what has changed between yesterday and today :-k 



Anyway I thank again and will test the connection at the office and tell you more.

Have a very nice day

---

### Post by Erik. on 2006-10-25
Hi,
When i do iwconfig i see this:
root@ejp:~# iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


i do not have any connection.
I have installed ndiswrapper and the driver.
What do i need to do now to get my wirless internet to work?
I have a wep key into my router and i know the key..

---

### Post by wieman01 on 2006-10-25
> **Erik. said:**
> Hi,
When i do iwconfig i see this:
root@ejp:~# iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


i do not have any connection.
I have installed ndiswrapper and the driver.
What do i need to do now to get my wirless internet to work?
I have a wep key into my router and i know the key..
You need to let us more about your driver, the steps during the installation, etc. It's best if you opened up a new thread for your card.

---

### Post by twade on 2006-10-25
> **xmastree said:**
> Try:
**sudo dhclient wlan0**
which I believe forces it to look for a dhcp server, rather than waiting many minutes.

When I try this I get the same problem as when I use the /etc/network/interfaces method:

```
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
. . . etc . . . 
No DHCPOFFERS received.
```

I just searched the forums and there appear to be a few threads of a similar sort, I haven't found any solutions yet (other than to be patient) but I'll keep looking.

---

### Post by twade on 2006-10-25
> **xmastree said:**
> Try:
**sudo dhclient wlan0**
which I believe forces it to look for a dhcp server, rather than waiting many minutes.

Please disregard my post immediately above. This does indeed force it to get an ip quickly. Many thanks!

to summarize for me:
```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 essid XXXXX
sudo iwconfig wlan0 key open XXXXXXXXXX
sudo ifconfig wlan0 up
sudo dhclient wlan0
```

works and connects quickly when the /etc/network/interfaces file method using:
```
sudo /etc/init.d/networking restart
```
or the GUI equivalent method gives the:
```
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
... etc ...
No DHCPOFFERS received.
No working leases in persistent database – sleeping.
```
error.

---

### Post by tturrisi on 2006-10-25
another point to consider:
Spaces are allowed in SSID names.  Some wifi adapters will fail to connect to SSIDs because the names have spaces in them.  Best practice is to never use spaces in SSID or Network Names.

examples:

SSID: My Home WLAN should be My_Home_WLAN or similar.
Network Name:  ABC Office should be ABC-Office.

---

### Post by Klifi on 2006-10-26
Ok back again, it work just one day ........](*,) 

Here the things I notice. The day it work I was just before in the coffe with a non secured wireless network. In the coffe ok, at home turn on the computer, choose from the system/administration/network/ wifi connection eth1/ propriété the network with ssid la maison de la planche the wep key was automatically filled and here we go everything find.

Today nothing is working but I wasn't before in the coffe shop. 
An other thing is that when I'm in the coffe shop, on the icon network connection on the top left of the screen I have the choice between lo inactive or eth1 with the strength of the signal, I choose that one and at home before choosing my network, I can see it with no strength (yesterday) and today I couldn't choose the eth1 ??

So I'm now in the coffe shop (instead work not good) and connection find in the system/administration/network I choose on eth1 the network, delete the wep key which is written and let's surf.

So I done a few command line and here are the results.

[B]sudo gedit /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


iface eth1 inet dhcp
wireless-essid la maison de la planche
wireless-key ABC12345678901234567890DEF[/B]

Funny the essid name and the wep key is absolutely not the one I'm working with ??

And this ...
[B]
klemmi@XPSKLLY:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:00:C5:BF:FF:7D
                    ESSID:"5777 7671"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:7
                    Encryption key:off
                    Bit Rates:11 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11
                    Quality=83/100  Signal level=-51 dBm  Noise level=-51 dBm
                    Extra: Last beacon: 12ms ago

sit0      Interface doesn't support scanning.[/B]


And this ...

[B]
klemmi@XPSKLLY:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"5777 7671"
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:00:C5:BF:FF:7D
          Bit Rate:11 Mb/s   Tx-Power:15 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=84/100  Signal level=-51 dBm  Noise level=-52 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:7   Missed beacon:0

sit0      no wireless extensions.[/B]



The other thing i realize is that when I do a sudo / etc/init.d/networking restart, I have the feeling that there is absolutely no try on the eth1 but only on lo and eth0 ???

When I change manually my essid and wep key in the etc/network/interfaces, I don't think that the changes are effective ??





:confused:  It's better to die during night, because we can always learn something during the day. But some days are much longer than other.

Have a great day.

---

