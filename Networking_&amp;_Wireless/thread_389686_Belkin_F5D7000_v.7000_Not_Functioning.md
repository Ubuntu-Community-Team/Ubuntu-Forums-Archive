---
title: "Belkin F5D7000 v.7000 Not Functioning"
date: 2007-03-21
forum: Networking &amp; Wireless
---

### Post by BluJai on 2007-03-21
Problem Summary:
After miserably failing to get a SMC wireless card to be recognized and installed, I replaced it with a brand new Belkin F5D7000 v.7000. It uses an Realtek 8185L chipset (as confirmed by visibly inspecting the card). According to many things I have read, the chipset should work just fine (possibly without installing any additional drivers). However, that is not the case.

The card was not immediately recognized and only the on-board dial-up modem is recognized in System/Administration/Network. I installed Ndiswrapper and now, after following all the steps I can find, it appears set up correctly in Ndiswrapper, but wlan0 shows up nowhere but there.

Current Status:
I have tried the Ndiswrapper steps from [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy). The driver shows up as driver installed, hardware present. However, wlan0 doesn't show up anywhere (nor is it under any other name). The only reference to it I can find is in (IIRC) a config file for Ndiswrapper which lists alias wlan0.


Final Notes:
I'm completely confused. It looks like (according to [https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion](https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion)) that this card should work just fine. As of v.5000 it is supported natively. Additionally, immediately below the card in question a CompUSA Realtek 8185L shows up as being supported "out of the box" also.

I have spent over 5 hours trying to get this working so far. The PC is in a location which makes connecting it via Ethernet a non-option. Any help provided will be greatly appreciated!!!!


*BTW, I am (of course) not at the Ubuntu 6.10 machine having the issue right now, so not all screen references are 100% accurate. Additionally, I am an IT Professional, but a Linux newbie, so please excuse my incorrect terminology.*

---

### Post by Floppyjoe on 2007-03-21
This thread may prove useful to you:

[http://www.ubuntuforums.org/showthread.php?t=380285&highlight=F5D7000](http://www.ubuntuforums.org/showthread.php?t=380285&highlight=F5D7000)

---

### Post by BluJai on 2007-03-28
Having the linux-restricted package installed did not help. I even tried using the beta of Feisty Fawn, but though its graphical ndiswrapper front end could install the driver, it never worked properly.

Solution Reached:
I returned the Belkin F5D7000 and purchased a **D-Link WDA-1320**. It worked like a charm! I did a fresh install of Edgy Eft and didn't have to configure the card at all (aside from SSID & WEP password).
:guitar: Perfect performance with the D-Link card!

---

### Post by woro2006 on 2007-04-18
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true")

Download the windows xp version of net8185.inf

Extract the file into a directory of your choice. 

install the driver
ndiswrapper -i net8185.inf
update the driver with the PCI ID
ndiswrapper -a 1799:700f net8185
restart the computer. 
then ndiswrapper -l should show that it exists.
net8185 : driver installed
        device (1799:700F) present
then configure it through System>Admin>Networking

---

### Post by Pha3drus on 2007-05-13
I was able to get my wireless card working with the above instructions, however I'd like to set it up so it loads the driver at boot up. I have to enter "sudo modprobe ndiswrapper" every time I boot up to get it to work. 

That's not a big deal by itself, but I'm running a file server for a bunch of people that don't know linux at all. I'd like to just be able to hit the power button and have access to my samba shares.

ndiswrapper -m doesn't work.  Neither did adding "ndiswrapper" to /etc/modules. 
In both cases, ifconfig brings up "wlan0", but the card is inoperable, and my computer actually slows down to a crawl. 

I think ndiswrapper has to be modprobed after login to work. Anyone know how to do this automatically?


Update:
I've noticed  a few other things that affect ndiswrapper. After I changed my default sound card, the wireless immediately stopped working, and I had to completely reload the wireless driver. I'm using an Audigy 2ZS, and it's also a PCI card. No idea what that was all about. 

Another thing is that I've found some posts that tell you to enter "sudo depmod -a" before you enter "sudo modprobe ndiswrapper". I've found that it works better if you enter "sudo depmod -a" right before you reboot, in the above steps.

---

### Post by Dark Shogun on 2007-05-16
Hi I'm new to linux, just installed Ubuntu 7.04 last night. Been trying to get the hardware working but for some reason it just will not work. I also have the Belkin f5d7000. I did everything that was supposed to be done.
ndiswrapper -l returns that i have my driver and hardware present, but for some reason my network configuration wont see it. All iwconfig returns is that lo has no wireless connections and eth0 has no wireless connections.
I keep seeing people that say to config wlan0, that device doesnt even exist for some reason on this linux. What do you suggest?

---

### Post by netreg on 2007-05-17
> **woro2006 said:**
> [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true")

Download the windows xp version of net8185.inf

Extract the file into a directory of your choice. 

install the driver
ndiswrapper -i net8185.inf
update the driver with the PCI ID
ndiswrapper -a 1799:700f net8185
restart the computer. 
then ndiswrapper -l should show that it exists.
net8185 : driver installed
        device (1799:700F) present
then configure it through System>Admin>Networking

Hi guys,

i followed the above instructions.   When i enter the command ndiswrapper -l i just get net8185: driver installed

I dont get the device present...

i'm not sure what to do/try next

thanks
Darren

---

### Post by him610 on 2007-10-10
Hello to all who have posted to this thread and anyone else who may read it.

Success

Initially, I had thought my Belkin card had the bcm4306 driver, and having had success with installing that one another system with a Linksys mpc54g, I tried the same routine again - no joy. Reconfigured, started over again from the beginning; a search on "700f" led me to this thread.  

I followed the instructions to the letter posted by woro2006 in reply #4; it worked. At first, I didn't think it had, but sometimes you just have to let things cook a little while. When I booted up tonight, there it was, 192.168.1.7, just underneath 192.168.1.8, my wired connection - just beautiful, makes one happy to be alive.

The system is homebuilt with a Tyan S2390 mainboard, a 850 MHz Athlon,  768 MB RAM, Ubuntu 7.04 installed using Wubi-installer. My router is a Belkin N Wireless Router. I bought both the router and the F5D7000 wireless card at our local Walmart store.

Cheers,
A happy camper :)

---

### Post by Vadi on 2007-10-16
> **netreg said:**
> Hi guys,

i followed the above instructions.   When i enter the command ndiswrapper -l i just get net8185: driver installed

I dont get the device present...

i'm not sure what to do/try next

thanks
Darren

I had the same problem. I uninstalled the driver then, put sudo before all commands, and it said device present!

---

### Post by Dark Shogun on 2007-10-26
i found out how to fix it. After following said directions.. do the following as root:
ndiswrapper -m
modprobe ndiswrapper

---

### Post by Vadi on 2007-10-26
Ahh, yeah that was most likely the case.

---

### Post by Barge on 2007-10-29
Hi I've got this card also and having trouble installing it in Gutsy. Near total noob too, although I have successfully broken a couple of fedoras/SuSEs/Ubuntus in the past. ;)

I had previously installed my WG111V2 usb card using ndiswrapper and thought it successfully uninstalled (plus removed).

I get to the point of having:

[I]net8185 : driver installed
device (1799:700F) present[/I]

when I **ndiswrapper -l**

However no wireless network appears in the Network Settings tool.

Running **lshw -C network** as suggested in another thread yields:

[I] *-network UNCLAIMED     
       description: Ethernet controller
       product: Belkin
       vendor: Belkin
       physical id: 7
       bus info: pci@0000:01:07.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64 maxlatency=64 mingnt=32[/I]

Now I understand I now need to stop this being in UNCLAIMED status somehow so that it will register as wlan0, I just have no idea how to go about that. Oh and I tried the other steps mentioned in this thread (without success) of doing
[B]
ndiswrapper -m
modprobe ndiswrapper[/B]

I'm sure I've messed something up somewhere, probably when attempting to install or uninstall the wg111 with ndiswrapper, I just don't know how to unbreak it. Any advice greatly appreciated. :D

---

### Post by Vadi on 2007-10-29
Heh, I had this same problem too.

Do **sudo ifconfig wlan0 up**, I think that's the syntax to claim it. After that, get WICD, and it'll work fine.

---

### Post by Barge on 2007-10-30
Heh thanks for that, I've taken a couple of steps back, I decided to try the x64 version of the driver last thing last night, being I'm running gutsy x64 (net8185x64.inf). Ubuntu wouldn't start so I removed the pci card and uninstalled the driver. I am now trying to get back to where I was with the 32bit driver and having a couple of problems. Going to uninstall ndiswrapper and reinstall following a procedure I saw elsewhere on the forum and take it from there.

There's no crisis, I can afford to play, Windows is still my main OS (for now) and I have an emergency blue cable I'm using with ubuntu.

EDIT: Back to how I was before, driver marked as installed, hardware present, but the network is unclaimed. sudo ifconfig wlan0 up returns wlan0: ERROR while getting interface flags: No such device I'm looking into wicd but the way I see it a different network manager won't fix anything until I get it finding wlan0. Time to keep playing. :D

---

### Post by Barge on 2007-10-30
Fixed it (sort of)

Uninstalled ndiswrapper fully, reinstalled, applied the 64 bit winxp driver as outlined for the 32 bit driver in this thread, network manager flashed up with 3 networks straight away, rebooted once successfully to try to connect to mine with wpa, no luck, got wicd and still had no luck connecting.

Rebooted again and was back to my old situation with this driver of ubuntu freezing halfway through boot (left for 5 mins).

I've decided since its a fairly fresh install to save myself some potential future headaches like this and go to 32 bit ubuntu before I get too deep in setting it to my liking, heh.

So yeah my experience here was that I couldn't get net8185.inf installed successfully in ubuntux64 despite it saying the device was installed. I got limited action with net8185x64.inf but it was unstable for me, ymmv.

---

### Post by Vadi on 2007-10-30
It actually doesn't freeze but takes a while before it realizes it can't connect to anything, and then continues booting.

I'm pretty sure that you needed to get that ifconfig <some random name> up to claim it, I just picked wlan0 because I remember it being so. You could try "wifi" as a name or something.

---

### Post by Barge on 2007-10-30
Up and running just like that in the new install, signal strengths, etc. Following the steps in this thread got me there this time.

---

### Post by Vadi on 2007-10-30
Nice :)

---

