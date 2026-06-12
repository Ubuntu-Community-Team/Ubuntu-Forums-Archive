---
title: "ubuntu 11.04 problem"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by johnw512 on 2011-07-28
Downloaded ubuntu but at startup screen advised me to switch to classic version? any ideas will help!!

---

### Post by fractalman on 2011-07-28
Downloaded and installed , right?

Sounds like you need to configure the graphics settings and possibly change the driver,
 11:04 comes with unity but for systems that haven't got the graphics capability you can use 'classic' mode, choose from the option at bottom of log in screen

if it's a fresh install chances are you just need to update everything,

open a terminal, ctrl+alt+t  and type

```
 sudo apt-get update  
```

you will be prompted for your password but when you type you will not see anything on the screen, then hit enter

this should update everything for you
then have a look under system>administration>additional drivers
and see if any drivers are available to use, i have about 3 i can choose but because i have an nvidia graphics card i installed the nvidia current driver from synaptic package manager

system>synaptic package manager
and in the searchbox look for nvidia-current, then mark for installation and click 'apply'

once installed, reboot and select 'unity' on the log in screen

---

### Post by johnw512 on 2011-07-28
<<< ABSOLUTE BEGINNER!! i DOWNLOADED UBUNTY 11.04 FROM WEB ONTO A CD, DOWNLOADED IT AND INSTALLED, DELETED WINDOWS XP. AFTER INSTALLATION IT TOLD ME THAT I COULDNT RUN UNITY ( DONT HAVE HARDWARE ) ANY HELP WITH THIS PROBLEM IS COMPLETELY APPRECIATED!!

---

### Post by johnw512 on 2011-07-28
I figurede out why i cant get unity on ubuntu 11.04..I HAVE NO PROPRIETARY DRIVERS!! What does this mean? I want to keep ubuntu but do i have to "downgrade" to a different version? If so what is the easiest way to accomplish that?  I am new to this and have limited knowledge on computers. Thank You in advance      

--Also when I installed ubuntu i deleted Windows XP..could this have been a factor or is it my computer just dont have that?

---

### Post by Frogs Hair on 2011-07-28
There would be no proprietary drivers installed by default . If you open Additional Drivers and there is no proprietary drivers offered , then a driver can't be found . If there is a recommended driver select activate .Do you know what graphics card your computer ? Removing XP would have nothing to do with driver availability .To find out what card or graphics controller you have use the following in the terminal . 

lspci

---

### Post by overdrank on 2011-07-28
Hi and welcome, please do not create multiple threads on the same issue. Threads merged :)

---

### Post by johnw512 on 2011-07-28
Ok I hope this is what u were talking about!! see if u can make sense of it THX  


00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by cloyd on 2011-07-28
Another suggestion: Download 10.04. Try it with a live cd or live usb.  It doesn't have unity, but it may work for you. The first machine I put ubuntu on ran with everything that I tried until 11.04. Just got a black screen. My other machine runs 11.04 just fine.

---

### Post by cloyd on 2011-07-28
Another suggestion: Download 10.04. Try it with a live cd or live usb.  It doesn't have unity, but it may work for you. The first machine I put ubuntu on ran with everything that I tried until 11.04. Just got a black screen. My other machine runs 11.04 just fine. I wonder if 10.04 will work for you. Besides, 10.04 is a long term support release . . . you will get to use it longer before having to upgrade to a new release.

Uh . . . sorry for the double post. Not quite sure how I did that.

---

### Post by wildmanne39 on 2011-07-28
Hi, run this in a terminal and it will tell us if you can run unity.
```
/usr/lib/nux/unity_support_test -p
```
and post the results here.

---

### Post by Mark Phelps on 2011-07-29
> **johnw512 said:**
> 00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)


This indicates that you're using an Intel video chip -- and there are no proprietary video drivers for Intel chips, only for AMD/ATI and Nvidia chips.

---

