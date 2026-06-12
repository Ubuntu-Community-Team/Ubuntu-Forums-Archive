---
title: "Slooooow and unrelieable internet since update to 16.04"
date: 2016-10-24
forum: Networking &amp; Wireless
---

### Post by Leukozyt on 2016-10-24
I use ubuntu 16.04 on an old lenovo T60p.

After I updated from 14.04 to 16.04, the wifi (and wlan) doesn't work properly anymore:
• If it works at all, it is so slow that it takes ages to even download new email (yaaaaaaawn)
• After some time it often drops out and everything is gone, no wlan, no wifi recognised. Works again after reboot.
• If I want to change from one network to another (e.g. to smartphone hotspot or wlan), it doesn't wort. Only works with the first connection after reboot.
• all networks/wifi work well on other devices and worked well before update.

I read about similar problems in a prior thread, but what was suggested there didn't work with me either.

I also read that it is suggested to directly install ubuntu 16.04 instead of updating. The IN issue is so tiring that I would do this, but how can I if I can't download an install CD image... (because it takes days, and the connection fails after minutes)?

Help would be very much appreciated. I am an ubuntu dummy (one of these who just uses it because windows is worse), so please formulate your answers accordingly  thanks!

here is what iwconfig says:

leukozyt@leukos:~$ iwconfig
lo        no wireless extensions.

wlan1     IEEE 802.11abg  ESSID:"PBS-46A2F9"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: A4:52:6F:46:A2:FE   
          Bit Rate=48 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:24  Invalid misc:239   Missed beacon:0

eth2      no wireless extensions.

irda0     no wireless extensions.

---

### Post by Hadaka on 2016-10-24
Hi, From a working wired connection please open a terminal ctrl/alt/t
 then Copy and paste the following command

```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info
```
This command writes a file to your home directory.The file name is wireless-info.txt
From your directory please copy,paste and post the wireless-info.txt
thanks.

---

### Post by danieledei on 2016-11-03
I am having the same problem.
May I send you the TXT  file you asked for.
Thank you

[ATTACH]271935[/ATTACH]

---

### Post by Hadaka on 2016-11-03
@danieledei , Hi, you have some unusual network definitions and in the event
we are able to solve your issues, we have no way to mark your problem sloved
as this can only be done by the person that started the thread, Please start your
own thread and include a new wireless diagnostic report to help find a possible
resolution.
thanks for your understanding.

---

### Post by Leukozyt on 2017-01-03
Thanks a lot, sorry for my late reply, all solved :-)
greetings
Leukozyt

---

### Post by Hadaka on 2017-01-03
Hi, glad you found a solution, would you please
post what you did for your slow wifi to possibly
help others.
thanks

---

