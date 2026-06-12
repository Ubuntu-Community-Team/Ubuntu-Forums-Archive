---
title: "BCM4306 connects, sees all networks, but drops signal every few minutes"
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by pjizz on 2008-11-27
Hi all,

I just recently switched from Xubuntu on my laptop because it seemed to enjoy freezing during class.  But now I have Intrepid up and running perfectly, set up the wireless card in a flash and just want to smash my head in the wall everytime I click a link, because that's basically how long my internet lasts: just long enough to load one page.  To fix it, I just click the nm-applet icon and reconnect, but you can imagine how frustrating this is...like restarting your care everytime you take a turn.

All the help I seem to be able to find deals with how to get the card up and running in the first place, so I thought I'd start a new thread.  I've got to believe someone else out there is having this same problem.

Thanks to all helpers!

-pjizz

---

### Post by pjizz on 2008-11-27
an MSPaint of my pain...

---

### Post by pjizz on 2008-11-29
bump bump

...this problem went away for a while, but is now back in full fury....also, the picture i put up was the wrong one, but really all it showed was my nm-applet tooltip reporting 86% connection while firefox reported the ever-annoying "can't establish a connection"

this is so verrrrry annoying, so please, anyone with even an idea or suggestion, love to hear it...

thx

---

### Post by J172 on 2008-11-29
Does this happen constantly (even after a restart, etc).
Does this happen with any other router?
Does this only occur wirelessly?
Does this model router have a history of this issue or need a firmware update?
Maybe a restart?

Post answers or use those to consult google. I'd be happy to help.

P.S. Love the theme, what is it?

---

### Post by kevdog on 2008-11-29
What driver are you using??  This would make all the difference!!

---

### Post by coskierken on 2008-11-29
STill having the problem?  I recently loaded a friends ole' P4 laptop and it had the bcm4306.  I wanted to use it as a frisbee!  Even though I was using ndisgtk (gtk version of ndiswrapper... its in Synaptic) and using the win ini file, the b43 driver kept showing up (lshw -C network). If I manually unloaded and reloaded it, it would work great.  below is what I did and it seemed to work.

Get the bcmwl5 inf and sys files and put them somewhere (home dir is fine in its own folder) These are all you need.  You can put the entire driver folder there, but it is not needed.  

Install NDISGTK with associated files
Run from terminal: sudo ndisgtk and find your drivers folder you created
Make sure that ndisgtk put a line in your: /etc/modules file by:
sudo gedit /etc/modules

There should be a line with just "ndiswrapper"
If it is not there, just put it there and save.

In a terminal window, try the commands right below.  

sudo modprobe -r b43
sudo modprobe -r ssb
sudo modprobe -r b43legacy
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper

If it works and your connection stays, you know you where having conflicts with one of the modules Intrepid loads (b43,ssb or b43legacy)

For some reason, I had to load and remove the ndiswrapper twice to get it to work. 

If it works, create a file:  sudo gedit wireless (any name will do)

Put all the commands in the file.
 
Save the file as a text file and change the properties to run as an executable 

Now, if you have confirmed it works and you want it to initialize on start up (you won't have to put your password in), put the file in the /etc/init.d folder.  It might tell you have an lsb header error, but it will still run.  

One last step I did was to blacklist the b43,ssb, and b43legacy.

The easy way: sudo gedit /etc/modprob.d/blacklist
Look for a line which says: blacklist bcm43xx
Just repeat the blacklist for b43, ssb, and b43legacy (one line each)

Let me know if it works for you.  There are probably better ways to do this, but I am a newbie.

---

### Post by pjizz on 2008-11-29
this doesn't happen constantly, but when it happens it happens alot.
it is definitely only with wireless, but I haven't had a chance to take it and try with a diff router yet, so I'll have to report back on that.
the router is at my girlfriend's, and it never has any problems with her shiny childish mac

as for my driver, i'm pretty sure I've got the b43, but I'm not sure the process by which I got it.  I've had some troubles from this old machine, and after switching from Xubuntu to Mandriva to SUSE to now Ubuntu, I've forgotten the process I used for this install to get the wireless up.  I have intrepid, so it has the restricted drivers GUI and I know I have the b43 activated there, but it reports two seemingly contradictory things "No proprietary drivers are in use on this system" at the top, but "this driver [b43] is activated and currently in use" at the bottom, so I'm not for sure if it's actually being used or not.

also, in case anyone wants to explain a related issue to me, I am never sure what networks I need to look at.  in terminal outputs it always seems like i have several instead of 2, just wireless and wired.  here's what I'm talking about

```
bander@bander-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:a7:82:d9
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5705-v3.16 latency=32 mingnt=64 module=tg3 multicast=yes
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:96:b8:22:50
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.2.6 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 6e:b5:f9:5d:ef:cd
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
bander@bander-laptop:~$ sudo lshw -C network | less
bander@bander-laptop:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:a7:82:d9
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 firmware=5705-v3.16 latency=32 link=no mingnt=64 module=tg3 multicast=yes port=twisted pair
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:96:b8:22:50
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.2.6 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 6e:b5:f9:5d:ef:cd
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

so from that, I can't tell if network 1 is my ethernet or wireless, and if network 0 is wireless or ethernet.  just confused on this...probably my unfamiliarity with hardware.

oh, and the theme is just a tiny modification of DarkRoom...I called it chocolate

---

### Post by pjizz on 2008-11-29
okay quick update.

i went back to the "Hardware Drivers" dialog and deactivated the "Broadcom B43 wireless driver"....the wireless still works initially, but then has the same hang up issues.  so apparently i'm not using the b43??  thoroughly confused.

---

### Post by pjizz on 2008-11-29
coskierken: followed those instructions and now i have no wireless at all.  so i don't think is my solution...

---

### Post by rpaco on 2008-11-29
I have almost the same problem, under 8.10 my old Dell Latitude 600 Laptop disconnects every few seconds and very often latches on to another network from a house down the road, its driving me mad. :mad:

  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth1
       version: 04
       serial: 00:04:23:63:06:47
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 ip=192.168.1.3 latency=32 link=yes maxlatency=34 mingnt=2 module=ipw2100 multicast=yes wireless=IEEE 802.11b

---

### Post by J172 on 2008-11-29
> **coskierken said:**
> STill having the problem?  I recently loaded a friends ole' P4 laptop and it had the bcm4306.  I wanted to use it as a frisbee!  Even though I was using ndisgtk (gtk version of ndiswrapper... its in Synaptic) and using the win ini file, the b43 driver kept showing up (lshw -C network). If I manually unloaded and reloaded it, it would work great.  below is what I did and it seemed to work.

Get the bcmwl5 inf and sys files and put them somewhere (home dir is fine in its own folder) These are all you need.  You can put the entire driver folder there, but it is not needed.  

Install NDISGTK with associated files
Run from terminal: sudo ndisgtk and find your drivers folder you created
Make sure that ndisgtk put a line in your: /etc/modules file by:
sudo gedit /etc/modules

There should be a line with just "ndiswrapper"
If it is not there, just put it there and save.

In a terminal window, try the commands right below.  

sudo modprobe -r b43
sudo modprobe -r ssb
sudo modprobe -r b43legacy
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper

If it works and your connection stays, you know you where having conflicts with one of the modules Intrepid loads (b43,ssb or b43legacy)

For some reason, I had to load and remove the ndiswrapper twice to get it to work. 

If it works, create a file:  sudo gedit wireless (any name will do)

Put all the commands in the file.
 
Save the file as a text file and change the properties to run as an executable 

Now, if you have confirmed it works and you want it to initialize on start up (you won't have to put your password in), put the file in the /etc/init.d folder.  It might tell you have an lsb header error, but it will still run.  

[B]One last step I did was to blacklist the b43,ssb, and b43legacy.

The easy way: sudo gedit /etc/modprob.d/blacklist
Look for a line which says: blacklist bcm43xx
Just repeat the blacklist for b43, ssb, and b43legacy (one line each)[/B]

Let me know if it works for you.  There are probably better ways to do this, but I am a newbie.
I don't think I'm following, blacklisting a device you're trying to get to work.... isn't going to help. I think I missed something. Unless you're trying to make it blacklist a driver. If so, I didn't know that was possible using the blacklist file.
[QUOTE=pjizz]
"No proprietary drivers are in use on this system" at the top, but "this driver [b43] is activated and currently in use" at the bottom, so I'm not for sure if it's actually being used or not.
[/QUOTE]
I have this exact same issue. I don't think its you.

---

### Post by pjizz on 2008-11-30
further update:

i went to the "hardware drivers" in system>administration and disabled the b43 wireless driver (which looks just like a simplified gui for running b43fwcutter), saw that things were still working albeit with the familiar droppage.  then i followed cokierken's steps and that gave me abs no wireless whatsoever, not even signal detection.  so then i reenabled the b43 driver from system>admin and now things seem to be more or less fine.  i think it feels just a tad slower sometimes, though that may just be my imagination.  the main thing though is that it hasn't dropped signal any.  i still wish i had a better understanding of what was going on though.

---

### Post by coskierken on 2008-12-01
You are not blacklisting the device, but the b43 driver.  You don't want to use it.  It, along with the b43legacy (Intrepid tries to use it)and ssb were causing a conflict.  So, that is why I remove(via the script) the things causing the conflict.  Then I loaded the ndisgtk to wrap the Windows driver in.  This is the only way I could get it to work properly.

Did you load ndisgtk and then run it from a command prompt?  If not, this is why you did not have wireless as the bcmwl5.inf and sys file were not loaded via ndiswrapper.  

I did not even have to load b43fwcutter.   

Since I removed the b43 with the script and used ndiswrapper(via ndisgtk), I have had no problems what so ever, connects, an did not drop out at all with pretty good connection rates.

---

### Post by pjizz on 2008-12-02
i used ndiswrapper but it didn't give me a fix.  however, reenabling fwcutter has seemed to work fine.  i don't really understand why, b/c that's how i had it setup beforehand.  but it does work fine.

---

### Post by pjizz on 2008-12-05
grrrr....

this is still giving me fits.  it clearly isn't a problem with coverage, as any time it happens, i just disconnect and reconnect and every thing works fine....for 5 minutes.  I'd like to give your method another try, coskierken, but the first time I did it my computer locked up when i ran sudo modprobe ndiswrapper....

i turned it back on and nothing was working.  i tried it again the other day and everything was working, with no droppage.  i checked the restricted hardware drivers gui in Intrepid and confirmed that the b43-fwcutter was not enabled.  so i finished playing for the night and shut down.  however, when I turned it on the next morning there was no wireless...not even detecting the interface or any networks.  so i reenabled the b43-fwcutter and it worked.

but now i'm back at square one with a spotty internet connection.  it's little things like this that keep windows alive...

---

### Post by pjizz on 2008-12-05
okay I just tried it again and same thing.  disabled b43-fwcutter, internet still works, followed coskierken until compy froze at sudo modprobe ndiswrapper.  restarted, no internet, enabled b43-fwcutter, internet exists and choppy.

any ideas?

---

### Post by Ayuthia on 2008-12-05
Does dmesg or /var/log/syslog say anything when the b43 driver disconnects?

---

### Post by Bucky Ball on 2008-12-05
Wild stab, but have you run:

```
iwconfig
```

... and made sure it is connecting to the correct network? My machine started getting a flaky connection and took me awhile to figure out it was connecting to an unsecured network in the area with a pithy signal. Just a shot ...

---

### Post by pjizz on 2008-12-05
> **Ayuthia said:**
> Does dmesg or /var/log/syslog say anything when the b43 driver disconnects?

i actually hadn't checked this [unfamiliar with the command] but did see a long string of obvious network problems

```
[ 1440.001446] b43-phy0 ERROR: PHY transmission error
[ 1440.228397] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1440.340039] Registered led device: b43-phy0::tx
[ 1440.340039] Registered led device: b43-phy0::rx
[ 1440.340195] Registered led device: b43-phy0::radio
[ 1501.000877] __ratelimit: 3111 callbacks suppressed
[ 1501.000923] b43-phy0 ERROR: PHY transmission error
[ 1501.000995] b43-phy0 ERROR: PHY transmission error
[ 1501.001057] b43-phy0 ERROR: PHY transmission error
[ 1501.001128] b43-phy0 ERROR: PHY transmission error
[ 1501.001191] b43-phy0 ERROR: PHY transmission error
[ 1501.001252] b43-phy0 ERROR: PHY transmission error
[ 1501.001323] b43-phy0 ERROR: PHY transmission error
[ 1501.001385] b43-phy0 ERROR: PHY transmission error
[ 1501.001447] b43-phy0 ERROR: PHY transmission error
[ 1501.001508] b43-phy0 ERROR: PHY transmission error
[ 1501.192282] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1501.305187] Registered led device: b43-phy0::tx
[ 1501.306683] Registered led device: b43-phy0::rx
[ 1501.307808] Registered led device: b43-phy0::radio

```

also...yes, it is attempting to connect to the correct network...but good suggestion

---

### Post by Ayuthia on 2008-12-05
From what I have read in the mailing lists, some 4306 cards have transmission problems.  I have not seen a fix for it yet.  I thought that 2.6.27 was supposed to have some fixes for it.  You might try this link:
[http://ubuntuforums.org/showthread.php?t=885173](http://ubuntuforums.org/showthread.php?t=885173)

You might ask lwfinger if his fix deals with PHY transmission errors.  He might be able to provide better guidance.

The other option is to try ndiswrapper.  You mentioned that you tried it before.  What happened?

---

### Post by pjizz on 2008-12-05
when I use ndiswrapper alone, i have no internets....i "think"

you see, whenever i enable ndiswrapper and then disable b43-fwcutter, i still have internet...but once i restart, i am without network connection.  that leads me to believe that fwcutter is not actually being disabled until i restart.  once i do, ndiswrapper is enabled and it reports the driver is installed (though in the gui, pressing the "configure network" button results in an error "network configuration tool not found"...not sure if that is related at all), so i'm not thinking ndiswrapper is a fix here, unless there is something wrong with the way i set it up

---

### Post by Ayuthia on 2008-12-05
> **pjizz said:**
> when I use ndiswrapper alone, i have no internets....i "think"

you see, whenever i enable ndiswrapper and then disable b43-fwcutter, i still have internet...but once i restart, i am without network connection.  that leads me to believe that fwcutter is not actually being disabled until i restart.  once i do, ndiswrapper is enabled and it reports the driver is installed (though in the gui, pressing the "configure network" button results in an error "network configuration tool not found"...not sure if that is related at all), so i'm not thinking ndiswrapper is a fix here, unless there is something wrong with the way i set it up

This actually sounds like the b43 driver is not blacklisted and ndiswrapper is not being loaded on reboot.  If you want to try it, please post the results of:
```
cat /etc/modprobe.d/blacklist|grep -e b43 -e ssb -e ndiswrapper
cat /etc/modules|grep -e b43 -e ssb -e ndiswrapper

```
This will help us see what is currently being blacklisted and what is going to be loaded after the kernel modules have been loaded.

To connect with ndiswrapper with the current session:
```
sudo modprobe -r b43 ssb ndiswrapper
sudo modprobe ndiswrapper
```
I am assuming that you already have ndiswrapper and have the driver installed.

---

### Post by pjizz on 2008-12-07
```
bander@bander-laptop:~$ cat /etc/modprobe.d/blacklist|grep -e b43 -e ssb -e ndiswrapper
# replaced by b43 and ssb.
bander@bander-laptop:~$ cat /etc/modules|grep -e b43 -e ssb -e ndiswrapper
ndiswrapper

```

I do have the ndiswrapper and the driver installed, yes...

I am confused, approaching fearful, of this whole issue.  You see, actually, I once again am having a string of good internetz.  It hasn't dropped a signal in a few days, so I really have no idea if finding a "fix" would help me or hurt me.  Of course, I am still super curious and have a strong desire to get some definitive answers outta this thing.  

Also, I think it'd be helpful if I had a clear explanation of the basic differences between the ndiswrapper method and the b43-fwcutter method.  I understand that one is using a window's driver and another is extracting it from the firmware, but if they both "work" then what is the real difference?  Why would one method have more success on one system and vice versa?  Could anyone speak to that?


Thanks for all the continued help.

---

### Post by Ayuthia on 2008-12-07
> **pjizz said:**
> ```
bander@bander-laptop:~$ cat /etc/modprobe.d/blacklist|grep -e b43 -e ssb -e ndiswrapper
# replaced by b43 and ssb.
bander@bander-laptop:~$ cat /etc/modules|grep -e b43 -e ssb -e ndiswrapper
ndiswrapper

```

I do have the ndiswrapper and the driver installed, yes...

I am confused, approaching fearful, of this whole issue.  You see, actually, I once again am having a string of good internetz.  It hasn't dropped a signal in a few days, so I really have no idea if finding a "fix" would help me or hurt me.  Of course, I am still super curious and have a strong desire to get some definitive answers outta this thing.  

Also, I think it'd be helpful if I had a clear explanation of the basic differences between the ndiswrapper method and the b43-fwcutter method.  I understand that one is using a window's driver and another is extracting it from the firmware, but if they both "work" then what is the real difference?  Why would one method have more success on one system and vice versa?  Could anyone speak to that?


Thanks for all the continued help.

If it is working for you now, just stick with it.  If things are configured correctly and understand a little more about how it works, you can always switch back and forth between the b43 and ndiswrapper.

The b43 driver is the native Linux open source driver.  It does require a proprietary firmware to help make it work.  The b43-fwcutter application will "cut" portions of the firmware that it needs to make the open source driver work.  Since the firmware is proprietary, it cannot be included in Ubuntu.  Some people like b43 because of the open source aspect and some like it because it does provide the ability to use kismet and aircrack-ng.  The other positive of the b43 driver is that since it is open source, any issues that occur in the driver get resolved more quickly where if something should go wrong with the Windows driver, you are pretty much out of luck since the Windows driver is not supported in Linux (and is closed source).

NDISwrapper is an application that allows people to use Windows NDIS drivers in Linux.  So there are some instances where you can use NDISwrapper for other things besides wireless cards.  It is nice because if you have an XP (or older) driver for your wireless card, there is a good chance that your wireless card with work in Linux.  In some instances, it can get better signal and speed than the b43 driver.  NDISwrapper does also support other wireless cards than b43 so it comes in handy for a lot of people that cannot get their wireless cards to work in Linux.  The down side to using NDISwrapper is that development has slowed down and contact to the NDISwrapper team has not been replied so nobody really knows if the project is still active.  I think that a portion of the silence from the NDISwrapper team comes from the conflict on the GPLness discussion with the kernel development team.  The other problem is that it is not able to use Vista drivers yet so if this does not get resolved in the near future, there may be no drivers available for the newer wireless cards.  

Why would one driver work better than another?  Since NDISwrapper is wrapping the Windows wireless driver, it tends to have a better success rate?  For b43, it is still under active development and more improvements are being made to support more cards.  As mentioned earlier, when bugs are found in particular cards, patches can be made to the kernel module and added to the next kernel release where NDISwrapper does not have that luxury (they rely on the Windows driver).

If you could care less about open source or using a proprietary driver (you just want your card to work), it does not really make any difference.  If you have an opinion, stick with the one you like.  If you are afraid that making a change to a mostly working card, I would just stick with it, learn more about Linux so you get more comfortable, then when you are ready (or fed up with it working intermittently) you can make the switch.

As for me, I tend to use the b43 driver because it has worked well for me.  The b43 driver, ndiswrapper, and Broadcom STA wl driver (which does not work for the 4306 card) works well for me.  I will switch the drivers around mainly for testing (I have all three installed) so it is possible to have all the drivers installed and swtich the drivers around when you want.

---

