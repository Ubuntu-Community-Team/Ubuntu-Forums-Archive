---
title: "radio off in Fujitsu 2060"
date: 2006-07-19
forum: Networking &amp; Wireless
---

### Post by maciek_m on 2006-07-19
Hi guys,
I'm a newbie and trying to start a wireless connection between my laptop (Fujitsu-Siemens V2060, Intel Pro wireless 2200) with my router.  The Fn+F10 key combination that works in XP seems not to work in Ubuntu. Although the "Networking" says that the wireless connection (eth1) is active the LED is dark and iwconfig seems to agree saying radio off:


eth1      radio off  ESSID:"nasz-DOMEK"
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power=off   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I tried "$sudo nano -w /etc/modules" and then "ipw2200 led=1", but nothing changed. The Fn+F10 key combination that works in XP seems not to work in Ubuntu. Can't find anything in the forum that looks like the solution to my problem.

Can anyone give me a clue, please?

---

### Post by x64Jimbo on 2006-07-19
The LED usually doesn't mean anything. If ifconfig says it's working, it's working. Forget the key combo. That stuff is built into the proprietary driver, which we don't use in Linux. 
To turn on your interface, do:
sudo ifconfig eth1 up
then you'll have to get a dhcp IP address if your router has dhcp
sudo dhclient eth1

---

### Post by maciek_m on 2006-07-19
thanks x64Jimbo, I did what you said and still have difficulties. I received this:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:13:ce:a9:52:05
Sending on   LPF/eth1/00:13:ce:a9:52:05
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


iwconfig still says "radio off" - does it mean anything?

how about other information here? Is it as it should?
eth1      radio off  ESSID:"nasz-DOMEK"
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power=off   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

And my router says the channel should be 6, while iwconfig says 0

---

### Post by x64Jimbo on 2006-07-19
Does your router have security turned on? If so, what kind?

---

### Post by maciek_m on 2006-07-19
Disregard everything I wrote below. The ... thing works without encryption. Thanks a lot for your help. I don't know what exactly helped (perhaps that I removed the WEP passphrase I put in the Networking table). Now, I will try to figure out how to make everything work with the encryption on. If you can recommend some useful reading for a newbie I will be soooooo thankfull.
____________________________________________________

Well, it did (WPA-PSK2, AES) but i turned it off and the answer to the "sudo dhclient eth1" command was the same (except for the interval numbers). In the meantime I managed to get a different iwconfig response (could the reboot into WinXP and turning on wireless there (Fn+F10) change that?):


eth1      unassociated  ESSID:"nasz-DOMEK"
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

But, as I said dhclient gives the same result. But then in the response:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:13:ce:a9:52:05
Sending on   LPF/eth1/00:13:ce:a9:52:05
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

My very limited knowledge of LAN expects the numbers to be rather 255.255.255.0. Am I right?

---

### Post by x64Jimbo on 2006-07-19
Well, I can tell you that I haven't been able to get WPA2 working at all in Linux. If you want to try out WPA-PSK (plenty secure if you pick a passphrase that's long and complex enough) you should look at a package called wpagui. It will manage your wpa_supplicant for you.

---

### Post by maciek_m on 2006-07-19
i

---

