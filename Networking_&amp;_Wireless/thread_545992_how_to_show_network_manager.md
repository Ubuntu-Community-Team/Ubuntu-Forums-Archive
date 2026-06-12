---
title: "how to show network manager?"
date: 2007-09-08
forum: Networking &amp; Wireless
---

### Post by merlin666 on 2007-09-08
I have upgraded to Feisty because of the announced network manager feature. Now I have installed ndiswrapper and it looks like the wireless card is working, but I cannot find the network manager application. I have installed it from synaptic package manager as well as with aptitude. It is not available for panels either. How can I get this to show somewhere?

---

### Post by noob12 on 2007-09-08
Assuming you are using GNOME, you probably lack (and need to add) a startup entry in **System | Preferences | Sessions | Startup Programs**.  If you see a Startup Program labelled Network Manager, just enable it.  If you don't find it, then create one using New.
Name it **Network Manager** and set the command line to be **nm-applet --sm-disable**.

---

### Post by Larry.19 on 2007-09-08
Ok, it WAS ENABLED.
Now perhaps you could actually answer Merlin666's question ?
Where is it going to show up ?
On what menu or pull down ?
Please tell how to run it ?
That was, after all, the original question from Merlin666 !!!

---

### Post by noob12 on 2007-09-09
In the GNOME UI, it will normally show up in the top right panel (notification area) as a small dual computer icon.  When you are connected wireless, it changes to a series of signal strength bars.

---

### Post by merlin666 on 2007-09-10
> **noob12 said:**
> In the GNOME UI, it will normally show up in the top right panel (notification area) as a small dual computer icon.  When you are connected wireless, it changes to a series of signal strength bars.

Ok I got that, I think I was expecting something that shows a list of available networks. Anyway, I got the list of networks with iwlist scan - how can I connect to a specific network?

---

### Post by noob12 on 2007-09-10
Enable the wireless with the right mouse button on the NM icon.  Then click on the same NM icon with the left button.  You should see the list of networks there, select the one you want to connect to.

---

### Post by merlin666 on 2007-09-10
> **noob12 said:**
> Enable the wireless with the right mouse button on the NM icon.  Then click on the same NM icon with the left button.  You should see the list of networks there, select the one you want to connect to.

With the right button I get a menu with a properties option, and panel related options.

---

### Post by peterv6 on 2007-09-10
Guys,
I'm a newbie, and found this thread interesting.  I have the network manager enabled, but there is no dual computer icon in the notification area.  I am running Gnome.  Can any of you help me find out how to show it?

---

### Post by noob12 on 2007-09-10
Hmm.  That really doesn't sound like your clicking on the nm-applet icon then.  That sounds very much like you added the Network Monitor launcher to your panel.  Not the same.  Confusing though because it sounds the same, and the icon almost looks the same too.

Look in the right hand of the top panel near where your date and power button are (usually).  If you see a little dual computer icon or signal bars there, then use that one for your right and left clicks.  If you do not see one there, do this:  Type ALT+F2.  A command dialog comes up.  In the command
area, type  
```

nm-applet --sm-disable

```
and click RUN and watch the notication area in the right hand side of the top panel.  You should see the little dual-computer icon of NetworkManager appear there.

In my earlier posting I provided instructions on how to start nm-applet in your session startup.  That will make sure you don't have to run that command again manually.

If that is what was happening, and to avoid future confusion, you may want to remove the Network Monitor launcher from the panel.  I don't think you'll find it useful.

[Some would say the same for NetworkManager actually (a lot of people are switching to wicd)]

---

### Post by merlin666 on 2007-09-10
I had already added the nm-applet command to the startup list by editing the network manager entry. When Iremove the "network monitor" there is no other network related activity there.

---

### Post by noob12 on 2007-09-10
Can you check if it is running?
```

ps -ef | grep nm-applet | grep -v grep

```
See if that gives you output.  If so, it indicates it is running.  

If it is not running, then try the manual startup instructions I just provided.

If it is running, then I'm not sure why it isn't showing up for you.

---

### Post by merlin666 on 2007-09-10
I had three instances running, killed the two that I had started manually.

---

### Post by noob12 on 2007-09-10
I would try killing all 3 and starting one new one manually.  I have no clue why it isn't showing up for you.  Sorry.

---

### Post by merlin666 on 2007-09-11
I think I may have "deleted" the notification area a long, long time ago and just replaced with a panel, as I am also not getting any update signals etc. How can I check if I actually have a notification area installed, and if not, how to get it back?

---

### Post by noob12 on 2007-09-11
Ah now that would do it.

Right click on the panel,  select Add to Panel.  Then scroll down to the bottom section and find the Notification Area icon which has a little informational i symbol.  Select that.  Bingo?

---

### Post by merlin666 on 2007-09-11
Thanks, I did that and got a desktop search icon and a network icon. The network icon only works for the wired network. Right now I am connected wireless and the icon is black!

---

### Post by noob12 on 2007-09-11
OK.  Well, it sounds like you found your notification area and the NM icon.   

When you right click is there an Enable Wireless checkbox, and when you check that does the behavior change?   Your current behavior may be due to the type of device you have or it may be because you have manual configuration settings on the device.  NM will start managing the wireless if you put it in roaming mode (equivalent to commenting out or removing any configuration for that interface from /etc/network/interfaces).

I'm no NM proponent.  I'm just trying to explain how it works by the way.  I get the feeling when this is over, you will decide to switch to wicd.

What kind of wireless device and driver are you using?
 (**sudo lshw -C network** should show you)

---

### Post by merlin666 on 2007-09-12
I have done some manual configuration to enable WPA-PSK, as this may not be part of the NM I am wondering if that may be the issue. There is a checkmark on "enable networking". The device info is

*-network:0             
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: c
       bus info: pci@00:0c.0
       logical name: wlan0
       version: 03
       serial: 00:90:4b:8c:f9:e7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=,10/01/2002,3.70.17.5 ip=192.168.0.100 latency=64 link=yes multicast=yes wireless=IEEE 802.11g
       resources: iomemory:d0000000-d0001fff irq:18

and I am definitely connected to my wireless router.

What is wicd?

---

### Post by noob12 on 2007-09-12
I expect that you have the wpasupplicant package installed, and with that you should be able to allow NM and the gnome-keyring to manage the WPA-PSK key based on what network you are connecting to.

If you are always configuring everything manually, you may not need NM in the picture and you may find it gets in the way.

I use NM, but a lot of users are using wicd [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/), an alternate network connection manager.  I've never used it so I wouldn't be a good guide for that, and you may want to start another thread to get help on that if you decide to go that way.

---

