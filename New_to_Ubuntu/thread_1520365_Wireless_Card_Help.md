---
title: "Wireless Card Help"
date: 2010-06-29
forum: New to Ubuntu
---

### Post by Automag05 on 2010-06-29
Hi all, I am new to Ubuntu and am unable to connect to a wireless network. 

I have a "Broadcom Corporation BCM4312 802.11b/g" card in my laptop and was wondering if anyone could advise me on how I could get this set up to the internet.

Thanks in advance.

---

### Post by Crazedpsyc on 2010-06-29
If you have GNOME, just click the network applet at right side of the top panel and select whichever wireless network you want to connect to. If there is no network manager applet open, press Alt+F2 and type in  nm-applet <enter> and do the same from there. If you use KDE, sorry I'm not sure exactly, but it should be similar.

---

### Post by Automag05 on 2010-06-29
Thank you for the reply.
I am using gnome, my wireless applet is up,
but unfortunately I cannot locate a network. 

I right clicked on the wireless applet, hit network connections, went under wireless, but nothing is there. Perhaps I am looking in the wrong place?

---

### Post by matt-fender on 2010-06-29
Are you 100% sure the card has drivers installed for it?


When you left click the network icon do you have 2 headings? Wired network + Wireless Network

Right click your network icon and ensure that wireless is enabled as well as networking, restart, then try again?


Keep posting if you dont have any luck

---

### Post by Crazedpsyc on 2010-06-29
Yes, don't right click. that wireless thing is for seeing what networks have been connected to and editing them, not connectiong to new ones. if you left-click it shows a listing of all networks--wired and wireless-- and lets you connect to them by clicking on your choice

---

### Post by Automag05 on 2010-06-29
Thanks for the help guys, I have been frazzled looking for an answer for this delemna.

When I left click it the menu says "Wired Network, disconnected   , Wireless Networks, disconnected     ,   VPN connections, Connect to hidden wireless Network... , and Create new wireless network... "

I am not sure if that means I have drivers or where to get them if I need them

---

### Post by Crazedpsyc on 2010-06-29
[IMG]file:///home/mike/Desktop/Screenshot.png[/IMG]That means it found your wireless card and has drivers for it, but there are no wireless or wired networks to connect to. make sure your wireless card switch is on too, if you have one. I would be surprised if ubuntu couldn't use that card, since it can use my weird external usb wireless card! if you have windows or mac, try looking for the network there, just to make sure it works

the screenshot shows my network menu with the network names blacked out for privacy

---

### Post by Automag05 on 2010-06-29
I'm glad it at least has drivers... although that could have solved my issue.

I toggled my internet switch, but it remained the same.

And I do get internet on my other computer.

Mine looks like that, although my "disconnected" are not links like yours and I don't have the bars on my menu.

---

### Post by Crazedpsyc on 2010-06-29
those are not links, that is just my theme lol. hmmm... I'm Googlein'... Googlein'... just a min
what version of ubuntu do you have?
see if anything here is helpful: [http://ubuntuforums.org/showthread.php?t=1029731](http://ubuntuforums.org/showthread.php?t=1029731)
it looks like that specific device has had much trouble with ubuntu is the past (google "Broadcom Corporation BCM4312 802.11b/g ubuntu")

---

### Post by Automag05 on 2010-06-29
Oh hahaha!

I have version 10.04.

Wireless card - Broadcom Corporation BCM4312 802.11b/g

Thanks for your trouble in looking for this

---

### Post by matt-fender on 2010-06-29
Just out of curiosity could you post the output of iwconfig?

To do this open a Terminal 

Applications > Accessories > Terminal

type in "iwconfig" , hit enter...and post the magic ;)

---

### Post by Crazedpsyc on 2010-06-29
open system>administration>Hardware Drivers, and see what it says, if anything. someone said they just had to enable and disable the driver there and it worked
if it does this should make it automatically work when you boot
> 
When you start up, can you check and see if the wl driver is loaded?   From the Terminal:
     Code:
     lsmod | grep wl 
If nothing returns, try the following:
     Code:
     echo wl | sudo tee -a /etc/modules 
This will add the wl module to /etc/modules so that it is loaded  upon booting.  

Hope that helps.


---

### Post by Automag05 on 2010-06-29
I was reading the forum page that you sent me, typed lspci in the terminal, but acquired a bunch of jibberish for me. :)

I was surfing for "ndisgtk" that was mention of in the thread, in hopes that I could put it on a USB and then transfer it to my laptop, but got stumped on what to download.

I went to...

[http://packages.ubuntu.com/dapper/all/ndisgtk/download](http://packages.ubuntu.com/dapper/all/ndisgtk/download) 

but a lot of stuff came up that I wasn't sure what it all was.

---

### Post by Automag05 on 2010-06-29
When I type in the code "iwconifg"

The output is...

lo    no wireless extenstions.

eth0    no wireless extensions.

wlan      0IEEE 802.11bg ESSID off/any
             Mode:Managed Acess Point: Not-Associated  Tx-Power=0 dBm
             Retry long limit:7 RTS thr:  off
             Power Management: off


I scanned for drivers and it says that no proprietary drivers are in use on this system

---

### Post by Crazedpsyc on 2010-06-29
You should already have ndisgtk, just run sudo ndisgtk. but this doesn't look helpful to me. lspci doesnt seem useful either sorry.

UPDATE::: run
```

sudo apt-get install bcmwl-kernel-source

```
from the terminal and see if that helps. reboot may be necessary

---

### Post by Automag05 on 2010-06-29
I clicked Alt+F2 to run "sudo ndisgtk" but nothing popped up om my computer.

Does that perhaps mean that something went wrong during installation and that I perhaps don't have it?

If so do I need to download it?

---

### Post by Crazedpsyc on 2010-06-29
no, looks dumb anyway, bcmwl-kernel-source is a wireless driver for that series, so it should work

---

### Post by Automag05 on 2010-06-29
Oh really?
Okay, I definitely don't want dumb things on my computer.

My world of Ubuntu... :confused:

---

### Post by Automag05 on 2010-06-29
I'm going to bump this in hopes that anyone has an idea.

---

### Post by matt-fender on 2010-06-29
You can install the broadcom driver from the package manager which is

System > Administration > Synaptic Package Manager > Search for broadcom and you should find the package in there. Mark for installation and when it completes reboot, see if you have any luck doing that.

Could you ALSO, post the output of LSPCI for me? 

Applications > Accessories > Terminal > enter "lcpsi" and hit return

---

### Post by matt-fender on 2010-06-29
Try this in a terminal

sudo ifconfig wlan0 up

---

### Post by Crazedpsyc on 2010-06-29
Hey! any luck with any of that?

---

### Post by lkraemer on 2010-06-29
I'm wondering what a search of this forum for "HOWTO: Broadcom Wifi & Ubuntu 10.04 LTS" would find?  It might be interesting..............

lk

---

### Post by bkratz on 2010-06-29
> **Automag05 said:**
> I'm going to bump this in hopes that anyone has an idea.

Here is a recent thread about the same card with a possible solution

[http://ubuntuforums.org/showthread.php?t=1518083&highlight=BCM4312](http://ubuntuforums.org/showthread.php?t=1518083&highlight=BCM4312)

---

### Post by Automag05 on 2010-06-29
I went to look at the packages, and I believe I already have the boradcom package installed,

Here is the output of lspci:

00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b3)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 SATA controller: nVidia Corporation MCP79 AHCI Controller (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
02:00.0 VGA compatible controller: nVidia Corporation C79 [Quadro FX 470M] (rev b1)
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

---

### Post by Automag05 on 2010-06-29
Thanks guys, I am going to look into all of these,

I tried "sudo ifconfig wlan0 up" and when it asks me for a password, I for some reason cannot type anything. 

It's obvious the Ubuntu Gods are angry with me!

---

### Post by Automag05 on 2010-06-29
Eureka!

Viewed the link of the thread that was left and installed that internet card drive.
Sorry guys, didn't know I would have to be hooked onto ethernet.
Thank you so much for all of y'alls effort, I will now be able to enjoy my computer on the internet...

Not to mention I also installed a driver to put my computer in hd, don't know what difference it made, but I like the term "hd" being put with my computer.

This was an incredibly long confusing journey, but I feel like it was a good introduction to find out and get use to using Ubuntu interface. 

Thanks! :D

---

### Post by bkratz on 2010-06-29
> **Automag05 said:**
> Thanks guys, I am going to look into all of these,

I tried "sudo ifconfig wlan0 up" and when it asks me for a password, I for some reason cannot type anything. 

It's obvious the Ubuntu Gods are angry with me!

By the way when you use that password ( for a sudo command) it is never echoed to the terminal--just hit enter when done.  It really goes in there!

---

### Post by matt-fender on 2010-06-29
> **bkratz said:**
> By the way when you use that password ( for a sudo command) it is never echoed to the terminal--just hit enter when done.  It really goes in there!


hes right! 

when using a sudo command in terminal your password is never shown

---

### Post by anewguy on 2010-06-30
Just a note - ndisgtk is *not* useless, especially in some cases like this.  If the user has no way to hard wire their computer to do the sudo apt-get update, there won't be a driver in system/administration/hardware drivers.  Perhaps there is no Linux driver available for the adapter.  What ndisgtk does do quite well is that in cases like this, you can use the Windows XP drivers for the device via ndiswrapper, and ndisgtk in a GUI'd front end to ndiswrapper that takes a whole lot of typing and headaches out of the equation.  Contrary to what some people post, ndiswrapper, and the GUI'd front-end ndisgtk are still very valuable tools.

---

### Post by matt-fender on 2010-06-30
> **anewguy said:**
> Just a note - ndisgtk is *not* useless, especially in some cases like this.  If the user has no way to hard wire their computer to do the sudo apt-get update, there won't be a driver in system/administration/hardware drivers.  Perhaps there is no Linux driver available for the adapter.  What ndisgtk does do quite well is that in cases like this, you can use the Windows XP drivers for the device via ndiswrapper, and ndisgtk in a GUI'd front end to ndiswrapper that takes a whole lot of typing and headaches out of the equation.  Contrary to what some people post, ndiswrapper, and the GUI'd front-end ndisgtk are still very valuable tools.


^^^ I agree 110% as long as you use ndisgtk you're good to go!

---

