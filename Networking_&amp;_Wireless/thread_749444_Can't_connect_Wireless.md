---
title: "Can't connect Wireless"
date: 2008-04-08
forum: Networking &amp; Wireless
---

### Post by anjpr on 2008-04-08
When I ran iwconfig in my laptop and home desktop I get the following message:

lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:"gpadillaco"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:0D:72:1F:EA:01   
          Bit Rate=1 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

When I run lscpi-v and lsmod I get the following information:
[ATTACH]65307[/ATTACH]

---

### Post by chili555 on 2008-04-08
What do you make of this?```
Link Quality=0/100
```This suggests your router or access point is either not working, not working correctly or too far away to get a usable signal. That is the first place I'd look. Are other machines able to connect to it wirelessly?

Any encryption on the router? WEP, WPA, Klingon. etc.? Have you confirmed the ESSID is correct with ```
sudo iwlist eth0 scan
```

---

### Post by anjpr on 2008-04-08
I'm not at home right now, as soon as I get there I'll check signal strength and iwlist.  Usually signal strength is around 60% at home.  I also have a WEP key at home and in the office, but my network manager keeps asking for the WEP key and doesn't connect.  I checked the key numbers in my Lynksys router and they are ok.  Still no clue what's the problem.

---

### Post by anjpr on 2008-04-08
This is what i get when running iwconfig and sudo iwlist eth0 scan:

[ATTACH]65343[/ATTACH]

---

### Post by chili555 on 2008-04-09
Your original post said **eth0** was the relevant wireless interface, yet your attachment says **ath0**. As well, your original post says the ESSID is **gpadillaco** and the attachment says **wifirouter**. Please try ```
sudo iwlist ath0 scan
``` and then we will get a lot closer to connecting.

Again, any encryption in place on your router?

---

### Post by anjpr on 2008-04-09
Thanks for the reply.  I have the same problem both at home and at the office.  I run ubuntu in my office using my laptop.  At home there is a desktop also running ubuntu.   eth0 is for my office laptop and ath0 is for my home desktop.  The essids are correct.

---

### Post by anjpr on 2008-04-09
I will check the desktop as soon as I get home tonight.

---

### Post by buried on 2008-04-09
NDISWrapper? have you tried that? If it's your last hope, I got my wi-fi working but randomly shutting down, logging off, restart etc.. lol

---

### Post by chili555 on 2008-04-09
> eth0 is for my office laptop and ath0 is for my home desktop. The essids are correct.Now what in your posts would have suggested that we are trying to diagnose two machines at once? We are certainly not getting useful information when we issue the wrong command to the wrong machine. 

This should be as easy as:```
sudo iwconfig ath0 essid <scan_verified_essid>
sud iwconfig ath0 key <encryption_key_if_any>
sudo dhclient ath0
```Substitute the correct details for the correct machine.

Your iwconfig both suggest the correct module, or driver, is in place and ready to go.

---

