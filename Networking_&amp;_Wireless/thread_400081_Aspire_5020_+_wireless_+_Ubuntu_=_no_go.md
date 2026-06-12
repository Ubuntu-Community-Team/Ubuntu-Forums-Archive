---
title: "Aspire 5020 + wireless + Ubuntu = no go"
date: 2007-04-03
forum: Networking &amp; Wireless
---

### Post by gdp77 on 2007-04-03
Ok. I have installed Ubuntu edgy on my Acer Aspire 5020, but wireless card doesn't work at all. I am a noob @ Linux, so I couldn't do something about it. Ethernet port works great and I connect to internet the moment I plug in the cable there. But I need wireless for my work and it doesn't work. 

I even tried Ubuntu 7.04, but I had no luck either. 

The WI-Fi card is recognized as Broadcom 802.11g by windows and u must press a key on the laptop case to enable the Wi-Fi. 

Please help me with this matter. If I manage to get WI-Fi working at my ubuntu istallation then I will be able to completely DUMB moronSoft out of my computer. 

Thanks for helping.

P.S. At the following link there are the drivers that Acer gives for my notebook. They might help

[http://support.acer-euro.com/drivers/notebook/as_3020_5020.html](http://support.acer-euro.com/drivers/notebook/as_3020_5020.html)

P.S. I forgot to mention that I use 64bit Ubuntu

---

### Post by bobswat on 2007-04-04
Are you able to see your wireless in System->Administration->Network?

should be wlan0

if not, then try using ndsiwrapper
run these commands in terminal:
make sure you have the windows drivers, that should include the .inf file Im talking about

```

sudo ndiswrapper -i */path/to/inf/file*
sudo ndiswrapper -m
sudo depmod -a
sudo modprobe ndiswrapper

```

then run ndiswrapper -l and it should say something to the effect of "*yourWirelessCard * **Drivers present Hardware Present**"

Hahha, its a solution that worked for me on ubuntu 6.06LTS (dapper)

Good luck!

EDIT: you probably dont have ndiswrapper installed, put your ubuntu disk in and you should be able to do 
```

sudo apt-get install ndiswrapper-utils

```

Should work as long as you have the proper repositories checked in System->Adminstration->Synaptic Package Manager (or whatever you're using)

---

### Post by shilliard on 2007-04-04
You also need to enable wireless on the laptop, there is a tool called acer_acpi that does this.  Check out:

[http://ubuntuforums.org/showthread.php?t=224350](http://ubuntuforums.org/showthread.php?t=224350)

You need to enable the wireless device and then use ndiswrapper, should work fine

---

### Post by mumbly58 on 2007-05-22
.. and you shoudl have a look at this  ------> [http://ubuntuforums.org/showthread.php?t=450299&highlight=acer_acpi]("http://ubuntuforums.org/showthread.php?t=450299&highlight=acer_acpi")

---

