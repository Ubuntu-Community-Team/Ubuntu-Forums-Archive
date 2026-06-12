---
title: "WiFI Nightmares"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by benny_boy83 on 2009-05-08
Hey Guys and Gals,

Big time newbie - Computer skills of a new born. So about 6 months ago due to the frustrations of using the worst OS system in the world namely Windows vista and being riddled with more viruses than an 80 year old hooker I decided to switch to the very cool Ubuntu platform of the time. I chose not to partition (Maybe a mistake) due to my strong dislike of the windows platform for many reasons. I felt a full divorce was the right way to go.

Install went fairly smoothly and I was totally in love with the slick and speedy system I had inherited. One major problem though - I couldn't connect to the Internet through WiFi - Though my Adsl line worked perfectly (Office) I can not connect at home to  my WiFi. I have a couple of other laptops that work fine (But they use windows) so Wifi is working.

Yesterday I upgraded to the new Jaunty 9.04 Version of Ubuntu. Same problem. I am pretty sure this is user error but would anyone be able to help?

I am using WiFi Radar and it is finding different connections available but is unable to find the IP when I try and connect. There are lots of options to add information to the connection but as stated I dont know much about computers and dont want to screw anything up by putting data in there. Especially as I have zero idea what information it wants or where to get it.

I am sure this is a simple fix and would gratefull appreciate any and all help.

Thanks in advance guys!!!

B

---

### Post by alphacrucis2 on 2009-05-08
> **benny_boy83 said:**
> Hey Guys and Gals,

Big time newbie - Computer skills of a new born. So about 6 months ago due to the frustrations of using the worst OS system in the world namely Windows vista and being riddled with more viruses than an 80 year old hooker I decided to switch to the very cool Ubuntu platform of the time. I chose not to partition (Maybe a mistake) due to my strong dislike of the windows platform for many reasons. I felt a full divorce was the right way to go.

Install went fairly smoothly and I was totally in love with the slick and speedy system I had inherited. One major problem though - I couldn't connect to the Internet through WiFi - Though my Adsl line worked perfectly (Office) I can not connect at home to  my WiFi. I have a couple of other laptops that work fine (But they use windows) so Wifi is working.

Yesterday I upgraded to the new Jaunty 9.04 Version of Ubuntu. Same problem. I am pretty sure this is user error but would anyone be able to help?

I am using WiFi Radar and it is finding different connections available but is unable to find the IP when I try and connect. There are lots of options to add information to the connection but as stated I dont know much about computers and dont want to screw anything up by putting data in there. Especially as I have zero idea what information it wants or where to get it.

I am sure this is a simple fix and would gratefull appreciate any and all help.

Thanks in advance guys!!!

B

What output do you get from typing these two commands in a terminal?


```
lspci
ifconfig
```

---

### Post by lkraemer on 2009-05-08
Open a Terminal window, cut and past each line, one at a time,
then post the output so each are separated and easy to read:
```

lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist
iwconfig

```
Then post the output of these commands

lkraemer

---

