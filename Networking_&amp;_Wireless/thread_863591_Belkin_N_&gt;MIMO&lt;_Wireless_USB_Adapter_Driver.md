---
title: "Belkin N &gt;MIMO&lt; Wireless USB Adapter Driver"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by GavinRoskamp on 2008-07-18
Hello linux users.

This is my first thread actually giving advice instead of asking for it :D

This thread is for the Belkin N (MIMO) Wireless USB Adapter. I can tell you how to easily get your belkin wireless device to work in Ubuntu! (I´m running Hardy Heron)

Without further ado, we need to get the show on the road. Make sure you have ndisgtk (part of ndiswrapper) I believe you can get it in synaptic.
After installation, it will be Administrator>Windows Wireless Drivers. Alternatively, you can use termanal and type ¨sudo ndisgtk¨ then your password.

Insert your Belkin CD into your CD drive. The CD has the .inf file needed to use it. Open up ndisgtk and click add driver. Click on the folder icon and locate your CD drive. Go to the ¨InstallationDrivers¨ folder. Go to ¨XP2K¨ and open the ¨rt2870.inf¨ file. It will say that the hardware is not present, but don´t worry. Reboot your computer with your USB device already attached and DO NOT UNPLUG IT. At least mine doesn´t work if you unplug it. :)

Now whenever you start your computer, you will have wireless! Use the networkmanager in your tray to choose a network.

Hope I could help!

-GavinRoskamp [email]Gavinstipsandtricks@gmail.com[/email] [www.GavinsTipsAndTricks.co.nr](www.GavinsTipsAndTricks.co.nr)

---

### Post by timstone on 2008-10-01
OK, I'm sort of a noob when it comes to linux.  But I have dabbled with it a bit years ago.  I'd like to put Ubuntu on my PC I'm using now, but for now I've got it installed on an older PC til I know everything is worked out and working fine.

I did everything you said in your post and the adapter is recognized by the system, but for some strange reason it's not connecting to the network.  I've changed the SSID and the security key but nothing seems to work.  Am I doing something wrong or is there a different way I can problem solve it?

---

### Post by Bobbyrne01 on 2008-12-03
Brillant, this fixed the problem for me!! I have a Wireless G+ MIMO Usb Adaptor (Belkin) and now it works perfect after doing what GavinRoskamp said!! Thanks :D

I wouldntve known what to do only for the "sudo ndisgtk" command



Thank You:D

---

### Post by spcwingo on 2008-12-03
You shouldn't have to reboot.  Just open a terminal and type:

```
sudo modprobe ndiswrapper
```

---

### Post by cgm on 2009-02-02
Thank you very much for this info. Worked perfectly and didn't even have to restart my PC!

---

### Post by ksherlock on 2009-02-05
> **GavinRoskamp said:**
> Hello linux users.

This is my first thread actually giving advice instead of asking for it :D

This thread is for the Belkin N (MIMO) Wireless USB Adapter. I can tell you how to easily get your belkin wireless device to work in Ubuntu! (I´m running Hardy Heron)

Without further ado, we need to get the show on the road. Make sure you have ndisgtk (part of ndiswrapper) I believe you can get it in synaptic.
After installation, it will be Administrator>Windows Wireless Drivers. Alternatively, you can use termanal and type ¨sudo ndisgtk¨ then your password.

Insert your Belkin CD into your CD drive. The CD has the .inf file needed to use it. Open up ndisgtk and click add driver. Click on the folder icon and locate your CD drive. Go to the ¨InstallationDrivers¨ folder. Go to ¨XP2K¨ and open the ¨rt2870.inf¨ file. It will say that the hardware is not present, but don´t worry. Reboot your computer with your USB device already attached and DO NOT UNPLUG IT. At least mine doesn´t work if you unplug it. :)

Now whenever you start your computer, you will have wireless! Use the networkmanager in your tray to choose a network.

Hope I could help!

-GavinRoskamp [email]Gavinstipsandtricks@gmail.com[/email] [www.GavinsTipsAndTricks.co.nr](www.GavinsTipsAndTricks.co.nr)
Hello
After following your directions when it comes to rt2870.inf I do not see it the only ones are rt2870.cat and rt2870.sys. What can I do?

---

### Post by TheLastExodus on 2009-04-05
I fallowed the steps but it seams that the wifi utility isn't showing any networks in range :/ though would it be a problem if I have a netgear wifi adapter in my computer aswell?

edit
Oh ya i'm on 8.10 64bit an it just seams that its not seeing  the adapter when its plugged in :/

---

### Post by Dillon02003 on 2009-04-24
[FONT=Arial]Ok, so here is my problem.

it detects the adapter but shows no connections to choose from.

What the heck do I do?[/FONT] :confused::confused:

EDIT: I know there is one because I have a wireless modem in another room and when I use my dual-booted Vista , there is a connection to choose from...

---

### Post by tcorneli on 2009-05-16
:idea: I would like to add that it if you're using a 64 bit version of Ubuntu, you might want to select the XP64 driver instead of the XP2K one. That's what was necessary for me.

Cheers :)

---

### Post by dBLiSS on 2009-09-02
I followed these steps and it connects fine to one of my routers. A B/G one. I have a second router that is just set to N and it will not connect. Is there some way to enable N connectivity?

---

### Post by DrLFToxic on 2009-10-30
> **GavinRoskamp said:**
> Hello linux users.
 
This is my first thread actually giving advice instead of asking for it :D
 
This thread is for the Belkin N (MIMO) Wireless USB Adapter. I can tell you how to easily get your belkin wireless device to work in Ubuntu! (I´m running Hardy Heron)
 
Without further ado, we need to get the show on the road. Make sure you have ndisgtk (part of ndiswrapper) I believe you can get it in synaptic.
After installation, it will be Administrator>Windows Wireless Drivers. Alternatively, you can use termanal and type ¨sudo ndisgtk¨ then your password.
 
Insert your Belkin CD into your CD drive. The CD has the .inf file needed to use it. Open up ndisgtk and click add driver. Click on the folder icon and locate your CD drive. Go to the ¨InstallationDrivers¨ folder. Go to ¨XP2K¨ and open the ¨rt2870.inf¨ file. It will say that the hardware is not present, but don´t worry. Reboot your computer with your USB device already attached and DO NOT UNPLUG IT. At least mine doesn´t work if you unplug it. :)
 
Now whenever you start your computer, you will have wireless! Use the networkmanager in your tray to choose a network.
 
Hope I could help!
 
-GavinRoskamp [EMAIL="Gavinstipsandtricks@gmail.com"]Gavinstipsandtricks@gmail.com[/EMAIL] [www.GavinsTipsAndTricks.co.nr]("http://www.GavinsTipsAndTricks.co.nr")
 
 
After following these exact steps, my USB Belin N Band MIMO (model 3000x) works...but for a short time.
 
it works for aprox. an hour, then its like the dongle freezes. the network traffic stops and i cant connect to another network. when i try to connect to another network/reconnect to the network, the light doesnt flash or anything. any ideas because im trying to make ubuntu 9.10 my primary os, so i can get rid of vista.. (i cant stand vista now i have tasted ubuntu 9.10).
 
thanks in advance..
 
Toxic

---

### Post by joshuntu on 2009-11-04
I have a Belkin N driver and just did a clean install of ubuntu 9,1 on my fathers computer. I tried to follow your direction however i was unable to locate the .inf file in the instalation disk. I tried with a different antena and instalation cd and found it and "installed" the driver (even though in the end it didnt work) but in the Belkin instalation cd there isn't an .inf driver present. what should I do? thank you for the help.

Josh

---

### Post by jastonas on 2009-11-13
For those who cannot see networks. I think i came across a solution to that, something that has to do with disabling "stuff".. google it and test it and let us know. My Belkin doesnt work at all for now but I am trying to find a solution without ndiswrapper.

Edit: I think they are talking about the "cant see networks problem" here [http://art.ubuntuforums.org/showthread.php?t=1304892&page=2](http://art.ubuntuforums.org/showthread.php?t=1304892&page=2)

---

### Post by mgphl52 on 2009-11-16
I too couldn't find any .inf files on the CD but I did download a drivers.exe from Belkin and unzipped it into a directory. However, I get "invalid driver" from ndisgtk on every .inf file... (This is from LinuxMint 7.0).

I currently have powerline-ethernet adapters running again but they are much slower than my wireless connection (router's downstairs due to cable outlet). Any "fresh" suggestions?

-michael

PS: The USB adapter works fine from windoze XP...

---

### Post by mercuryrune on 2009-11-17
How are you guys even getting network manager to see your belkins?
I can't even get THAT far.

I'm running 9.10 Karmic, and network-manager is completely grayed out.   I'm using a Belkin F5D8053 pre-n Wireless USB adapter, and after doing the whole ndiswrapper/gtk dance, I can install any of the three seperate driversets for the model (net8192u, rt2870, netr28u) and have them install no-problem, but after doing a modprobe they still remain inactive, and network-manager will not acknowledge them, even though the wireless usb device does appear under a lsusb as wlan0 (001:003 | 050d:805e).

Any clues to help me out with getting my wireless usb adapter to work with ubuntu?

(and for the record, I do have win7 on another drive and it works fine on it...)

---

### Post by sks24 on 2010-01-26
Well, here's what I'm getting with the Belkin N wireless (MIMO)adapter, and any suggestions appreciated.

I'm running a fresh wubi 9.10 install.

All the networks that normally show up on my other computer are recognized, as is my own.  However, when I type in my key in the Network Authentication box, it can't connect to my wi-fi network.

After a minute or so of trying it cycles back to the "Authentication Required" box.  

I ran "sudo modprob ndiswrapper". Result: command not found.

Any ideas?  Seems like I'm so close!

Thanks in advance,
Scott

---

### Post by sks24 on 2010-01-26
I did, btw, type "probe" and not "prob".

---

### Post by Cfossy2 on 2010-02-01
One thing you may want to check is if UTW (firewall) is activated as it can stop you from connecting to your network.If it is running then disable it initially then either restart it or try another firewall, I have Firestarter as my own firewall as it is easy to configure. Also check to see if there are any other Firewalls running and if the network card is activated. If not then activate through the GUI. Also check to make sure that your security settings, either WEP or WPA are setup properly, as otherwise you will not be able to authenticate the card with the router.These are just a few things that I have found to be problems. BTW I am currently running Karmic Koala with a Belkin router and wireless 54G PCI card.

---

### Post by rannel on 2010-05-03
I followed your steps and mine wireless netowork driver says invalid driver
and though i now have a blue light coming from my adaptor im still not connected to the internet and my wireless network controls say nothing about the adaptor

---

### Post by frozenmafia on 2010-08-03
hmm, I can't seem to do the sudo command, It says: command not found.

Any help? I need it fast so that I can run my website again :(

---

### Post by frozenmafia on 2010-08-03
Josh: Goto installationfiles > drivers it's all in there

---

