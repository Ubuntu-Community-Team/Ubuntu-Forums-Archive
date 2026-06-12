---
title: "Network card but no associated access point"
date: 2007-02-20
forum: Networking &amp; Wireless
---

### Post by gbarron on 2007-02-20
Hi,

I am running ubuntu 6.10 on an AMD 64 and I am having a problem with my network card (Texas Instruments ACX 111 54Mbps Wireless Interface)

Firstly I would like to point out that I can connect to my network from a "wired" connection and this works fine, but I cannot connect to the same network via the wireless interface.

I have set the WEP details in the network manager and confirmed the details are correct.
I have opened tools such as KWifiManager and they say there is no network card available, but when I ask them to scan they use the wireless network card to find my access point.

I have run iwconfig and the details of my card are there, but they say there is no access point associated with it.

I am using the same details to connect to the access point from a win XP laptop and all is well so I assume that I have not configured something.  I have been through several "fix" guides, but I am having no luck.

Any help would be greatly appreciated.
Regards
Gary

---

### Post by ukripper on 2007-02-21
> **gbarron said:**
> Hi,

I am running ubuntu 6.10 on an AMD 64 and I am having a problem with my network card (Texas Instruments ACX 111 54Mbps Wireless Interface)

Firstly I would like to point out that I can connect to my network from a "wired" connection and this works fine, but I cannot connect to the same network via the wireless interface.

I have set the WEP details in the network manager and confirmed the details are correct.
I have opened tools such as KWifiManager and they say there is no network card available, but when I ask them to scan they use the wireless network card to find my access point.

I have run iwconfig and the details of my card are there, but they say there is no access point associated with it.

I am using the same details to connect to the access point from a win XP laptop and all is well so I assume that I have not configured something.  I have been through several "fix" guides, but I am having no luck.

Any help would be greatly appreciated.
Regards
Gary



Install wlassistant, try it with that.

---

### Post by gbarron on 2007-02-24
Hi,

I have installed wlassistant, nice tool by the way, but it still can't connect.  When the tool opens it has my wireless access point shown.  I then clicked on it and entered the details as I have on my windows machine.  From that point forward when I click the access point it simply says connection failed.

Regards
Gary

---

### Post by ukripper on 2007-02-26
> **gbarron said:**
> Hi,

I have installed wlassistant, nice tool by the way, but it still can't connect.  When the tool opens it has my wireless access point shown.  I then clicked on it and entered the details as I have on my windows machine.  From that point forward when I click the access point it simply says connection failed.

Regards
Gary



Make sure afetr putting connection details you tick on ASCII as well
also try using Auto DHCP instead of static IP incase you using one.

Stil if it doesn't work then paste output of the folowing command here:

$ sudo gedit /etc/network/interfaces

---

### Post by chili555 on 2007-02-26
If your key looks something like this:```
5b6d7378593c3045233e332547
``` then it's *hex* and not ascii. Ascii should look about like this: ```
[msxY<0E#>3%G
``` If it looks like this: ```
ilovecoldbeer
``` it's a passphrase that is used to generate a WEP key. I know of no way to get a passphrase to work in Ubuntu, but YMMV.

In my own case, my /etc/network/interfaces file includes this: ```
auto eth1
iface eth1 inet dhcp
wireless-essid GBR1
wireless-key 096cxxxxxxxxxxxxxx4afe 

```

I have obscured the middle of the key, but you can see the structure of the key is hex and works perfectly.

---

### Post by gbarron on 2007-03-11
Hi Guys,

Firstly, thanks for the help and advice.

I was advised (off site) that the issue may the 64 bit edition and so I have now formatted the partition and installed ubuntu 6.10 32 edition.  This is suffering from the same problem.

When I go in to the wireless detectors they say the signal strength is excellent.  The network manager lists the wlan0 device and I have configured the WEP key, which is hex.  The requested output from the command is:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid sky90641
wireless-key 9F1C3EE11C

When I try to connect to the access point it simply says connection failed.

Regards
Gary

---

### Post by chili555 on 2007-03-11
May we please see sudo iwconfig wlan0 and iwlist wlan0 scan? Thanks.

---

### Post by gbarron on 2007-03-17
Hi,

Here are the outputs requested.  I have removed all security to remove the WEP as an issue.

wlan0     IEEE 802.11b+/g+  ESSID:"STA0E98E0"  Nickname:"acx v0.3.21"
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:2 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Encryption key:off
          Power Management:off
          Link Quality=34/100  Signal level=8/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


iwlist output

wlan0     Scan completed :
          Cell 01 - Address: 00:18:4D:1B:F2:72
                    ESSID:"SKY90641"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=49/100  Signal level=28/100  Noise level=0/100
                    Encryption key:off
                    Bit Rates:54 Mb/s

---

### Post by chili555 on 2007-03-17
Here is your relevant section of /etc/network/interfaces: ```
auto wlan0
iface wlan0 inet dhcp
wireless-essid sky90641
wireless-key 9F1C3EE11C
```
I assume, if you have turned off security in the router, you have commented out the wireless key, Thus: ```
auto wlan0
iface wlan0 inet dhcp
wireless-essid sky90641
**#**wireless-key 9F1C3EE11C
```

Also, when you scanned it said the ESSID is: ```
wlan0 Scan completed :
Cell 01 - Address: 00:18:4D:1B:F2:72
ESSID:"SKY90641"
Mode:Master
etc.
``` SKY90641. Your interfaces file says you will only connect to an access point named sky90641. They are not the same. Please amend your interfaces file, save and close. Restart networking sudi /etc/init.d/networking restart and let us know.

---

### Post by gbarron on 2007-03-17
Hi,

I have made the changes suggested and run the scans again with the details below:

wlan0     IEEE 802.11b+/g+  ESSID:"SKY90641"  Nickname:"acx v0.3.21"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Encryption key:off
          Power Management:off
          Link Quality=47/100  Signal level=26/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

gbarron@gbarron-desktop:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:18:4D:1B:F2:72
                    ESSID:"SKY90641"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=47/100  Signal level=26/100  Noise level=0/100
                    Encryption key:off
                    Bit Rates:54 Mb/s

When I ran the restart command it said no dhcp offers received.  I was wondering if there was anything I may have missed.

Regards
Gary

---

### Post by chili555 on 2007-03-17
Your wireless interface is certainly stubborn today! Wake up, wlan0!

I suggest you try: ```
sudo iwconfig wlan0 ap 00:18:4D:1B:F2:72
sudo dhclient wlan0
```

On my own systems, I have seen dhclient work and ifup not and vice-versa. If dhclient fails, you might try: ```
sudo ifdown wlan0
sudo ifup wlan0
```

Let us know.

---

### Post by gbarron on 2007-03-17
Hi,

Not sure if it helps, but here is the wlan0 log from the network restart.

Listening on LPF/wlan0/00:12:0e:0e:98:e0
Sending on   LPF/wlan0/00:12:0e:0e:98:e0
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Regards
Gary

---

