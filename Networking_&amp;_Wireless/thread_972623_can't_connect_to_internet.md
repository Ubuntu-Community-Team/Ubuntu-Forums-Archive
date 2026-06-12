---
title: "can't connect to internet"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by ramadha on 2008-11-05
i have bought new PC with Asus mother board & Intel processor then installed Window XP & all the mother board drivers. then i have installed Ubuntu to another partition.
problem is that, i can't connect to internet on Ubuntu, network is only works in XP only.

mother board: Asus P5GC-MX/GBL Intel 945GC VGA/Sound Socket 775 DDR2 mATX 
processor: Intel core 2 duo 2.56Ghz
router : Us Robotics


even network bulb doesn't indicate with Ubuntu (also doesn't work in Ubuntu live CD),
but everything is work fine in XP,

please help me to connect to the internet through ubuntu

---

### Post by cariboo on 2008-11-06
Could you paste the output of:

```
sudo lshw -C network
```

in your next post. We need to know what network adapter your motherboard has.

Jim

---

### Post by ramadha on 2008-11-06
hi jim,

i got this out put!

> [ResponseResult]

ResultCode=0

[Install Progress]

 Confirm Realtek Driver 

 Check Operation System Version 

 Realtek HD Audio Driver WDM Directory Exist .

 Microsoft Bus Driver Directory Exist 

 delete C:\Program Files\Realtek\Audio\InstallShield

 Copy Microsoft HD Audio QFE from MSHDQFE Directory

 Copy Realtek HD Audio Driver from WDM Directory

 Install Microsoft HD Audio QFE File (KB888111xpsp2.exe) 

 Install Realtek HD Audio Audio Driver 

 --> SetupAPI result LAAW_PARAMETERS.nLaunchResult = -4

 Copy Audio Driver to each correct location from Driver Directory


my network adapter is PCIe Gigabit/100/10 LAN controller (Onboard one)

ramadha

---

### Post by ramadha on 2008-11-06
hi jim,

i got this out put!

> [ResponseResult]

ResultCode=0

[Install Progress]

 Confirm Realtek Driver 

 Check Operation System Version 

 Realtek HD Audio Driver WDM Directory Exist .

 Microsoft Bus Driver Directory Exist 

 delete C:\Program Files\Realtek\Audio\InstallShield

 Copy Microsoft HD Audio QFE from MSHDQFE Directory

 Copy Realtek HD Audio Driver from WDM Directory

 Install Microsoft HD Audio QFE File (KB888111xpsp2.exe) 

 Install Realtek HD Audio Audio Driver 

 --> SetupAPI result LAAW_PARAMETERS.nLaunchResult = -4

 Copy Audio Driver to each correct location from Driver Directory


my network adapter is PCIe Gigabit/100/10 LAN controller (Onboard one)
my motherboard details can find in this link 
([http://ucables.com/ref/ASUS-P5GC-MX-GBL-MOTH-R45392](http://ucables.com/ref/ASUS-P5GC-MX-GBL-MOTH-R45392))

ramadha

---

### Post by Smeags on 2008-11-06
ramadha,

I was having similar issues with my Asus board (P5N32-E SLI).  I did a lot of searching and found that I needed to update my BIOS.  I hadn't updated it since I bought it probably about 2 years ago now.  I know that this problem is a known issue with boards that use the nVidia 680i chipset, but I'm not sure what chipset your board uses.

As soon as I updated my BIOS, all networking worked perfectly under Ubuntu 8.10.  This might at least be something to look into.

---

### Post by superprash2003 on 2008-11-06
are you sure you got that output when you typed lshw -C network from the terminal(Applications->accessories->terminal) ??

---

### Post by ramadha on 2008-11-06
i'm really sorry:(, it's not the output(i hv misspelled it, i'm new to ubuntu, "superprash2003" thanks for ask me to check it again)

The real out put is
> ramadha@ramadha-desktop:~$ sudo lshw -c network
[sudo] password for ramadha:

Hardware Lister (lshw) - B.02.10
usage: lshw [-format] [-options ...]
       lshw -version
        -version        print program version (B.02.10)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information 

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid,etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid,etc. )
        -quiet          don't display status

ramadha@ramadha-desktop:~$  

Smeags, i have updated my bios,but it didn't work
(my chipset is Intel 945GC Express)

ramadha

---

### Post by ramadha on 2008-11-07
i have found out my network card details,
it's 

description: 	Ethernet interface
product: 	RTL8111/8168B PCI Express Gigabit Ethernet controller
vendor: 	Realtek Semiconductor Co., Ltd.

please help me to solve this network problem!

ramadha

---

### Post by Riqz on 2008-11-07
I don't think that's the output either

---

### Post by lado on 2008-11-07
I got my wireless card working in BIOS. 
Enter BIOS when computer startup, find the tab where you can choose wifi card to be always on... 
hovewer i can still not connect to internet.. I find my router with good signal, but it wont connect. I use a WEP hex key..

---

### Post by Absorbed on 2008-11-07
ramadha, you need a capital C not little c in the command you typed and to repost the output.

This:
```
ramadha@ramadha-desktop:~$ sudo lshw -c network
```

Should be this:
```
ramadha@ramadha-desktop:~$ sudo lshw -C network
```

Also, what version of Ubuntu are you using?

---

