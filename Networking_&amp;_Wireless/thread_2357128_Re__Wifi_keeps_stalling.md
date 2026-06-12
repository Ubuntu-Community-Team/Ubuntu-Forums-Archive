---
title: "Re:  Wifi keeps stalling"
date: 2017-03-30
forum: Networking &amp; Wireless
---

### Post by sandjkirkland2 on 2017-03-30
i asked this question at askubuntu.com but received no responses. I decided to ask it here as well in hopes to get better responses (any). In the title I say "WIFI KEEPS STALLING". I say stalling instead of disconnecting because the NM applet shows wifi is connected and even shows a strong wifi signal even when wifi stops working.

My O.S. Ubuntu 16.04 Studio. Every few minutes i have to disable end re-enable  wifi through nm. i have to keep doing this as long as I am online. Wifi  says connected but I get no network traffic unless I disable and  re-enable wifi. I've searched google for this problem but all I get are  responses with the older ubuntu versions. i don't know if this matters  or not but I have laptop Samsung R780 with bios build 7 years old. All original parts.

I ran 
```
wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) && \
chmod +x wireless-info && \
./wireless-info
```

when I knew I was connected
and the results are at  [URL="http://paste.ubuntu.com/24252415/"]paste.ubuntu.com/24252415



[/URL]

I ran the above code when I noticed that wifi stopped working and here is the results
Resolving github.com (github.com)...  192.30.253.113, 192.30.253.112 Connecting to github.com  (github.com)|192.30.253.113|:443... failed: Connection timed out

It displays the same message over and over until it gives up.

I turned on echo when booting to see if I  could see any problems and I found this. 
```
14.3678521 rt1819xe  0000:02:00.0 wlan0 (uninitialized): *rt192e_read_eeprom* info(): Invalid EEPROM ID: 4a4.
``` 

I don't understand this problem because i do have wifi as soon as I type my password in to start a session. Wifi just does not stay connected for more than 5 minutes at a time. To re-establish connection all I have to do is click on the wifi network which is an effect of turning wifi off and then back on. This connection only lasts 3 to 5 minutes and then I have to this procedure over and over, as long as I am online.

---

### Post by howefield on 2017-03-30
Thread moved to the "*Networking & Wireless*" forum, probably a better fit.

---

