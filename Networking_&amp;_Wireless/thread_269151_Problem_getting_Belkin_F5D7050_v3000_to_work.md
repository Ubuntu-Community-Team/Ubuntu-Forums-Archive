---
title: "Problem getting Belkin F5D7050 v3000 to work"
date: 2006-10-01
forum: Networking &amp; Wireless
---

### Post by walmack on 2006-10-01
This is my first post on this this forum. I am completely new to ubuntu and linux. I have been googling and checking forums for two days now and I am completely stuck. I have a belkin F5D7050 v3000 wireless adaptor.

I have reached the stage where I type

ndiswrapper -l

This works, and my rt73 driver and hardware are said to have been detected.

However I still cant connect. The l.e.d doesn't flash or anything. I checked on device manager and belkin 54g is there also.

I did try,

modprobe ndiswrapper

this resulted in error messages.

as did, ndiswrapper -m.

I have gone through numerous 'how tos' and I am getting frustrated.

I tried to install network-manager-gnome, but it was dependent on ibatk1.0-0, which was dependent on ibc6, which was dependent on tzdata. Finally when I tried to install tzdata I got a message in the terminal about a 'broken pipe'.

I have tried and tried and tried, but I need help.

If anyone could find their way to helping my sorry self then it would be greatly appreciated. Please remember I am a noob and need things in baby steps

Thanks

---

### Post by Gflo on 2007-09-16
well at least im not the only person with this problem
have you tried this guide?
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29)
i think its stupid because you have to be connected to the internet to use it but the whole purpos of the thing is to be able to acsess the internet

---

