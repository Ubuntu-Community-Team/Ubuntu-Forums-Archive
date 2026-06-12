---
title: "how to CONNECT to WiFi"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by beanco on 2009-11-02
Hi All,

I got a new laptop at work, a lenovo SL500 or sg like that... The IT guys were more than happy to let me install Ubuntu, that worked otu fine, they set up the WiFi connect for me...

It worked for a couple of days, then I did sg, not sure what and now it does not work.

OK, the IT guys looked at it today, they were in  a hurry, could nto figure out what has happened and told me to google it.... fare enough since they were really busy... They did tell me that everything literally seems fine but they could not find out how to connect to the network...

yeha, all the settings were there, in the syst/admin/network... they could noly find the apply button, they tooled round for a bit and could not find a CONNECT button, they tried a few thigns from teh command line, no luck...

ok... I know this is not much helpful info... what do you need to know from me?

BTW.. this is a dual boot machine and on the windblows OS I can use the WiFi with no worries.

Thanks

robi

---

### Post by anewguy on 2009-11-02
I guess more information is in order:

- What kind of wireless adapter?  If you don't know, then go to a terminal window (applications/accessories/terminal) and then copy and post back here the output from:

lspci <press enter> 

lsusb <press enter>  Should only need to do this if a laptop, as some laptops have the wireless connected to an internal USB


- Are you running networkmanager?  Assuming "normal" Ubuntu (gnome desktop), look in the upper right on the top bar - is there anything like some vertical bars, or 2 computers, etc.?  If you click on these, do they show anything for available networks?

- The "did something" didn't include an upgrade to a newer version of Ubuntu did it (like 8.10 to 9.04, 9.04 to 9.10, etc.)?


I'm sure there is probably more we need to know, but let's start there.

Dave :)

---

### Post by danastasio on 2009-11-02
well what kind of adapter are you using? I know that belkin does not generally work with linux depending on what you are using.

---

### Post by beanco on 2009-11-06
> **danastasio said:**
> well what kind of adapter are you using? I know that belkin does not generally work with linux depending on what you are using.


Atheros !!!

Robi

---

### Post by beanco on 2009-11-06
Oh yeah, I am on 9.04

by *did something*  i mena I have no idea what happened since the connecttion was working.

I did try apt-get update but I think the connection was working after that....

In Windows there is an option, sg like, *connect to wireless network* that I choose when the computer detects a wireless network. But in ubuntu I cannot find anything like this....

Like I said the IT guys say the hardware is fine, it is working, they cannot find the *connect to...* button either..

robi

---

### Post by ukripper on 2009-11-06
Did you check if the wifi switch is turned on and light is coming up?

---

### Post by bumanie on 2009-11-06
Hello beanco. Is it an atheros wifi card or an atheros wifi adapter? I am assuming internal card. If so, what chipset does it use? Atheros have a number of chipsets. Post the output of > lspci.

---

### Post by beanco on 2009-11-06
> **ukripper said:**
> Did you check if the wifi switch is turned on and light is coming up?

well, if I can use the WiFi network when in Windows that means the swhithc is turned on right?

Bumaine, Atheros Wireless PCI Express Adaptor....

I ran lspci but no way of getting the output off the computer and I do not feel like typing it all in here..., kin dof hard during meetings to type that much with out getting caught

robi

---

### Post by ukripper on 2009-11-06
> **beanco said:**
> well, if I can use the WiFi network when in Windows that means the swhithc is turned on right?



Sorry didn't read that bit before.

---

### Post by beanco on 2009-11-06
FOlks,

I log onto the Windows partition and use the WiFi network no worries, I log onto Ubuntu and I cannot use it, I do not know how to actually connect to it. There was an icon but it is gone now.

robi

---

### Post by k33bz on 2009-11-06
> **beanco said:**
> FOlks,

I log onto the Windows partition and use the WiFi network no worries, I log onto Ubuntu and I cannot use it, I do not know how to actually connect to it. There was an icon but it is gone now.

robi

It is hard to help you with out knowing the specs. Please do this:

Go to Applications
This will pull up a menu, now you will need to go to Accessories and click on Terminal. Once the terminal is loaded up copy and paste this command:
```
lspci
```

Once you do this your terminal will print out alot of info. Copy and paste that info into this thread.

---

### Post by beanco on 2009-11-06
> **k33bz said:**
> It is hard to help you with out knowing the specs. Please do this:

Go to Applications
This will pull up a menu, now you will need to go to Accessories and click on Terminal. Once the terminal is loaded up copy and paste this command:
```
lspci
```

Once you do this your terminal will print out alot of info. Copy and paste that info into this thread.

well, i am on the window partition right now because I cannot get to this forum from the ubuntu one.


So, how can I get this info via Windows?

---

### Post by beanco on 2009-11-06
Here is the result
```

robi@ubuntu:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09) 
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09) 
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09) 
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03) 
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03) 
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03) 
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03) 
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03) 
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03) 
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03) 
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03) 
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03) 
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03) 
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03) 
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) 
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03) 
00:1f.2 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03) 
00:1f.5 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03) 
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01) 
0c:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02) 
0d:00.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) 
0d:00.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) 
0d:00.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12) 
0d:00.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12) 
robi@ubuntu:~$ robi@ubuntu:~$ lspci 
bash: robi@ubuntu:~$: command not found 
robi@ubuntu:~$ 00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09) 
bash: syntax error near unexpected token `(' 
robi@ubuntu:~$ 00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09) 
bash: syntax error near unexpected token `(' 
robi@ubuntu:~$ 00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09) 
bash: syntax error near unexpected token `(' 
robi@ubuntu:~$ 00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03) 
bash: syntax error near unexpected token `(' 
robi@ubuntu:~$ 00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03) 
bash: syntax error near unexpected token `(' 
robi@ubuntu:~$ 00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03) 
bash: syntax error near unexpected token `(' 
robi@ubuntu:~$ 00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) 
bash: syntax error near unexpected token `(' 
robi@ubuntu:~$ 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03) 
bash: syntax error near unexpected token `(' 
robi@ubuntu:~$ 00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03) 
bash: syntax error near unexpected token `(' 
robi@ubuntu:~$ 00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03) 
bash: syntax error near unexpected token `(' 
robi@ubuntu:~$ robi@ubuntu:~$ lspci 
bash: robi@ubuntu:~$: command not found 
robi@ubuntu:~$ 00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09) 
bash: syntax error near unexpected token `(' 
robi@ubuntu:~$ 00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09) 
bash: syntax error near unexpected token `(' 
robi@ubuntu:~$ 00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09) 
bash: syntax error near unexpected token `(' 
robi@ubuntu:~$ 00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03) 
bash: syntax error near unexpected token `(' 
robi@ubuntu:~$ 00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03) 
bash: syntax error near unexpected token `(' 
robi@ubuntu:~$ 00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03) 
bash: syntax error near unexpected token `(' 
robi@ubuntu:~$ 00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) 
bash: syntax error near unexpected token `(' 
robi@ubuntu:~$ 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03) 
bash: syntax error near unexpected token `(' 
robi@ubuntu:~$ 00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03) 
bash: syntax error near unexpected token `(' 
robi@ubuntu:~$ 00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03) 
bash: syntax error near unexpected token `(' 
robi@ubuntu:~$ 

```

---

### Post by ukripper on 2009-11-06
> 02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01) 


This may help - [http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html)

---

### Post by 3rdalbum on 2009-11-06
> **beanco said:**
> I log onto the Windows partition and use the WiFi network no worries, I log onto Ubuntu and I cannot use it, I do not know how to actually connect to it. **There was an icon but it is gone now.**

That's what I was about to ask you!

It sounds like you're missing the Network Manager applet. It's actually a little program called "nm-applet" that runs inside a part of your Gnome panel called the "Notification Area".

Go to your top panel and right-click on an empty area of it. Choose "Add to Panel" and go down to Notification Area and click the Add button.

As the icon appeared now? If so, then click on it and connect to your network (assuming what the IT guys did hasn't completely mucked up your system, lol).

If the icon hasn't appeared, or if you've recieved an error message that there's already a notification area, then you may need to run the nm-applet program manually.

Hit Alt-F2 and type:

```
nm-applet
```

Click OK, and the icon should appear in your notification area. Click it and connect like usual.

---

### Post by beanco on 2009-11-10
thanks for the info.

I ran the applet manually as taht was faster but to no avial. so I tried the right click option and the icon apperaed, I am trying to connect to the WiFi now... might have to move as the signal is usually weak here.

UKripper, i will read that link because I always like to learn stuff....

robi

---

### Post by beanco on 2009-12-02
The saga goes on.

There are several of use at work that cannot use the WiFi.. ie. we cannot connect... often... 

so, sometimes I get lucky and make a connecgtion, but more often then not it does not ... keeps stalling out when authenticating (or whatever it is in English) and adress...

If I unplugg the WiFi router, pug it back in I can connect... obvously this is not a good solution... besides messing up anybody who might be using that router I only have physical access to one router... in the other parts of the building there is no way for me to unplug/plug in the routers, ever if I wanted to...

This happens in XP as well, so it is not an OS related issue.

The IT dude has not idea how to fix this problem....

robi

---

### Post by beanco on 2010-01-15
I have given up on this.

I can use the laptop here at home.

I can access the WiFi network here at home.

At work I cannot. I have not been able to connect using Ubuntu or XP for weeks.

some co workers manage to log on once in a while, some regularly, some, like me never. We all have the same lenovo sl500... two of us are on Ubuntu/XP machines, everbody else is XP only....

Robi

---

### Post by theozzlives on 2010-01-15
Sounds like you guys need a new IT dude.

---

