---
title: "Ubuntu 16.04 cannot connect to Wi-Fi, Centrino Wireless-N 2200 (BGN)"
date: 2018-02-12
forum: Networking &amp; Wireless
---

### Post by liuyangly25 on 2018-02-12
Hi,

I have a lenovo Z580. I just erased previous windows os and installed a fresh ubuntu 16.04 LTS. But the wifi cannot connect. Can anyone help?

network-info.txt can be found here. [https://paste.ubuntu.com/=tbJKW9zvHN/](https://paste.ubuntu.com/=tbJKW9zvHN/)

Thanks,
Leon

---

### Post by chili555 on 2018-02-13
You have a wireless card nightmare right here:> SSID                            BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY          ACTIVE  * 
Network-Invalid-2.4             <MAC 'Network-Invalid-2.4' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2              no        
66666                           <MAC '66666' [AC5]>  Infra  6     2437 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2              no        
66666-guest                     <MAC '66666-guest' [AC6]>  Infra  6     2437 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2              no        
66666-guest                     <MAC '66666-guest' [AC4]>  Infra  6     2437 MHz  54 Mbit/s  82      &#9602;&#9604;&#9606;&#9608;  WPA2              no        
pixelspring                     <MAC 'pixelspring' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  75      &#9602;&#9604;&#9606;_  WPA1 WPA2         no        
xfinitywifi                     <MAC 'xfinitywifi' [AC9]>  Infra  11    2462 MHz  54 Mbit/s  74      &#9602;&#9604;&#9606;_  --                no        
--                              <MAC '' [AC12]>  Infra  11    2462 MHz  54 Mbit/s  70      &#9602;&#9604;&#9606;_  --                no        
--                              <MAC '--' [AN8]>  Infra  11    2462 MHz  54 Mbit/s  69      &#9602;&#9604;&#9606;_  WPA1 WPA2 802.1X  no        
Pikachu_wifi_2.4                <MAC 'Pikachu_wifi_2.4' [AC8]>  Infra  11    2462 MHz  54 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA2              no        
Vinu-Home-2.4                   <MAC 'Vinu-Home-2.4' [AC7]>  Infra  8     2447 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA2              no        
DIRECT-4Hdchen23                <MAC 'DIRECT-4Hdchen23' [AN11]>  Infra  6     2437 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA2              no        
--                              <MAC '' [AC13]>  Infra  1     2412 MHz  54 Mbit/s  52      &#9602;&#9604;__  --                no        
66666                           <MAC '66666' [AC3]>  Infra  6     2437 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA2              no        
GOOGLE_plus                     <MAC 'GOOGLE_plus' [AC11]>  Infra  11    2462 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA1 WPA2         no        
GOOGLE_plus                     <MAC 'GOOGLE_plus' [AC17]>  Infra  11    2462 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA1 WPA2         no        
HP-Print-A3-Officejet Pro 8620  <MAC 'HP-Print-A3-Officejet Pro 8620' [AC10]>  Infra  11    2462 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA2              no        
--                              <MAC '' [AC14]>  Infra  8     2447 MHz  54 Mbit/s  30      &#9602;___  --                no        
ET                              <MAC 'ET' [AC15]>  Infra  11    2462 MHz  54 Mbit/s  25      &#9602;___  WPA2              no        
GOOGLE                          <MAC 'GOOGLE' [AN19]>  Infra  11    2462 MHz  54 Mbit/s  22      &#9602;___  WPA1 WPA2         no    You have a crowded environment and several access points with the same name. I suggest that you undertake several steps. First, I recommend that your regulatory domain be set explicitly. Check yours:

   ```
 sudo iw reg get
```

If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:

    ```
sudo iw reg set IS
```

Of course, substitute your country code if not Iceland. Set it permanently:

    ```
sudo nano /etc/default/crda
```

Change the last line to read:

   ```
 REGDOMAIN=IS
```

Proofread carefully, save and close the text editor.

In your message log, we see:> wlp3s0: deauthenticated from <MAC '66666' [AC5]> (Reason: 2=PREV_AUTH_NOT_VALID)That means, roughly, that the password you have in your system is not valid for this instance of the access point 66666. Maybe it was the password for the* other* 66666.

Let's remove all the other connection information and start fresh. From the terminal:```
sudo rm /etc/NetworkManager/system-connections/*
```The command 'rm' for remove is permanent; proofread carefully before you press Enter.

Next, let's bind Network Manager to the strongest of the access points 66666. Please run:```
sudo iwlist scan
```Find out the MAC address for the access point. Here is a disguised sample from my machine:```
wlp3s0    Scan completed :
          Cell 01 - Address: [COLOR="#FF0000"]99:2B:B0:DC:45:99[/COLOR]
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"GBR5"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002bbe8887c1f
                    Extra: Last beacon: 740ms ago

```Now bind Network Manager to that and only that access point, like this: [https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617](https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617) While you are adding the details, select the Wireless Security tab and fill in the double-checked WPA2 password.

Restart NM:```
sudo service network-manager restart
```Any improvement? It may take a reboot.

---

### Post by liuyangly25 on 2018-02-22
Tried several times, finally made it works. Thank you so much!

---

