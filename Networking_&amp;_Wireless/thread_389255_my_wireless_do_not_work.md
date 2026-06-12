---
title: "my wireless do not work"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by IsKall on 2007-03-20
I have an Intel Wireless Pro 2915, but it can't find any wireless connections,
this is what I get from iwconfig,

```

iskall@iskall:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:"Brusk"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

Does anyone know how I can fix this problem on edgy? (BTW this problem did not exist in dapper)

---

### Post by chili555 on 2007-03-20
> eth1 radio off  Is there a little switch on your laptop that got pushed in the wrong direction? Is there a setting in the BIOS you can enable or disable the wireless?

---

### Post by IsKall on 2007-03-20
eth1 radio off, did not work, it said "bash: eth1: command not found"

no the button is not pushed wrong, it dont have that type of button it is a pushin button . 

I dont think that "ability" exists in BIOS, will check.

---

### Post by IsKall on 2007-03-20
BIOS only had one option, and it was if I wanted to enable the Network, and is was on enable.

anyone?

---

### Post by chili555 on 2007-03-20
I did not ask you to issue a command 'eth1 radio off', I was merely pointing out that your iwconfig reports:```
eth1     [COLOR="Red"]radio off[/COLOR] ESSID:"Brusk"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```You will not get associated with an access point until you can turn the radio on.

---

### Post by IsKall on 2007-03-20
How do I do it in linux? Is it possible by command?

---

### Post by IsKall on 2007-03-20
I turned it on now, but still it cant find any wireless connections...

```

iskall@iskall:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"Brusk"  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


```

---

### Post by chili555 on 2007-03-20
What does ```
sudo iwlist eth1 scan
```tell us?

---

### Post by IsKall on 2007-03-20
Wow, this command made me find my own router! But why can't the Networking Application do that in System?
And whow do I connect to a wireless router?

the command wrote this.
```

iskall@iskall:~$ sudo iwlist eth1 scan
Password:
eth1      Scan completed :
          Cell 01 - Address: 00:14:C1:24:F8:D9
                    ESSID:"brusk"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=-12 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : TKIP CCMP 
                        Authentication Suites (1) : PSK  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : PSK  
                       Preauthentication Supported
                    Extra: Last beacon: 52ms ago
          Cell 02 - Address: 00:13:46:42:68:BC
                    ESSID:"Hemma"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=64/100  Signal level=-62 dBm  
                    Extra: Last beacon: 356ms ago
          Cell 03 - Address: 00:11:95:0C:BE:AA
                    ESSID:"default"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=33/100  Signal level=-80 dBm  
                    Extra: Last beacon: 2904ms ago
          Cell 04 - Address: 00:14:C1:0C:12:F8
                    ESSID:"USR5461KIM"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=33/100  Signal level=-80 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 228ms ago
          Cell 05 - Address: 00:17:3F:0D:E3:E2
                    ESSID:"belkin54g"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=56/100  Signal level=-67 dBm  
                    Extra: Last beacon: 88ms ago
          Cell 06 - Address: 00:15:E9:E1:1A:75
                    ESSID:"default"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=27/100  Signal level=-83 dBm  
                    Extra: Last beacon: 4372ms ago
          Cell 07 - Address: 00:0D:88:BC:E7:1F
                    ESSID:"KTH1946"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=29/100  Signal level=-82 dBm  
                    Extra: Last beacon: 3652ms ago



```

---

### Post by chili555 on 2007-03-20
The first thing I see is the ESSID you have in iwconfig is Brusk. When you scan to see what's out there, you see brusk. I would do the following command: ```
sudo iwconfig eth1 essid brusk
```

That's the easy part. The next thing we see is:```
IE: WPA Version 1                       Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP 
Authentication Suites (1) : PSK
```

This tells us the access point is encrypted with WPA. You will need to configure your computer to speak WPA. You might start here: [https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

---

### Post by IsKall on 2007-03-20
chili555, thank you for your help! I Really appreciate it! :)

---

### Post by IsKall on 2007-03-20
the connection works, but when I follewd

---

