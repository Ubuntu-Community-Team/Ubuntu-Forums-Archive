---
title: "RaLink RT2500"
date: 2007-11-28
forum: Networking &amp; Wireless
---

### Post by hyp3R on 2007-11-28
Hey people.
As you can see from the thread name, I have issues with configuring Ralink RT2500 wireless card on Ubuntu 7.10.

First off, I ll say that I m aware of many links like :

[http://www.ralinktech.com/ralink/Home/Support.html](http://www.ralinktech.com/ralink/Home/Support.html)
[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500)
and so on, so I ll tell you what I did so you can help me.

So, I installed Ubuntu 7.10 on my second partition (It's dual boot now).
I opened the Ubuntu guide and typed wireless in search field.
Since I found some things like : Install ndiswrapper drivers and windows drivers I did it.

I installed the drivers from my Ubuntu 7.10 CD (Sync manager) and I installed windows XP drivers as well. 
I extracted files to my desktop (.INF) one and installed it with command

sudo ndiswrapper i- ~/Desktop/Rt2500.INF

(Note - I found this on Ubuntu 6.10 guide like half year ago when I tried to configure it there.)

After that I did :
ndiswrapper -l to see if the driver is listed and yes it was/is there.

Did : 
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m

Like 15 days ago I tried those things with 6.10.
I asked for some help on other forums ([www.youngcoders.com](www.youngcoders.com)) and they told me to try with commands in terminal :

sudo network-admin
Than to add open dns servers : 208.67.222.222
                                                 : 208.67.220.220

sudo cp /etc/resolv.conf /etc/resolv.conf.auto
sudo getid /etc/dhcp3/dhclient.conf
sudo ifdown eth0 && sudo ifup eth0

I tried those things as well but It didn't make any difference.
Problem is because I actually connect to my wireless link (There are 6 points in my town, located on 6 buildings and they are all listed and same with windows I can connect to any and every time I click let's say google it will pop up gateway 10.100.18.1/login I enter my user name and password and I can work, but not here.

It seams I m actually connected but it won't open anything ...

Please people, I m trying to make this almost 15 days, I m not sleeping and I totally quit on everything but this till I make it work.
Please if there's anyone who knows how to configure entire thing, please post it, you would help me a lot !

Thanks
hyp3R
*[www.youngcoders.com*](www.youngcoders.com*)

---

### Post by hyp3R on 2007-11-28
Anyone ?!?

---

### Post by pebo on 2007-11-28
Try compiling a driver from [here]("http://rt2x00.serialmonkey.com/wiki/index.php/Downloads"). They are regularly updated. I'm not on ubuntu atm, but they work for me. You will probably have to blacklist any rt2x00 driver that you have on your system. You shouldn't need to use ndiswrapper.

---

### Post by hyp3R on 2007-11-29
Ok thanks, I will try to do it but I think I already did it since I followed entire guide... I m in linux center atm so I ll let ya know when am home ...

Thanks

---

