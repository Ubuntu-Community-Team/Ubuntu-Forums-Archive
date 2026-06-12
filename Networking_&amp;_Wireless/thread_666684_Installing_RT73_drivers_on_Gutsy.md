---
title: "Installing RT73 drivers on Gutsy"
date: 2008-01-13
forum: Networking &amp; Wireless
---

### Post by wrathkeg on 2008-01-13
Hi.  I am trying to install the rt73 drivers to use my wireless card on a fresh install of Gutsy. The drivers compiled, and the iwlist command seems to find the network, but I can't seem to get any further. That is, I can't seem to actually get onto the internet and so on. I've checked various howtos, on here and elsewhere, but they don't seem to help.

Here's what I do (a bit long but you might need all these details of what works and what doesn't: if not, just skip to the bottom :) ). I plug the card in, and then this: 

```
sudo ifconfig wlan0 up
sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:19:5B:1D:97:14
                    ESSID:"NETWORK_NAME"
                    Mode:Managed
                    Channel:6
                    Encryption key:on
                    Bit Rates:0 kb/s
```

So far, so good: looks to be finding the network. So I move on to the Wireless Station Configuration section from the docs.

```
sudo iwconfig wlan0 mode managed
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid NETWORK_NAME
sudo iwconfig wlan0 key open
```

No problems, but it's here the problems seem to begin. I try to enter the WEP hex key, but it doesn't seem to like it:

```
sudo iwconfig wlan0 key XXXXXXXXXXXXXXXXXXXXXXXX
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "XXXXXXXXXXXXXXXXXXXXXXXX".
```

But I press on anyway, just in case the error wasn't fatal :)

```
sudo iwconfig wlan0
wlan0     RT73 WLAN  ESSID:"NETWORK_NAME"  
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:19:5B:1D:97:14   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:0000-0000-00
          Link Quality=83/100  Signal level:-56 dBm  Noise level:-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

This looks okay to me.   As far as I can tell, if I do the following then I should get an IP address:

sudo dhclient wlan0

But unfortunately all I get is this:

```
There is already a pid file /var/run/dhclient.pid with pid 5584
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:19:5b:35:14:c5
Sending on   LPF/wlan0/00:19:5b:35:14:c5
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

And then I can't connect to anything.  Has anyone had this specific problem?  If so, have you overcome it? Might it be related to the problems with the key? Or something else... I have looked at other how-tos for the RT73 drivers on here, but they don't seem to offer me any help.

TIA

WK

---

### Post by wrathkeg on 2008-01-15
anyone?

---

### Post by rustybronco on 2008-01-15
Not much help. "Error for wireless request "Set Encode" (8B2A)"
[http://www.linuxquestions.org/questions/linux-wireless-networking-41/wep-key-errors-393642/?highlight=%288B2A%29](http://www.linuxquestions.org/questions/linux-wireless-networking-41/wep-key-errors-393642/?highlight=%288B2A%29)
have you tried connecting  without encription"
Have you tried wep in hex? xx:xx:xx:xx:xx:xx on the router and nic? 

" Encryption key:0000-0000-00" what format is this? ascii?

---

### Post by wrathkeg on 2008-01-15
thanks for that.

actually, I have just read that (at least for some) my card (DWL G122) is supported out of the box on Gutsy, so I am going to try that route, rather than drivers.

And it's time to fess up: my error with the password was that I had misread a "1" as a "l". :oops:

---

### Post by rustybronco on 2008-01-15
Happens alot (I believe)  :) 
glad you got it.

---

