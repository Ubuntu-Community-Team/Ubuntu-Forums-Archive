---
title: "Installing/setting up ndiswrapper"
date: 2006-09-29
forum: Networking &amp; Wireless
---

### Post by srunni on 2006-09-29
Hi, I'm trying to get ndiswrapper working a USB wireless adapter I just got (the level one WNC-0301USB). I know it works with ndiswrapper, because their site says so, but does anyone know where I can find a tutorial for setting it up?

Thanks in advance for the help!!

---

### Post by moephan on 2006-09-30
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29)

Cheers, Rick

---

### Post by srunni on 2006-10-01
So I followed the guide you linked, but when I tried to do the driver install, I got an error, even though [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List) says that the driver with the CD should work. What exactly is going on?

---

### Post by srunni on 2006-10-02
Anyone?

---

### Post by darth_vader_ca on 2006-10-02
what is the error you are getting and what point are you at in configuring ndiswrapper?

you might have the wrong driver loaded.

go to the terminal and type

ndiswrapper -l

see if the hardware is present
and the driver is present.

if the driver is not present or the hardware perhaps you got the wrong driver loaded.

to uninstall your driver you have to type

ndiswrapper -e then the dirver name.

once you get the driver loaded

you can add ndiswrapper to the modules so it loads at startup.

modprobe ndiswrapper
echo ndiswrapper >> /etc/modules

when you reboot your computer you should be able to configure the interface in network.

cheers.

---

### Post by srunni on 2006-10-02
Well, I installed the driver, using the ```
ndiswrapper -i Autorun.inf
``` command. However, when I do ```
ndiswrapper -l
```, I get ```
autorun invalid driver!
```

I didn't try adding ndiswrapper to the modules to autorun on startup, but after installing that driver, I plugged in the wireless USB thing, and went to the ndiswrapper frontend. I tried to run "Configure Network," but it didn't do anything. I figured out how to remove the driver and did so. Is this "invalid driver!" error common? The ndiswrapper page says the driver that comes on the CD with the hardware should work, but I think it might be an older version that they say works, and I can't find that version anywhere online. Any ideas?

---

### Post by darth_vader_ca on 2006-10-02
Autorun is not a driver that is used for windows to boot the cd automatically,

the driver should be a different .inf file.

to uninstall the autorun

you have to do 

sudo ndiswrapper -e autorun.inf

---

### Post by srunni on 2006-10-02
Yeah, I managed to remove the autorun file. But that is the only .inf in there (there is a .ini, but I don't think that's it).

But anyway, I went to the chipset manufacturer site and downloaded their driver, which is available for *nix. Using it, I was able to recognize the wireless USB thing. The only problem is that I have to use iwconfig (in command line) to configure the whole thing. Is there anywhere I can get a frontend for iwconfig?

---

