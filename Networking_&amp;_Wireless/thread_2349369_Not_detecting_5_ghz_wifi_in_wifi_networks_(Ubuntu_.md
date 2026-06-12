---
title: "Not detecting 5 ghz wifi in wifi networks (Ubuntu 16.04)"
date: 2017-01-13
forum: Networking &amp; Wireless
---

### Post by JackMohr on 2017-01-13
I just updated my wireless router. My new wireless router is dual band, 2.4 ghz and 5 ghz. When I look in my wi-fi networks on Ubuntu, my computer only detects the 2.4 ghz band. I've tried entering the details of the 5 ghz band as a hidden network but it will not connect. Other laptops and mobile devices in the house have successfully connected to the 5 ghz band without issue. Any suggestions?

---

### Post by JackMohr on 2017-01-13
Following recommendations in [this thread]("http://unix.stackexchange.com/questions/137894/how-do-i-find-out-if-my-wireless-card-supports-5ghz"), I got the following:

```
jack@jack-Inspiron-1545:~$ iwlist wlp12s0 freq 
wlp12s0   32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
```

It looks like I have 5 GHz capability on my wireless card. I've reset the Wifi channel to one of the 5 GHz channels listed above but I'm getting nothing.

---

### Post by geeksmith on 2017-01-13
It may be easier for the forum members to help if you post the output from the script in this sticky thread: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by JackMohr on 2017-01-14
```
jack@jack-Inspiron-1545:~$ wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
> chmod +x wireless-info && \
> ./wireless-info
--2017-01-14 11:01:27--  https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info
Resolving github.com (github.com)... 192.30.253.112, 192.30.253.113
Connecting to github.com (github.com)|192.30.253.112|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info [following]
--2017-01-14 11:01:28--  https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 151.101.44.133
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|151.101.44.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16156 (16K) [text/plain]
Saving to: ‘wireless-info’

wireless-info       100%[===================>]  15.78K  --.-KB/s    in 0.03s   

Last-modified header missing -- time-stamps turned off.
2017-01-14 11:01:28 (463 KB/s) - ‘wireless-info’ saved [16156/16156]

[sudo] password for jack: 

Results saved in "/home/jack/wireless-info.txt".

Results also archived in "/home/jack/wireless-info.tar.gz", as they exceed the 19.5 kB size limit for ".txt" attachments on the Ubuntu Forums.
```

---

### Post by jeremy31 on 2017-01-14
Please attach the wireless-info.tar.gz file to a post or copy the contents of the wireless-info.**txt** file and paste at paste.ubuntu.com and post the URL

---

### Post by JackMohr on 2017-01-15
I've attached the wieless.info.tar.gz file

[ATTACH]273214[/ATTACH]

---

### Post by geeksmith on 2017-01-16
Crazy question -- are you sure there is at least one 5GHz BSS in range? Many consumer APs don't have a 5GHz radio, and you haven't mentioned whether you're running your own AP or using somebody else's.

If the 5GHz APs are using DFS channels, you'll have to set your regulatory domain in order to see them in a channel scan. Check out this link for more info: [https://wireless.wiki.kernel.org/en/users/documentation/iw#updating_your_regulatory_domain](https://wireless.wiki.kernel.org/en/users/documentation/iw#updating_your_regulatory_domain)

---

### Post by jeremy31 on 2017-01-16
Let's set the country code in case Canada uses different 5Ghz frequencies than what are used with the default country code
```

sudo iw reg set CA
sudo sed -i 's/^REG.*=$/&CA/' /etc/default/crda

```

Reboot and see if the 5 Ghz works

You could also try the open source driver by uninstalling the proprietary with
```
sudo apt-get remove bcmwl-kernel-source  && sudo apt-get install firmware-b43-installer
```

Reboot

---

### Post by JackMohr on 2017-01-16
geeksmith- the other devices in the house are on the 5 GHz radio band and they're all in the same area.

I tried resetting the country code and uninstalling the proprietary drivers/installing open source ones with no luck. Post driver swap and restart I'm seeing a lot more wifi networks as available but unfortunately my 5 GHz band is not among them.

---

### Post by jeremy31 on 2017-01-17
Do the results from ```
iwlist chan
```
Match any 5Ghz channels available on the router?

---

### Post by JackMohr on 2017-01-20
jack@jack-Inspiron-1545:~$ iwlist chan
lo        no frequency information.

wlan0     11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency:2.462 GHz (Channel 11)

enp9s0    no frequency information.


Not seeing any of the 5 GHz channels available. The 2.4 GHz and 5 GHz bands have separate names and passwords, so not totally surprised they aren't showing up here.

---

### Post by JackMohr on 2017-01-20
I believe I've discover what my issue is and it is my wireless card not being able to support the 5 GHz.

Ran lspci in terminal following [URL="https://ubuntuforums.org/showthread.php?t=1006786"]this thread to confirm my wireless card

[/URL]At the end of the output: 0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

Based on [this thread ]("http://superuser.com/questions/945517/how-to-determine-what-type-of-wifi-networks-are-supported-by-your-driver-on-linu")it looks like the b/g indicates the card only supports 2.4 GHz.

---

### Post by wildmanne39 on 2017-01-20
This also says you do not have a card capable of 5ghz.
```
wlan0 11 channels in total; available frequencies :
Channel 01 : 2.412 GHz
Channel 02 : 2.417 GHz
Channel 03 : 2.422 GHz
Channel 04 : 2.427 GHz
Channel 05 : 2.432 GHz
Channel 06 : 2.437 GHz
Channel 07 : 2.442 GHz
Channel 08 : 2.447 GHz
Channel 09 : 2.452 GHz
Channel 10 : 2.457 GHz
Channel 11 : 2.462 GHz
Current Frequency:2.462 GHz (Channel 11)
```
if you did the channels would be listed their.

---

