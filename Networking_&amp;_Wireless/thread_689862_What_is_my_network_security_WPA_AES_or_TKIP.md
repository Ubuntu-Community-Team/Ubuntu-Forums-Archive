---
title: "What is my network security? WPA AES or TKIP?"
date: 2008-02-06
forum: Networking &amp; Wireless
---

### Post by letmein on 2008-02-06
So i have set my router to WPA2 with AES security and a 63 character of random characters....so i assume my network is configured as such...

However, when i do a "iwlist scan" on my network devices i see the following:

> wlan0     Scan completed :
          Cell 01 - Address: 
                    ESSID:"mynetwork"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:43/100  Signal level:-68 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


So my question is what gives? I specify WPA2 + AES on my router and here im seeing TKIP - is this something i should be concered about? I guess my 2nd question is...is there anything else i can impletment to make my network more secure?

---

### Post by wieman01 on 2008-02-07
Can you connect to your network?

I am surprised to see that it is recognized as TKIP. Have you perhaps enabled TKIP + AES?

There is no other security measure you could implement. WPA2 with AES and a sufficiently long pass-phrase is the best protection you can get. MAC filtering and turning off SSID broadcast are all bogus, so you have done the right thing. :-)

---

### Post by kevdog on 2008-02-07
You can run TKIP with WPA2 or AES.  AES is a slightly more efficient ciphering algorithm, however TKIP will work with some Linksys routers.  Possibly others.

---

### Post by wieman01 on 2008-02-07
Plus AES is considered more secure as TKIP was supposed to be an interim solution and a replacement for WEP to correct certain deficiencies. Both are RC4 based, but TKIP uses alternating encryption keys.

Use AES whenever possible, but I think that's what you are trying to do anyway.

---

### Post by wieman01 on 2008-02-07
By the way, you guys may want to read this:

[http://www.schneier.com/essay-064.html]("http://www.schneier.com/essay-064.html")

Bruce Schneier is my favorite crypto-analyst.

---

### Post by letmein on 2008-02-09
Yes, i've got it connected...just find it odd that my router is configured for AES and yes, my computer network settings are also set to AES and yet....TKIP is outputted through "iwlist scan" - anyway im sure no one in my neighborhood even knows what wpa2 is...let alone how to crack it.

Im using DD-WRT as my router firmware and see tabs to a bunch of other network configuration settings which i have no clue what they are, is there a way to specify the strength of my router signal...say, only available to computers 50 meters away?

---

### Post by kevdog on 2008-02-09
wieman01

That was a great link -- and written by the author of the twofish, blowfish ciphers.  What a treat!

---

### Post by wieman01 on 2008-02-10
> **letmein said:**
> Yes, i've got it connected...just find it odd that my router is configured for AES and yes, my computer network settings are also set to AES and yet....TKIP is outputted through "iwlist scan" - anyway im sure no one in my neighborhood even knows what wpa2 is...let alone how to crack it.

Im using DD-WRT as my router firmware and see tabs to a bunch of other network configuration settings which i have no clue what they are, is there a way to specify the strength of my router signal...say, only available to computers 50 meters away?
One setting I know of that controls the signal strength is "Overclocking". 
> 
DD-WRT -> Administration -> Management -> Overclocking
You can choose a lower frequency, but would have to do some testing. I have never done that myself.

---

### Post by wieman01 on 2008-03-05
Something I wanted to share with everyone:

[http://citp.princeton.edu/memory/]("http://citp.princeton.edu/memory/")
[http://citp.princeton.edu/memory/media/]("http://citp.princeton.edu/memory/media/")

**Morale:** Turn your computer off while you don't use it.

---

### Post by vitorio on 2008-03-16
> Quote from  [[COLOR=#d40000]**wieman01**[/COLOR]]("http://ubuntuforums.org/member.php?u=113534"):
[COLOR=Black]
I am surprised to see that it is recognized as TKIP. Have you perhaps enabled TKIP + AES?[/COLOR]Well, I'm having the same problem here too.  Here is my iwslist scan otuput:

eth1      Scan completed :
          Cell 01 - Address: XX:XX:XX:XX:XX:XX
                    ESSID:"MyESSID"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:9
                    Frequency:2.452 GHz (Channel 6)
                    Encryption key On
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=93/100  Signal level=-57 dBm  Noise level=-72 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 12ms ago

So the question remains the same?  What Cipher I'm using here?  My settings in DD-WRT are WPA2-PSK with AEP.  No mistakes here. And as far as I know DD-WRT is not supposed to fall back to TKIP in such setting independently of a client request.

Is it actually possible that iwlist scan provides incorrect output?  To me it looks like this is a case since I would rather expect a connection being refused by DD-WRT if my card tries using TKIP.

BTW. 

Actually in my case another weired thing is that I do connect to my router which is set as mentioned above and the connection is relable and stable.  But...

I never had to use anything mentioned in your tutorial. :-)

It just works after I upgrated from Feisty, where I used ndiswrapper with wpa_supplicant, to Gutsy, where I am using restricted bcm43xx driver.  The ndiswrapper module is still presented in my kernel but it is never loaded.  So, I think I'm using just an "out-of-box" Gutsy configuration.  Am I wrong here?

Thanks.

---

### Post by kevdog on 2008-03-16
According to imdano - the creator of WICD, certain chipset will report the incorrect pairwise and group cipher type -- many do not report it at all.  What is important is that you match your settings to that of the router, independent of what iwlist states

---

### Post by wieman01 on 2008-03-17
> **vitorio said:**
> Well, I'm having the same problem here too.  Here is my iwslist scan otuput:

eth1      Scan completed :
          Cell 01 - Address: XX:XX:XX:XX:XX:XX
                    ESSID:"MyESSID"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:9
                    Frequency:2.452 GHz (Channel 6)
                    Encryption key On
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=93/100  Signal level=-57 dBm  Noise level=-72 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 12ms ago

So the question remains the same?  What Cipher I'm using here?  My settings in DD-WRT are WPA2-PSK with AEP.  No mistakes here. And as far as I know DD-WRT is not supposed to fall back to TKIP in such setting independently of a client request.

Is it actually possible that iwlist scan provides incorrect output?  To me it looks like this is a case since I would rather expect a connection being refused by DD-WRT if my card tries using TKIP.

BTW. 

Actually in my case another weired thing is that I do connect to my router which is set as mentioned above and the connection is relable and stable.  But...

I never had to use anything mentioned in your tutorial. :-)

It just works after I upgrated from Feisty, where I used ndiswrapper with wpa_supplicant, to Gutsy, where I am using restricted bcm43xx driver.  The ndiswrapper module is still presented in my kernel but it is never loaded.  So, I think I'm using just an "out-of-box" Gutsy configuration.  Am I wrong here?

Thanks.
Maybe... maybe... your PC does not know/support AES and confuses it with TKIP. No idea. You could try TKIP to make sure it works at all.

---

### Post by wieman01 on 2008-03-17
> **kevdog said:**
> According to imdano - the creator of WICD, certain chipset will report the incorrect pairwise and group cipher type -- many do not report it at all.  What is important is that you match your settings to that of the router, independent of what iwlist states
Oh, OK. First time I hear it but then I saw Atheros chipsets confusing AES/TKIP with WEP-40 or something like that. You have seen it also I reckon. Very odd.

---

### Post by vitorio on 2008-03-17
Well, after a little investigation I think the problem is either in iwlist' or in my card reporting to iwlist incorrectly.

Here is what is kept in my DD-WRT router nvram parameter:

```
~ # nvram show | grep aes
wl_crypto=aes
wl0_wds0=*,auto,aes,psk2,MySSID,xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xxxx
wl0_crypto=ae

```

Here is output of 'sudo iwlist eth1 wpakeys':

```
user@hostname:~$ sudo iwlist eth1 wpakeys
eth1      2 key sizes : 40, 104bits
          4 keys available :
                [1]: xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xxxx (128 bits)
                     Address: 00:00:00:00:00:00
                     Algorithm: CCMP                 Flags: 0x00000001
                        tx-seq-valid
                [2]: xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xxxx (128 bits)
                     Address: 00:00:00:00:00:00
                     Algorithm: CCMP                 Flags: 0x00000001
                        tx-seq-valid
                [3]: xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xxxx (128 bits)
                     Address: 00:00:00:00:00:00
                     Algorithm: CCMP                 Flags: 0x00000001
                        tx-seq-valid
Error reading wpa keys (SIOCGIWENCODEEXT): Invalid argument
          Current Transmit Key: [1]
```

And here is output of 'sudo iwlist eth1 genie':

```
user@hostname:~$ sudo iwlist eth1 genie
eth1    
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

```

You can clearly see that the last 2 command outputs are in complete contradiction each with other (note CCMP vs TKIP reported).

In addition I had this rendig::

```
user@hostname:~$ sudo lsmod | grep aes
aes                    28608  3 
```

While both these rending nothing:

```
user@hostname:~$ sudo lsmod | grep ieee80211_crypt_tkip.ko
user@hostname:~$ sudo lsmod | grep ieee80211_crypt_tkip
```

That is, the only encryption related module loaded while I'm connected is 'aes' module.

Thus now I'm quite positive that I'm connecting using WPA2-PSK/AES.   And the problem is as stated above: either in iwlist or in bcm43xx reporting incorrectly.    Actually this line from iwlist output above probably supports the last suggested:

```
Error reading wpa keys (SIOCGIWENCODEEXT): Invalid argument
```

---

