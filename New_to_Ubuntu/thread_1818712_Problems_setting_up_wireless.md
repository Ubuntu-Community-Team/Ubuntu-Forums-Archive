---
title: "Problems setting up wireless"
date: 2011-08-05
forum: New to Ubuntu
---

### Post by SuchetBargoti on 2011-08-05
Hi guys, 

Installed Ubuntu 10.04 a week ago and have been on the Ethernet cable since for the internet. Unplugged that yesterday to find out that wireless is not working! At the same time it is working well on the windows partition. 

Started searching for solutions and ended up downloading ndisgtk installs "Windows wireless drivers" and to that i need to provide the .inf file for my wireless card "Intel® Centrino® Advanced-N 6230 with Bluetooth v3.0+HS"

So I went to the intel website and downloaded ICS_Ds64.exe. Other forums mentioned that I need to extract this file to find the .inf file so I did
cabextract ICS_Ds64.exe
but that spat out:
```

ICS_s64.exe: no valid cabinets found

All done, errors in processing 1 file(s)

```
I also had to success with unzip (I have my network cable plugged in while doing all this).

I also downloaded ICS_Dx32.exe which is the windows xp 32 bit driver as I have a 32 bit ubuntu. Same error while trying to use cabextract. 

I have also looked at my windows 7 reinstallation DVD and the Drivers and Utilites dvd but dont really know where to find the .inf file in those. 

Few week ago when I first started using Ubuntu, I had Ubuntu v11.04 installed and there were no wireless problems on that. Unfortunately due to reasons I cannot go into here, I need to work on Ubuntu 10.04. Any help would be appreciated.

---

### Post by Matt__ on 2011-08-05
[COLOR=DimGray]# there is a linux driver [on this site]("http://intellinuxwireless.org/?n=Downloads") for you.

#I believe its just unpack and do```
cp iwlwifi-6000g2b-5.ucode /lib/firmware
```[/COLOR] //edit: looks like this dosnt work with kernel 2.6.24 and up.
so [look here instead]("http://linuxwireless.org/en/users/Download") for the upstream version.

Full instructions on compiling on this site too.

---

### Post by SuchetBargoti on 2011-08-05
Thanks Matt,

I followed the bleeding edge installation at the second [link]("http://linuxwireless.org/en/users/Download") you sent me and although there was a lot of reading on that page :( got through it, restarted comp and wireless works!!

---

### Post by Matt__ on 2011-08-05
now clone your install with [remastersys]("http://www.geekconnection.org/remastersys/repository/") (to create a custom live disc) or a utility of your choice so you dont have to go through it again!

---

