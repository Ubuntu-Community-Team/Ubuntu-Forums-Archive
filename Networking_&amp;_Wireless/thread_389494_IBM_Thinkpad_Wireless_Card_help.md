---
title: "IBM Thinkpad Wireless Card help"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by rs1996 on 2007-03-20
I am new to Linux and am enjoying my experience so far. However, I am having a very difficult time understanding how to get my wireless card to work. I have an IBM Thinkpad R40 with an Atheros internal wireless card. I think that Ubuntu has detected it since it shows in device manager, but I really have no idea how to get it to work. I am an experienced Windows user and would have no problem troubleshooting in that environment, but Linux is a whole new experience for me. Can someone point in the right direction?

---

### Post by chili555 on 2007-03-20
Let's start the easy way and, if necessary, take sterner measures later.

Open a terminal and type:```
sudo iwconfig
```You will find an interface that has a lot of information beside it; the others will say ' no wireless extensions.' It may, hopefully, be ath0.

Then type;```
sudo iwlist ath0 scan
```Make note of the ESSID of the wireless device you wish to connect to.

Go to System -> Administration -> Networking. Do you see a wireless interface? If so, highlight it and click Properties. I suggest checking Enable this connection, put in the ESSID you scanned and select DHCP. Click OK and see if you connect.

If any of this does not go as expected, post back.

---

### Post by rs1996 on 2007-03-20
Thanks Chili, will try and post back what I get.

---

### Post by rs1996 on 2007-03-20
When I type iwconfig, I get the following:

[B]ath0      IEEE 802.11a  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:0 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/B]

When I type iwlist ath0 scan, I get the following:
**ath0      Interface doesn't support scanning : Invalid argument**

Even though the card is 11a and b capable, I believe my router is only b/g. Yet after running the iwconfig command it displays IEEE 802.11a.

Anyway, what should I do now?

Thanks much,

---

### Post by rs1996 on 2007-03-20
Scratch the last part of that last post...

I ran the iwlist command w/o sudo and got the following:

I purposely changed the ESSID and MAC address...

[B]ath0      Scan completed :
          Cell 01 - Address: 00:XX:YY:ZZ:AB:11
                    ESSID:"XYZWireless"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=59/94  Signal level=-36 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:AA:BB:CC:CD:D2
                    ESSID:"ABCWireless"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=7/94  Signal level=-88 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
[/B]
I then went to Administration>Networking and I do see a Wireless interface. I did Enable. It went to Activating Interface and then nothing. How do I enter my WEP key?

---

### Post by chili555 on 2007-03-20
Back under Wireless Properties, where you entered your ESSID, you will see encryption method, select Hex. Put in your key in the 10- or 26-character key mode, NOT passphrase. Your key should look like this: 93c8530b2df51711bad5596f91 and not like this: ilovecoldbeer.

---

### Post by rs1996 on 2007-03-20
Thanks Chili. I can connect now...although in Networking Tools, the ath0 shows as an unknown interface despite having an IP address.

Will I need to reconfigure this every time I start my laptop?

Signing out for the night...will check back tomorrow.

Thanks for the help so far.

---

