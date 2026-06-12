---
title: "iwl3945 wireless monitor mode"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by Anomander on 2008-05-07
I see that Hardy has switched to the iwl driver for intel wireless chips.
I'm having trouble switching the driver into monitor mode, something that used to work ok with the old ipw drivers.
I'm trying to use wireshark to do some wireless sniffing.

When I try to flip the iwl3945 driver into monitor mode with:
sudo iwconfig wlan0 mode monitor

I get:
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Device or resource busy.

I know the driver is basically working because I can get it to scan with:
sudo iwlist wlan0 scanning.
That gives me results.

Anyone know anything about this driver and how to get it to sniff?

---

### Post by Cannaregio on 2008-05-07
Same problem here.
iwl3945 on a Amilo Fujitsu Siemens on Hardy
Monitoring (and kismet) only work if I boot with previous kernel 2.6.22-14 generic instead of new kernel 2.6.24-17.

Didn't find a solution (yet).

Anyone can help?

---

### Post by chili555 on 2008-05-07
> Anyone can help?Sure, chili can help. Please try:```
sudo ifdown wlan0
sudo iwconfig wlan0 mode monitor
```Then start up Kismet or whatever. When you are finished, do:```
sudo iwconfig wlan0 mode managed
sudo ifup wlan0
```

---

### Post by Anomander on 2008-05-07
No, that didn't work.
Same problem.
I also tried killing NetworkManager, thinking that might get in the way, but still no luck.

---

### Post by Cannaregio on 2008-05-07
> **chili555 said:**
> Sure, chili can help. Please try:```
sudo ifdown eth1
sudo iwconfig eth1 mode monitor
```Then start up Kismet or whatever. When you are finished, do:```
sudo iwconfig eth1 mode managed
sudo ifup eth1
``` 


chili you'r da man !!
your solution works perfectly (with [COLOR="Blue"]eth1[/COLOR] instead of [COLOR="#0000ff"]wlan0[/COLOR] in my case)
still I would like to know why my card did work well in Gutsy (auto setting in monitor mode when starting kismet and automatically back to managed when exiting) and now does require such gimmicks in Hardy...

thanks again

---

### Post by Mista 3lit3 on 2009-01-31
what's up HACKERZ? This is the leader of the 3lit3 Group ''LEAGONZ'' this is the first time ever in 10yrs i have ever replied to someone or gave help to but i had that same problem a few yrs back and i stayed up for 3dayz getting this to work right and i really want to help u hackerz out. This will work on any Unix BSD linux from redhat 7.0 thu fedora core 10.
'' PS feel free to email with any problem U may have :D ''

[root@XXXX XXXX ~]# sudo ifconfig wlan0 down
[root@XXXX XXXX ~]# sudo iwconfig wlan0 mode monitor 

Start up what ever program u're using from kismet to aircrack
when done using the programs of u're choice give this command and u're finished.
''WARNNINNNN'' MUST B LOGIN AS ROOT NOT su''
''WARNNINNNN'' IF U DO NOT USE THE sudo command ''
''WARNNINNNN'' YOU WILL NOT B ABLE TO RECONNECT''
''WARNNINNNN'' TO THE WIRELESS NETWORK WITH OUT REBOOTING U'RE SYSTEM ''


[root@XXXX XXXX ~]# sudo iwconfig wlan0 mode managed
[root@XXXX XXXX ~]# sudo ifconfig wlan0 up

---

