---
title: "Can't get connected to public wifi"
date: 2008-02-06
forum: Networking &amp; Wireless
---

### Post by json25 on 2008-02-06
Can't get connected to public wifi, I got my wireless at home working fine using AES, but I can't connect to anything else ie Hotel Networks and my local library.  It sees the networks when I click on the network icon but the passphrases never work.  When I used windows in hotels or airports I remember it would autoconnect enough to get to the webpage where you paid for the service or entered a password, so far I can't get Linux to do that.  

Using Xubuntu and a Broadcom BCM4318 which obviously works since it works at home.  Any suggestions?

Thanks,
Jason

---

### Post by Andrew Stone on 2008-02-06
Is "roaming" mode turned on?  Also, are you running a secure network at home?

---

### Post by json25 on 2008-02-06
yes, roaming mode is on and at home I'm using WEP, I forgot I couldn't get the WPA AES to work either, so I had to degrade to WEP, the public network I'm trying to get on is also WEP.  

Another thing I forgot to mention, I'm on Xubuntu 64bit

---

### Post by faulkes on 2008-02-06
> **json25 said:**
> yes, roaming mode is on and at home I'm using WEP, I forgot I couldn't get the WPA AES to work either, so I had to degrade to WEP, the public network I'm trying to get on is also WEP.  


noted.

> 
Another thing I forgot to mention, I'm on Xubuntu 64bi


Shouldn't really matter, but I will keep it in mind.  

Could you send the output of the following:

```

sudo iwlist eth1 scan
-note replace eth1 with your own wireless interface if it is different

and

iwconfig

```

Also check /var/log/messages & /var/log/secure for anything that the driver/kernel may have
reported.

faulkes

---

### Post by json25 on 2008-02-06
This is what I have at home
eth1      Scan completed :
          Cell 01 - Address: 
                    ESSID:""
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=91/100  Signal level=-42 dBm  Noise level=-72 dBm
                    Extra: Last beacon: 52ms ago

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.462 GHz  Access Point:   
          Bit Rate=24 Mb/s   Tx-Power=19 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=65/100  Signal level=-50 dBm  Noise level=-72 dBm
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I took out the mac's and ESSID's, this is my system at home that works.  I'll have to scan again when I get to a public access point.  I'd like to try and get my WPA AES working at home though.

Thanks

---

