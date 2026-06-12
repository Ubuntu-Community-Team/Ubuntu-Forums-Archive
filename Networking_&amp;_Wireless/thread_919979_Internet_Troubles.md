---
title: "Internet Troubles"
date: 2008-09-14
forum: Networking &amp; Wireless
---

### Post by Wayner on 2008-09-14
I'm new to Ubuntu and I am having troubles getting internet working with it. 

I have a Dell Wireless 1505 Draft 802.11n WLAN Mini-card and I was looking for it on the supported cards list and didn't find it and so in Ubuntu in the network settings place my wireless card isn't showing up thus not letting me use internet.

Any help would be very much appreciated 

Thanks
Wayner

---

### Post by Crafty Kisses on 2008-09-14
First, try installing the following package:
```
sudo apt-get install ndisgtk
```
Then after that package is installed, you need to download the drivers for your card, and you can do that right [**here**]("ftp://ftp.hp.com/pub/softpaq/sp34501-35000/sp34510.exe").
Remember, don't forget:
```
sudo ndiswrapper -m

```
And```

sudo modprobe ndiswrapper
```
Make sure the ndiswrapper worked correctly and see if you get an output from this command:
```
sudo ndiswrapper -l
```
Then see if it's detected through the computer itself, you can do that by doing this:
```
lspci | grep Wireless
```
After you've done all that, reboot and it should spring to life. :)

---

### Post by pingolluz on 2008-09-14
Hello to everybody here!
Im just new here also & I have same problem with you Wayne. 
Pls help us here.... :confused:
I'd just installed Ubuntu to my computer here at home coz I wanna have dual OS so I have now Vista & Ubuntu.
May only problem is that.... I can't connect Ubuntu t internet.
Im not techie so I need some help too...

Thanks in advance!

---

