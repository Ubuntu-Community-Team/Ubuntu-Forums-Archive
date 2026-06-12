---
title: "Unreliable wireless connection"
date: 2014-03-21
forum: Networking &amp; Wireless
---

### Post by vplobanov on 2014-03-21
Hi everyone,
I'm quite new at using Linux and Ubuntu specifically (I had Mint for awhile before), and today encountered a strange problem. I just got a new Toshiba Satellite p50-A series laptop, and immediately replaced windows 8 with ubuntu. It took awhile to get the wireless working at all (despite a strong connection from my router). Finally, with the help of this post ([http://askubuntu.com/questions/331667/no-wireless-for-intel-corporation-7260-version-63](http://askubuntu.com/questions/331667/no-wireless-for-intel-corporation-7260-version-63) ) I was able to get it set up. 

Currently I'm having an issue, where every 5 minutes or so the wifi quits. I still have the symbol, suggesting that there is a connection. However no internet dependent apps (or, obviously, browsers) will connect. Wired connection is perfect, and the internet connection is strong for the duration of the 5 minutes and without lag.

Understandably this is quite annoying. Switching the wifi on/off (via the short cut on the keyboard) will fix the problem, but only temporarily.

Any ideas as to what could be causing this issue? 
Please let me know if there are any tests I can do through terminal to help.

---

### Post by chili555 on 2014-03-21
>  Finally, with the help of this post ([http://askubuntu.com/questions/33166...260-version-63](http://askubuntu.com/questions/33166...260-version-63) ) I was able to get it set up. Pretty good stuff, isn't it? That guy is awesome.

Are you certain you got the later firmware?```
dmesg | grep iwl
ls -al /lib/firmware | grep 7260
```Thanks.

---

