---
title: "Complete Linux newbie looking for help"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by brittlee on 2010-08-18
Hello!
I just installed Kubuntu 10.04, because after hearing my friend talk about her amazing Linux Operating system, I seriously wanted to try it.
I was just messing around with how it comes, and was like "Woah, this is cool!"

Then, I tried to connect to the internet.

I noticed my wireless was not on, so I pressed the hot key (F12 on my HP Pavilion dm4), but the LED light did not change from orange to blue like it is supposed to.
Concerned, I've spent the past two days trying to find a way to fix this.
I've been all over these forums and Google trying to find SOMETHING to help me.
I've read tutorials and help posts, but Ive realized something.

I have no clue what I'm doing.

I know what the terminal is, and I know how to get to it, but I dont really know how to use it.
I looked at a tutorial, but it didn't really help me with my problem.
I see tons of stuff about the BIOS, but I don't even know how to get to that.
I tried looking it up, but nothing told me how to GET to the BIOS, it just told me how to use it.

Also, I tried connecting my computer to the internet using the Ethernet cable, but...I'm not even sure how to do that, because I've been using wireless for the past 5 years.


Any help would be greatly appreciated, even just some help on how to USE this operating system.
I shifting over from Windows 7, so...I'm basically clueless.
Sorry for all the questions!

---

### Post by nightshade209 on 2010-08-18
Could you tell which tutorial you looked at? BIOS is usually the first screen you see when you start up the PC, before the operating system even loads. You'll probably be getting a message every time you boot up, telling you how to enter BIOS (Delete key, or F2, or Alt+F2 or something - differs between manufacturers). I don't mean to alarm you, but I would strongly suggest NOT changing anything in your BIOS unless you know what you are doing. Also, you shouldn't start troubleshooting a networking problem from the BIOS unless you have tried everything else.
Also, the hotkey might not be mapped. Is there any other way of setting up the connection?
And you don't have to be sorry about asking questions!!

---

### Post by Zorgoth on 2010-08-18
You might have to press Fn-F12 rather than F12.

Also that LED may or may not work right - it should, but the only way to be sure of whether you have wireless is to try to connect...

So there should be an icon in your notification area/system tray for networking - these are the little icons in the top right, just like Windows has on the bottom right.

Also you can try to fiddle with System > Preferences > Network connections
(your wireless will probably be called something like wlan0)

Could you please give us the output in the terminal of the command

lspci

this should identify your wireless adapter (and all your other pci devices)

Finally, you may need proprietary drivers to run you card, particularly if it is a broadcom card.  You can check that out in System > Administration > Hardware Drivers.

EDIT: You are in Kubuntu, so some of my advice does not apply.

There should still be a program called "Hardware Drivers" somewhere on your computer still I think - try searching for it in the text box the KDE main menu.

Also your notification area I believe is just where it is in Windows.

can't remember off the top what the equivalent to System > Preferences > Network connections is - maybe it is in "Configure your desktop" or whatever it is?

---

### Post by Zorgoth on 2010-08-18
DOH!

Hardware Drivers might not tell you anything if you are not connected to the internet.  You will need to hook up to ethernet (this essentially always works) - you will need an ethernet cable, and there should be a port on your wireless box that will let you hook up directly.

---

### Post by Kixtosh on 2010-08-18
> **brittlee said:**
> ... Also, I tried connecting my computer to the internet using the Ethernet cable, but...I'm not even sure how to do that, because I've been using wireless for the past 5 years. ...I'll tackle the real easy part!
 
1) Check your wireless router, wherever that is in your home. It may be an integrated broadband modem and wireless router (gateway) or a separate wireless router, connected to a separate broadband modem. On the back, you will probably find four RJ45 ethernet sockets, with a lable such as E1, E2 ... These look similar to RJ11 telephone jacks, but are wider, with more connectors inside.
 
2) Find the same RJ45 ethernet socket on your laptop. Again, don't confuse it with the telephone (modem) jack, if your computer has one of those. Not all laptops have an ethernet port, but on recent HP laptops, this has often been located on the left side.
 
3) Find yourself an ethernet cable (they are frequently included free with any modem you may have received, depending on where you are and your ISP). If your wireless router is separate from your broadband modem, then you will already have an ethernet cable connecting both of those.
 
4) Connect one end to the laptop, and the other end to the wireless router.
 
Voilà! You should be in business!
 
[http://en.wikipedia.org/wiki/Category_5_cable](http://en.wikipedia.org/wiki/Category_5_cable)
[http://www.amazon.com/b?ie=UTF8&node=464398](http://www.amazon.com/b?ie=UTF8&node=464398)

---

### Post by brittlee on 2010-08-18
Kixtosh:: I connected the Ethernet cable, and it says it is connected, but with no Internet access. What am I supposed to do about that? 

Zorgoth:: I tried the Fn+F12, and still nothing. I'm not only looking for the change in the LED color, but also checking the wireless button in the bottom right-hand side of the screen. It doesn't even show that I have any connections available.

When I put in lspci I get this::
```

&#65279;brittany@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
02:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
brittany@ubuntu:~$ 


```

I have...no clue what that means.
I do know the part that is my username, and that the ~ means something about my home file? Or something like that.
But besides that, I'm clueless.


nightshade209:: Oh, thank you! I don'tguess I'll be messing with that any time soon, then. =)



And, I don't know if this helps, but I know that my Internet connection is fine. It works when I run Windows 7 on the HP, and it also works on both Vista and Ubuntu on my old Toshiba laptop (Satellite A135, I think?) But the Toshiba has a switch on th front to turn wifi on, it's not a hotkey on the keyboard.

---

### Post by Devastator9 on 2010-08-18
Check out this thread.
[http://ubuntuforums.org/showthread.php?t=1540910&highlight=Broadcom+Corporation+Device+4727+%28rev+01%29](http://ubuntuforums.org/showthread.php?t=1540910&highlight=Broadcom+Corporation+Device+4727+%28rev+01%29)

---

### Post by brittlee on 2010-08-19
Thanks to everyone who has tried to help me!!

Under the advice of a friend's dad, I uninstalled Kubuntu and installed Ubuntu.
I was getting impatient while the system was booting, so I pressed my wifi hot key, and it worked! :D

I am very grateful to those of you who helped, thanks so much!

---

### Post by NCLI on 2010-08-19
Since Ubuntu and Kubuntu are basically the same thing, I guess the reinstall just fixed it :-S

---

### Post by Zorgoth on 2010-08-19
The fundamental problem was probably because you had a Broadcom network controller requiring special drivers.

---

### Post by Ms_Angel_D on 2010-08-19
brittlee, I'm glad you got it fixed and the internet is working for you. 

I would like to suggest some reading to help you better understand the system your using. Ubuntu/Windows/OSX they are all like cars and should all have some pre-instruction before being used.

[LIST]
[*][http://www.ubuntupocketguide.com](http://www.ubuntupocketguide.com)
[*][http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[*][http://www.ubuntugeek.com](http://www.ubuntugeek.com)
[*][https://help.ubuntu.com](https://help.ubuntu.com)
[*][http://www.howtoforge.com](http://www.howtoforge.com)
[*][http://www.ubuntu.com/support](http://www.ubuntu.com/support)
[/LIST]

The pocket guide I highly recommend it covers lot's of fundamental basics and you can download a free PDF copy from the site.

If you have any questions don't hesitate to ask.

Angel

---

