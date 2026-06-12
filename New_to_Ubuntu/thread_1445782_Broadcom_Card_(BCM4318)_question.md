---
title: "Broadcom Card (BCM4318) question"
date: 2010-04-03
forum: New to Ubuntu
---

### Post by iGuitar on 2010-04-03
I am new to ubuntu 9.10 and can't get my wireless card to work with it. I am running a dual boot btween windows vista and ubuntu if that matters. The wireless doesn't work at all. Any help would be appreciated.

---

### Post by Anthon on 2010-04-03
Have you tried to install proprietary drivers?
Menu System -> Administration -> Hardware Drivers.
IIRC I had to do that for my laptop, but I am not sure which version of the Broadcom chipset it has.
Let me know if that doesn't work for you and I will check.

---

### Post by iGuitar on 2010-04-03
I tried that but it says it doesn't detect anything.

---

### Post by redbook4574 on 2010-04-03
> **iGuitar said:**
> I am new to ubuntu 9.10 and can't get my wireless card to work with it. I am running a dual boot btween windows vista and ubuntu if that matters. The wireless doesn't work at all. Any help would be appreciated.

You will need to install bcmwl-kernel-source and use the sta driver.

---

### Post by iGuitar on 2010-04-03
> **redbook4574 said:**
> You will need to install bcmwl-kernel-source and use the sta driver.

And how would i do that?

---

### Post by Anthon on 2010-04-03
I fired up my laptop and found it uses the Broadcom B43 Legacy driver. It is a Broadcom 4306 chip but that should have the same driver as yours. 
I used to have to muck about with ndiswrapper by hand, but not since 8.10 or 9.04 I think.
Have you checked that the hardware is switched on? Some Laptops have a BIOS setting that switches off wireless on bootup.

---

### Post by Anthon on 2010-04-03
Just in case: to check if the wireless is on, run 
dmesg and search for Broadcom in the output ( dmesg | fgrep -i broad )

---

### Post by redbook4574 on 2010-04-03
> **iGuitar said:**
> And how would i do that?

sudo apt-get install bcmwl-kernel-source
or use synaptic

---

### Post by iGuitar on 2010-04-03
> **redbook4574 said:**
> sudo apt-get install bcmwl-kernel-source
or use synaptic

Now I would need to be connected to the internet for that to work correct?

---

### Post by Naggobot on 2010-04-03
If you are running newly installed 9.10 I would recommend updating the system before attempting the driver search. 

System->Administration->Update manager

-> Search and install updates

then after update

System -> Administration -> Hardware Drivers
I have BCM4318 chipset on my laptop and it uses B43 driver.

I have understoond that the driver is not included in the live cd or that there is a bug on the live cd. 

For me the driver installation in 9.10 was done by application called b43-fwcutter during system installation. I had hardwired connection to internet while installing.

See 

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

for broadcom installation instructions

---

### Post by redbook4574 on 2010-04-03
> **iGuitar said:**
> Now I would need to be connected to the internet for that to work correct?

True if you can connect via ethernet. 

Or alternatively it should be on your cd in pool-restricted-b-bcmwl.

---

### Post by iGuitar on 2010-04-03
> **redbook4574 said:**
> True if you can connect via ethernet. 

Or alternatively it should be on your cd in pool-restricted-b-bcmwl.

Well i can't connect via ethernet right now because i don't have a long enough cable. My router is upstairs and the computer is downstairs. So what is this other way with the cd?

---

### Post by Naggobot on 2010-04-03
Or not 

[https://bugs.launchpad.net/ubuntu/+bug/528838](https://bugs.launchpad.net/ubuntu/+bug/528838)

> On most laptops or netbooks using Broadcom Wireless Broadband, there are no drivers. This bug appears in Ubuntu 9.10 as well as Lucid Lynx Alpha 3, 2, and 1.
 Bug is easily remedied by installing the BCMWL-Kernel-Source. However, if possible, it would be convenient to add the drivers on the download ISO.

 

---

### Post by iGuitar on 2010-04-03
> **Anthon said:**
> Just in case: to check if the wireless is on, run 
dmesg and search for Broadcom in the output ( dmesg | fgrep -i broad )

This is my output 

```
[5.068849] b43-phy0:Broadcom 4318 WLAN found (core revision9)
[5.782762] Broadcom 43xx driver loaded [Features: PL, Firmware - ID:FW13]
```

---

### Post by redbook4574 on 2010-04-03
> **iGuitar said:**
> Well i can't connect via ethernet right now because i don't have a long enough cable. My router is upstairs and the computer is downstairs. So what is this other way with the cd?

Just naviagate to pool-restricted-b-bcmwl on your cd and double click on bcmwl-kernel-source, this will open your package manager and allow you to install.

---

### Post by iGuitar on 2010-04-03
> **redbook4574 said:**
> Just naviagate to pool-restricted-b-bcmwl on your cd and double click on bcmwl-kernel-source, this will open your package manager and allow you to install.'

So do I boot from the Live Cd I used to install then add it or what? I'm kinda confused. Sorry I very new at this whole linux thing.

---

### Post by redbook4574 on 2010-04-03
> **iGuitar said:**
> '

So do I boot from the Live Cd I used to install then add it or what? I'm kinda confused. Sorry I very new at this whole linux thing.

Boot as normal, Put you cd into the drive and install as directed before, also if you need b43-fwcutter (and I'm not sure whether you will or not) it is located in pool-main-b-b43-fwcutter

---

### Post by iGuitar on 2010-04-03
> **redbook4574 said:**
> Boot as normal, Put you cd into the drive and install as directed before, also if you need b43-fwcutter (and I'm not sure whether you will or not) it is located in pool-main-b-b43-fwcutter

So if i boot into ubuntu, put the cd in,then open up the cd, find the package and/or packages,then install, I should be good to go?

---

### Post by redbook4574 on 2010-04-03
> **iGuitar said:**
> So if i boot into ubuntu, put the cd in,then open up the cd, find the package and/or packages,then install, I should be good to go?

Hopefully yes although you may need to find some dependencies I can't quite remember now, but there will be plenty of people around to help, by the way how are you connected at the moment and what os are you using ??

---

### Post by iGuitar on 2010-04-03
> **redbook4574 said:**
> Hopefully yes although you may need to find some dependencies I can't quite remember now, but there will be plenty of people around to help, by the way how are you connected at the moment and what os are you using ??

Well right now since Ubuntu 9.10 can't connect to the internet currently so I have to use Windows Vista for the forums. I have been switching back and forth between the os's everytime someone suggests to do something. It's a big pain. 

What are dependencies?

---

### Post by iGuitar on 2010-04-03
@redbook4574

I installed what you said, bcmwl and b43-fwcutter (bcmwl required dependency dkms, which i also installed) and nothing really seemed to happen. Is this because I have to setup and enter all my wireless network info into ubuntu or can I just search for my network without having to input all the details?

---

### Post by redbook4574 on 2010-04-03
> **iGuitar said:**
> @redbook4574

I installed what you said, bcmwl and b43-fwcutter (bcmwl required dependency dkms, which i also installed) and nothing really seemed to happen. Is this because I have to setup and enter all my wireless network info into ubuntu or can I just search for my network without having to input all the details?

You will need to reboot before anything will happen.

---

### Post by iGuitar on 2010-04-03
> **redbook4574 said:**
> You will need to reboot before anything will happen.

I rebooted. Things changed but they didn't seem to change like I wanted them to. When I click on the signal icon in the systems notification area the connect to a hidden network option is gone and so is the wireless network option

---

### Post by redbook4574 on 2010-04-03
Ok 

go to

system,

Hardware drivers

sta driver

activate.

Then reboot.

---

### Post by iGuitar on 2010-04-03
No drivers came up. It didn't give me a driver to activate.

---

### Post by redbook4574 on 2010-04-03
Ok do you want to try another tack, using a windows driver and ndiswrapper ??

---

### Post by iGuitar on 2010-04-03
> **redbook4574 said:**
> Ok do you want to try another tack, using a windows driver and ndiswrapper ??

Okay let's give it a try. 

By the way, thanks for walking me through all this stuff. I really appreciate it. It's nice to know ubuntu has such a strong, helpful community.

---

### Post by Naggobot on 2010-04-03
As I previously told I have BCM4318 wireless and I had the exact same behavior with the newly installed 9.10 as you are experiencing. For me also the system did not list any hardware drivers from the system->adminstration->hardware drivers. So in my opinion you are doing nothing wrong. 

I do not know how to make it work with out Internet connection but I am quite confident that re-installation with hardwire does work. It worked for me and it worked in this case

[http://ubuntuforums.org/showthread.php?t=1441921](http://ubuntuforums.org/showthread.php?t=1441921)

I can not give 100% guarantee, but here are two verified cases of unsuccessful Broadcom installation with out Internet connection. If you have a router in your house it should be possible to move your computer next to it and attempt to update the system. **If** there is a bug that prevents you from getting the wireless to work without Internet connection you can easily end up spending a lot of time with out results.  

No matter which path you choose, I need to emphasize that BCM4318 works with 9.10 so do not give up. It is unfortunate that this problem effects you and it is unfortunate that this seems quite common.

---

### Post by redbook4574 on 2010-04-03
OK here goes,

First from you cd 

pool-main-n-ndiswrapper and install both deb's in there

second

pool-main-n-ndigtk (this is a graphical front end to ndiswrapper).

I have included a zip file with the necessary driver - create a directory on your desktop or home and extract the files to it.


run ndisgtk and navigate to bcmwl5.inf (do not use bcmwl6.inf - this is for vista and is not supported by ndiswrapper.

It may still require a reboot

Lets hope this works.

---

### Post by iGuitar on 2010-04-03
> **Naggobot said:**
> As I previously told I have BCM4318 wireless and I had the exact same behavior with the newly installed 9.10 as you are experiencing. For me also the system did not list any hardware drivers from the system->adminstration->hardware drivers. So in my opinion you are doing nothing wrong. 

I do not know how to make it work with out Internet connection but I am quite confident that re-installation with hardwire does work. It worked for me and it worked in this case

[http://ubuntuforums.org/showthread.php?t=1441921](http://ubuntuforums.org/showthread.php?t=1441921)

I can not give 100% guarantee, but here are two verified cases of unsuccessful Broadcom installation with out Internet connection. If you have a router in your house it should be possible to move your computer next to it and attempt to update the system. **If** there is a bug that prevents you from getting the wireless to work without Internet connection you can easily end up spending a lot of time with out results.  

No matter which path you choose, I need to emphasize that BCM4318 works with 9.10 so do not give up. It is unfortunate that this problem effects you and it is unfortunate that this seems quite common.

What do you mean by re-installation with hardwire? 

And I could move the computer upstairs to the router but that would be a huge pain. If worst comes to worst I will move it upstairs.

And how did you get your BCM4318 to work on 9.10?

---

### Post by iGuitar on 2010-04-03
> **redbook4574 said:**
> OK here goes,

First from you cd 

pool-main-n-ndiswrapper and install both deb's in there

second

pool-main-n-ndigtk (this is a graphical front end to ndiswrapper).

I have included a zip file with the necessary driver - create a directory on your desktop or home and extract the files to it.


run ndisgtk and navigate to bcmwl5.inf (do not use bcmwl6.inf - this is for vista and is not supported by ndiswrapper.

It may still require a reboot

Lets hope this works.

This may seem like a stupid question but how do you run ndisgtk?

---

### Post by Naggobot on 2010-04-03
> What do you mean by re-installation with hardwire? I mean that you connect to your computer to the router with cable before booting to live cd prior to installation. My apologies for bad phrasing. My story is as follows

I bought an old ACER5021WMLi laptop from friend since he told me that he had tested Ubuntu on it and everything except bluetooth worked ok. 

I installed Ubuntu 9.10 Karmic to the laptop using live cd. When the the system rebooted after the installation I started setting up the wireless as previously with my other computer. I selected

System->Administration->Hardware drivers 

And the system reported no drivers present. I rebooted a few times and tried a again but previous command did not work. Now My friend who had previously installed Ubuntu on the same computer had told me that this was how he got the wireless working. So obviously something had to be different with the installation. 

I figured that since my friend has a router next to he's computers he might have had Internet connection during setup so I decided to try to do the installation again with internet connection so that the cable is connected to the router. 

I connected the cable, started the computer using live CD. Now at this point after the system had booted from live CD I used 

System -> Administration -> Hardware Drivers to search for wireless card to see if it ca be found and it could be. So from live CD at this point my system did recognize that there is a wireless adapter with B43 driver. 

Curious point is that at this point I could not connect to wireless network using the wireless card. I leater learned that there may be a bug on live cd. I did not let the missing wireless connection bother me at that time, instead I selected for the LiveCD to install the Ubuntu to hard drive. (I can not remember where the command is)

Now I followed the installation procedure to some extent and at some point during the installation the installer finds the B4318 card and runs B43-fwcutter *and downloads the correct driver from the internet. *So the installer did not use the driver from the live cd. 

After installation when the system had rebooted from the hard drive I selected 

system -> administration -> update manager

and updated the whole system

After update I and reboot I unplugged the network cable and selected once more

system -> administration -> hardware drivers 

and now the system did find the correct B43 driver and after that I was able to set up the wireless connection 

So I emphasize that I am not familiar with the inner workings of linux/ubuntu but this is my story with BCM4318.

Edit: 
And I need to point out that if you get it working with ndiswrapper then you are ok. If not then you can always opt to other options.

---

### Post by redbook4574 on 2010-04-03
sorry I should have been more specific

system - windows wireless drivers

---

### Post by redbook4574 on 2010-04-03
sorry again 

system - administration - windows wireless drivers

---

### Post by iGuitar on 2010-04-03
> **Naggobot said:**
> I mean that you connect to your computer to the router with cable before booting to live cd prior to installation. My apologies for bad phrasing. My story is as follows

I bought an old ACER5021WMLi laptop from friend since he told me that he had tested Ubuntu on it and everything except bluetooth worked ok. 

I installed Ubuntu 9.10 Karmic to the laptop using live cd. When the the system rebooted after the installation I started setting up the wireless as previously with my other computer. I selected

System->Administration->Hardware drivers 

And the system reported no drivers present. I rebooted a few times and tried a again but previous command did not work. Now My friend who had previously installed Ubuntu on the same computer had told me that this was how he got the wireless working. So obviously something had to be different with the installation. 

I figured that since my friend has a router next to he's computers he might have had Internet connection during setup so I decided to try to do the installation again with internet connection so that the cable is connected to the router. 

I connected the cable, started the computer using live CD. Now at this point after the system had booted from live CD I used 

System -> Administration -> Hardware Drivers to search for wireless card to see if it ca be found and it could be. So from live CD at this point my system did recognize that there is a wireless adapter with B43 driver. 

Curious point is that at this point I could not connect to wireless network using the wireless card. I leater learned that there may be a bug on live cd. I did not let the missing wireless connection bother me at that time, instead I selected for the LiveCD to install the Ubuntu to hard drive. (I can not remember where the command is)

Now I followed the installation procedure to some extent and at some point during the installation the installer finds the B4318 card and runs B43-fwcutter *and downloads the correct driver from the internet. *So the installer did not use the driver from the live cd. 

After installation when the system had rebooted from the hard drive I selected 

system -> administration -> update manager

and updated the whole system

After update I and reboot I unplugged the network cable and selected once more

system -> administration -> hardware drivers 

and now the system did find the correct B43 driver and after that I was able to set up the wireless connection 

So I emphasize that I am not familiar with the inner workings of linux/ubuntu but this is my story with BCM4318.

Edit: 
And I need to point out that if you get it working with ndiswrapper then you are ok. If not then you can always opt to other options.

Hmm okay. But I already installed ubuntu without an internet connection. So could I still do it your way?

---

### Post by iGuitar on 2010-04-03
> **redbook4574 said:**
> sorry again 

system - administration - windows wireless drivers

Well it works. I can now use the internet on ubuntu! Thank you Thank you Thank you. Now on to the next problem. lol.

---

### Post by redbook4574 on 2010-04-03
> **iGuitar said:**
> Well it works. I can now use the internet on ubuntu! Thank you Thank you Thank you. Now on to the next problem. lol.

Glad to have been of help.

---

### Post by jcfuwbs on 2010-04-16
just wanted to say after 8 hours or trying and searching this thread fixed my issue i am using a Hp Pavillion Dv8000 with a BCD4318 card and my net is working beautifully! Thanks a ton

---

### Post by Canada Lee on 2010-04-24
I am running Ubuntu Karmic 9.10 (fresh install) on an Acer Aspire 3000 laptop with a Broadcom BCM4318 Airforce One 54g Rev 02 wireless...

I have wireless connectivity with the B43 driver showing up in the Hardware Drivers application. I have used fwcutter, and can't be certain it completed and downloaded the necessary firmware, as there is a known bug relating to it, where it has a YES / NO question about downloading the firmware, and once selecting YES it exits...without any explanations as to success or failure...search for that fwcutter bug, and you'll know what I mean.

Anyways, what I am experiencing like so many others with broadcom's are experiencing is connectivity with random disconnects. I have been trying to troubleshoot this for months, and I think we need to be digging deeper...not looking on the surface... Here's what I've found out...

Need to have a controlled environment, so...
Laptop is running on AC with battery disconnected to rule out any power saving modes or functions attempting to interfere with operation. Also, screen saver has been deactivated, and in power saving settings it is set while on AC to leave monitor on and never turn it off, and never spin down hard drives.

I have a big torrent downloading, and my wifi led light is flashing, and I have System Monitor running to show a graph of SENT & RECEIVED...when I see the LED light stop flashing (sometimes it may be off, or it may be on - but its state will remain constant, as in if its off, it stays off and doesnt fluctuate, if on, it stays on and doesnt fluctuate...and when I say the led may be off and stays in that state, I mean the wifi is on, but the led is blinking on and off to represent data xfer and the light just happened to be in the off state when it got HUNG UP.

When the led light gets stuck in whatever state, I know its about to loose connectivity, so I go to my terminal, and I >> ping -c 1 -I wlan0 [www.google.com]("http://www.google.com/") << and sure enough, the ping fails...so I do a >> sudo ifconfig wlan0 down << and if the led was stuck in the ON state, I will see the led go out, and the network manager starts scanning (it wont connect though till)...I then do a >> sudo ifconfig wlan0 up << and then the led light comes up...and the networking manager is still scanning and connects.

So...you dont have to do a reboot to get back your network connectivity...
So I made a little wireless script to KEEP-ALIVE the connection, and if lost, do the DOWN and UP command...sounds like it'd work you think...but makes me think something else may be causing the wireless to BE IGNORED...

Here's my keep-alive script...
#!/bin/bash
while [ 1 = 1 ]
do
if [[ ! `ping -c 1 -I wlan0 www.google.co.uk` ]]; then
echo "$(date)"
ifconfig wlan0 down
sleep 5s
ifconfig wlan0 up
sleep ${1}s
fi
done

I place it in my /usr/local/bin folder, make it executable...open a term, and run it with
sudo keep-alive 60
the 60 can be whatever you want it to be, it tells it to wait 60 seconds then ping, then wait 60 seconds then ping...it will run till you stop it with a CTRL-C...if a ping fails it will DROP the wlan0 interface, wait 5 seconds and then bring it back UP. It will also echo in the terminal the ping failure and the time and date.

Thing I noticed, the terminal window is open, my keep-alive is running (I even had it echoing the successful pings every 60 secs) and I can see my cursor blinking in the terminal window...but when I notice the wifi led light not blinking, I know it is going to loose connectivity...and the cursor in the terminal has stopped blinking, and the clock on the top panel has stopped updating...everything on the screen is frozen to a snapshot of when the wifi was working...if I hit the mouse touchpad, the cursor in the terminal starts blinking, the clock in the top panel updates, my torrent display updates. Its like the display went to sleep...and me touching the pad woke it...and it wasnt ASLEEP long enough for loss of connectivity, I know this cuz I waited longer before hitting the touchpad, and when that woke it, then I see a bubble saying disconnected from my network...and then the network manager scanning...and it wont connect, then my keep-alive script drops the wlan and brings it up, and then the netman scanning connects...

You have to remember, I have told it not to spin down hard drives, never to turn off or blank the display, nor screensaver.

But I know my keep-alive script was frozen, everything was frozen...no heavy CPU usage, just like asleep. and me touching the pad woke it from that sleep, and it continued where it was before the sleep...

What makes it sleep like that? What components of Ubuntu perform that job? It cant be the wifi driver just stopped communicating to the kernal, cuz me waking it by swiping my finger on the mouse touchpad should not be able to influence a modem communication driver...

On the other hand, a power savings mode, inactivity, screensavers and so on can be influenced by user input to interrupt their behavior.

So even when power savings is off, something is suspending things...and it is not at constant intervals, it is at random intervals. There is no overheating going on here, and the cpu in not throttling. I am using only max of 10% when torrent is dloading. And if there was overheating or throttling, who ever heard of influencing their state by swiping the touchpad!

Anybody know where to look for something that is making the kernal or some other area going to sleep?


Also, I have followed instructions from the following site to set up my firmware, as that site seemed to relate different scenarios for the b43legacy the b43 and the b43xx drivers (discriminating certain drivers ONLY for certain chipsets), while other sites seem to only use the b43 for all scenarios (no discrimination)...or the b43xxx for all scenerios (again no discrimination)

[http://wireless.kernel.org/en/users/Drivers/b43#fw-b43-lp](http://wireless.kernel.org/en/users/Drivers/b43#fw-b43-lp)

I had the same connectivity with random disconnects before using the b43 provided by the Hardware Devices application, and after following that website.

No change in random disconnects...but it never disconnects when I'm at the laptop using it...because my every move keeps the computer in a state of being awake.

Its only once I have left it alone, that it seems to go to sleep and when it does, everything even the screen display, and the wifi led light, just freezes or pauses...and will stay that way...and my keep-alive program wont save it, cuz it has stopped doing pings, cuz its been paused.

I set it to echo the time and date of each successful ping every 60 seconds, and it would, and it would...but then when the wifi led light's state gets stuck, I know the prob is happening again, and sure enough, no more successful pings, no more failed pings being echoe'd to the screen...clock aint updating...touch the pad...everything on the display updates, then a min later a failed ping (3 mins after the last ping shown on screen - a ping should be happening every 60 seconds)...then a bubble for disconnected network...then the netman scanning, then cuz my prog did a DOWN & UP, connection.

But I shouldnt have to be here to wake it from sleep.  There is no setting in the BIOS for this.

Someone must have an idea where to look?!

---

### Post by homepig on 2010-05-31
> **iGuitar said:**
> Well it works. I can now use the internet on ubuntu! Thank you Thank you Thank you. Now on to the next problem. lol.

[FONT=Arial]I am running [/FONT]10.04 (Lucid Lynx) and my card is  BCM4318 [Airforce One 54g]

I have followed the instructions posted by iGuitar but I still need to do following before it finally worked. 
1. install deb packages found in ubuntu10.04 cd [**must**]
../pool/main/d/dkms 
dkms_2.1.1.2-2fakesync1_all.deb
../pool/main/p/patch  
patch_2.6-2ubuntu1_i386.deb
../pool/main/f/fakeroot  
fakeroot_1.14.4-1ubuntu1_i386.deb
../pool/restricted/b/bcmwl  
bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb

[FONT=Arial]2. blacklist the b43 kernel driver(s)  
[/FONT][FONT=Arial]To do this edit and add the following two lines to **/etc/modprobe.d/blacklist.conf**:  [/FONT]
[FONT=Arial]blacklist b43
blacklist ssb

[/FONT]After all this I could view the wireless network and choose mine but nothing showed up in System -> Administration  -> Hardware Drivers.[FONT=Arial] This thread helped me a lot. Thank you!
[/FONT]
pls find some other reference here
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

