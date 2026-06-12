---
title: "[SOLVED] WPA with pairwise and group ciphers - WEP-40"
date: 2008-03-04
forum: Networking &amp; Wireless
---

### Post by ittiam on 2008-03-04
I see this strange thing with WPA version using WEP-40 as pairwise and group ciphers which I think should be TKIP. I tried googling about it and found that there is some problem with the AP but am not able to get clear idea as what problem it is.

It works when i use knetworkmanager but when i try setting it up from command line using wpa_supplicant it does not work. Yea I guess the problem is with wpa_supplicant.conf but in knetworkmanager also the encryption is set to WPA personal. Can anyone help me as how can i get it working using wpa_supplicant from the command line?

I am using Broadcom wireless driver.
thanks

```
Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:84/100  Signal level:-42 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK

```

my wpa_supplicant.conf
> ctrl_interface=/var/run/wpa_supplicant

network={
       ssid="MySSID"
       scan_ssid=1
       proto=WPA
       key_mgmt=WPA-PSK
       group=CCMP TKIP
       pairwise=CCMP TKIP
       psk=mypsk_generated_using_wpa_passphrase
}
~

---

### Post by kevdog on 2008-03-04
Try removing CCMP from the interface file.

ap_scan=1
ctrl_interface=/var/run/wpa_supplicant 

network={
        ssid="ESSID_IN_QUOTES"
        scan_ssid=0
        proto=WPA
        key_mgmt=WPA-PSK
        psk="ASCII PSK Password in Quotes" or generated_key_without_quotes
        pairwise=TKIP
        group=TKIP
}

---

### Post by ittiam on 2008-03-05
Thanks kevdog! It worked using CCMP itself in the file. However one mistake which I made was make ap_scan = 2 in the conf file. I know I did not copy paste it properly in my previous post. But when I removed that line it started working from command line. 

Is it possible for you to explain this? What is ap_scan and how making it 2 did not work for me. I dont know why I put 2 there but I did.

While googling i found another thread which had the same problem and was mentioned it worked fine in feisty, that is it was being displayed as TKIP in fesity but it was being displayed wrongly as WEP-40  in gutsy while executing iwlist scanning and I guess a bug has already been filed. Any idea has the update been released with this fix?

---

