---
title: "Gigafast WF747-UI wireless usb"
date: 2006-12-26
forum: Networking &amp; Wireless
---

### Post by xSauronx on 2006-12-26
i decided to take the laptop i was using and put linux on it, since ive always wanted a dedicated linux machine to use. 

ive got a Gigafast WF747-UI wireless usb adapter id like to use. it doesnt have native drivers, but id like to have the experience of getting it to work....or at least trying, before i buy a wireless adapter that would give me less trouble. 

oh, and im cheap ;)

im using Xubuntu 6.10 on a dell inspiron 1000

the first thing i did was google around a bit, and came across the following page:
[please tell: your network problems and solutions]("http://www.ubuntuforums.org/showthread.php?t=184795&page=4")

i thought i had hit a jackpot, since the specific adapter was explicitly mentioned. but this was not the case. 

i followed the directions (you cant miss the post) by gizzmoe. first i blacklisted what he said to blacklist and rebooted, after that the network config panel showed a wireless usb adapter. hurrah? no. 

i installed the drivers properly with ndiswrapper, and when i type in ndiswrapper -l it shows the driver is installed, and the hardware present. 

but im getting nothing. 

i notice that in the network config it shows the wireless device as eth2...and sometimes eth1, instead of wlan0 (which, after a bit more googling and forum-hunting, im rather certain is what it should be labled) 

whether thats the actual problem or not, i dont know. i *do* know that wifi radar doesnt see *anything* in an office building that should show at least 3 wireless networks, and that even specifically setting it to connect to the one in my boss' office doesnt get it anywhere. 

so now i need some help :)

i dont know what other information to give that may help solve the problem, just say the word and next time i log on (im at a friends and left the laptop at home) ill get whats asked for. 

again, id really like to be able to play around and maybe learn a little by trying to get this to work before i buy something that may be easier to set up. 

thanks :)


Update:

after getting home last night and fooling around a bit, the device came up under the network management panel as wlan0. i also noticed that the lights on the device are now on. wifi-radar doesnt cause any changes, or pick up anything. 

after getting to work this morning, i see its now eth1 again. i have no idea why. any ideas?

---

### Post by xSauronx on 2006-12-27
ttt, im completely lost as to what to do

---

### Post by sadalmelik57 on 2007-01-06
I did get my Gigafast USB Wireless adapter to work by using the instructions at this location.  Maybe it will help you.  I had to install the ZyDas 1211b drivers.  

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29)

I've seen references to the NDISWrapper but I don't know a thing about it and I didn't use it to install and get it working.

Good Luck!

---

