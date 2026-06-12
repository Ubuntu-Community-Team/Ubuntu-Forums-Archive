---
title: "wireless card not detected on Thinkpad X60 7.10"
date: 2007-11-15
forum: Networking &amp; Wireless
---

### Post by tabithaboof on 2007-11-15
I have a thinkpad x60 which I have a fresh install of gutsy on. Almost everything worked perfectly out of the box but I am totally stumped with getting my wireless card to work. As far as I can tell my machine has and atheros card and I found this very helpful post

[http://ubuntuforums.org/showthread.php?t=429195](http://ubuntuforums.org/showthread.php?t=429195)

and I have followed this How To

[http://thinkwiki.org/wiki/How_to_install_ndiswrapper_for_the_ThinkPad_11a/b/g/n_Wireless_LAN_Mini_Express_Adapter](http://thinkwiki.org/wiki/How_to_install_ndiswrapper_for_the_ThinkPad_11a/b/g/n_Wireless_LAN_Mini_Express_Adapter)

which helped me 

1  - install ndiswrapper
2 - Download the windows driver
3 - Install the windows driver 

as verfified here 

```
tabby@tabby-laptop:~/Desktop/WINXP_2K$ ndiswrapper -l
net5416 : driver installed
        device (168C:0024) present

```

but iwconfig cant find the card!

```
tabby@tabby-laptop:~/Desktop/WINXP_2K$ modprobe ndiswrapper
tabby@tabby-laptop:~/Desktop/WINXP_2K$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

tabby@tabby-laptop:~/Desktop/WINXP_2K$ iwconfig wlan0
wlan0     No such device

```

I would REALLY appreciate some help on this one! Thanks alot.

---

