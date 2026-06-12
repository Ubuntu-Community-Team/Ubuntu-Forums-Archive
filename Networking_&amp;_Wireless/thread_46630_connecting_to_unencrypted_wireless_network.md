---
title: "connecting to unencrypted wireless network"
date: 2005-07-05
forum: Networking &amp; Wireless
---

### Post by dninja on 2005-07-05
I'm asking this on behalf of a friend so please excuse missing info.

He has just bought a wireless card and WAP and is trying to connect from his laptop to the WAP. Starting basically we tried with no encryption setup and just tried to use iwconfig to connect to the WAP. The problem is that it never actually connects. The commands we are trying are:

root@laptop:/var/log/kismet # iwconfig eth0 essid ourhouse channel 11 key open
root@laptop:/var/log/kismet # iwconfig
lo        no wireless extensions.

irda0     no wireless extensions.

eth0      IEEE 802.11b/g  Mode:Monitor  Frequency:2.442 GHz
          Access Point: 00:00:00:00:00:00   Bit Rate:54 Mb/s   Tx-Power=31 dBm
          Sensitivity=20/200
          Retry min limit:8   RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Link Quality:138  Signal level:0  Noise level:15
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

the wap is there and working, I can pick it up from my laptop using kismet. If he tried to connect to my encrypted WAP he can connect fine.

the WAP shows up in a scan

root@tasslehoff:/var/log/kismet # iwlist scanning
lo        Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth0      Scan completed :
          Cell 01 - Address: 00:0C:41:DD:ED:8E
                    ESSID:"ourhouse"
                    Mode:Master
                    Encryption key:off
                    Channel:11
                    Quality:188/0  Signal level:-94 dBm  Noise level:-26 dBm

So, as far as I can tell, the wireless card is ok, the WAP is ok and transmitting. Can anyone suggest what else we could check?

---

### Post by varunus on 2005-07-05
Try not entering the channel or the key and letting it autodetect.  Also, make sure to type in "sudo dhclient eth0" after using iwconfig, or else it won't work.

Because the AP shows up in iwlist scanning, you may be able to use:
sudo iwconfig eth0 ap 00:0C:41:DD:ED:8E

Good luck.

---

### Post by dninja on 2005-07-05
cheers, still no luck, I have tried the command below and then the same again without the essid and without the key params.

iwconfig eth0 essid ourhouse key off ap 00:0C:41:DD:ED:8E 

Still no luck, iwconfig doesn't seem to pick up the WAP:

eth0      IEEE 802.11b/g  Mode:Managed  Frequency:2.462 GHz  
          Access Point: 00:00:00:00:00:00   Bit Rate:0 kb/s   Tx-Power=31 dBm   
          Sensitivity=20/200  
          Retry min limit:8   RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:223
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

The WAP doesn't mention that it has a dhcp server on it so I would set the ip address by hand if not. I don't think I am connected well enough to be at the point of setting up IP's though.

Any more ideas?

---

### Post by alastair on 2005-07-05
Maybe try breaking it up i.e.

iwconfig eth0 ap 00:0C:41:DD:ED:8E
iwconfig eth0 essid "ourhouse"
iwconfig eth0 key open

Then check with "iwconfig" again.

---

### Post by dninja on 2005-07-05
Still no luck. I've just tried the same thing with the details for my WAP with my laptop and that fails too. If hotplug runs the scripts then the connection is setup ok, if I try to do it by hand then something seems to be missed.

I'm going to try replacing the iwconfig script with something that logs the comands then calls the real script. See what gets called.

Any other ideas while I'm trying that would be appreciated.

---

### Post by dninja on 2005-07-05
I've just replaced the binary and logged all params it it calls iwconfig 3 times:

Array
(
    [0] => /sbin/iwconfig
    [1] => eth0
    [2] => mode
    [3] => managed
)
Array
(
    [0] => /sbin/iwconfig
    [1] => eth0
    [2] => key
    [3] => <my key>
)
Array
(
    [0] => /sbin/iwconfig
    [1] => eth0
    [2] => essid
    [3] => kendermore
)

I've tried this replacing the essid with ourhouse and the key with open and off but no luck. I'm beginning to think that there is something wrong with his WAP.

Any last ideas anyone before I tell him to take it back?

---

### Post by funkydan2 on 2005-07-05
Why are you setting a value for the key?

If the Access Point has no encryption enabled, then all you should need to do is
sudo iwconfig eth0 essid ourhouse ap 00:0C:41:DD:ED:8E
sudo dhclient eth0

The "Network Monitor" tool should also help (if you're using gnome).  Click on it in the Gnome Panel, then click 'Configure'.  Select your wireless card and click 'Properties'.  Enter the SSID for your access point, make sure that the key is blank and DHCP is enabled.  Then activate your card.

---

