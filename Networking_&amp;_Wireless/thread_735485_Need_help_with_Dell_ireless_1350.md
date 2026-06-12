---
title: "Need help with Dell ireless 1350"
date: 2008-03-25
forum: Networking &amp; Wireless
---

### Post by lakelovers on 2008-03-25
I hope I'm not posting too many times with this problem but I'm at the end of my rope. I'm running gusty 7.10 and have a Dell 1350 wireless card. I have the firmware loaded and I've also installed bcm43xx-cutter which didn't work, however, the power light and link light lit up on the card but I could not get on line with it. I enabled the wireless ethO and eth1; still no access to internet. (I'm using a direct wire to the router for this post. Then I tried ndiswrapper and got a message that it was not valid. I  will be so indebted to anybody who solve this problem for me.

---

### Post by sillyxone on 2008-03-25
more detail please. Where did you get the (Windows) driver from, at what step did ndiswrapper spit back that message?

---

### Post by lakelovers on 2008-03-25
I downloaded ndiswrapper from the internet .. I installed bcm43xx-fwcutter from synaptic. After enabling Broadcom 43xx chip family, I opened /usr/sbin/ndiswrapper-1.9. That's when a got the message: "The firmware location or the firmware itselt you chose is not valid. Please make sue you selectged a firmware file from the proper location." I also tried /usr/sbin/ndiswarapper. I'm wondering, now, if I should have used the Windows CD to copy the driver but I think I tried that. I'll try again.

---

### Post by sillyxone on 2008-03-25
let's be clear first: if you want to use ndiswrapper, you have to disable/blacklist bcm43xx since they are basically two approaches using the same driver.

here is basically the procedure:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc)

please adapt it to your situation (you already have the driver so don't have to download it). Let me roughly outline the steps:

- blacklist bcm43xx
- install ndiswrapper (easier if use Synaptic)
- use ndiswrapper to install the windows driver (.inf file)
- verify that it's working

after this, you should be able to connect using NetworkManager. However, NM is not always a smooth experience so I do recommend using Wicd instead (again, from Synaptic). When you install Wicd, it will automatically remove/replace NetworkManager.

---

### Post by lakelovers on 2008-03-26
Thanks, I'm moving, and feel confident that your direction will get me a working wireless. I have a few questions: Do you have a preference: bcm43xx or ndiswrapper? Or do I try both to see what works? I'm confused about the Windows driver. Do I used the  driver file (bcmwl5.inf) from Windows CD? Wicd is not on my Synaptic, and tried installing with aptitude and it found no file "Wicd," and the network manager disappeared as you said it would. How do I install the windows driver (.inf file) with ndiswrapper? I'm sorry I'm such a dudderhead but I've tried following your instructions but I don't know enough linux stuff to execute you instruction to the end.

---

### Post by sillyxone on 2008-03-26
bcm43xx didn't work and ndiswrapper is working for me. 

bcm43xx extract the firmware from Windows binary driver (bcmwl5.sys) to talk directly to the wireless card. Ndiswrapper create a wrapper around the Windows binary driver, basically mapping Linux API to Windows API so that Linux can talk to the driver. Thus, I prefer ndiswrapper since it reserve all the functionalities that the manufacture intended. This is also the reason why you can only have either bcm43xx or ndiswrapper at a time.

NetworkManager and Wicd are two network managers. I found Wicd is easier to use. You can follow the instruction on Wicd website to install it:
[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

to install the wireless driver using ndiswrapper, this is how I remember:

- blacklist bcm43xx in /etc/modprobe.d/blacklist
- install ndiswrapper, run "ndiswrapper --help" to have an idea of its options. If you already played with ndiswrapper, clean it up by running "ndiswrapper -m bcmwl5"
- make sure you have the correct Windows driver for your card. Ndiswrapper only need two files: bcmwl5.sys and bcmwl5.inf. Copy them to a folder in your Ubuntu.
- staying in the folder where you put those two file, run  "ndiswrapper -i bcmwl5.inf", ndiswrapper will parse the .inf file and use the .sys file as the driver
- run "ndiswrapper -l" to make sure that the driver has been installed (you should see the word "present" printed out)
- run "sudo modprobe ndiswrapper" to query the wireless card. Your wireless LED should be ON now.
- run "sudo ndiswrapper -m" to make the configuration permanent.
- you can check if your wireless is working by running "iwlist eth1 scan" and should see the list of wireless networks around you.
- follow the instruction on Wicd page to install it. Once installed, there should be a tray icon for your to configure it (if the tray is not there, just run "/opt/wicd/tray.py")

feel free to ask question, I had a hard time before as well

---

### Post by lakelovers on 2008-03-26
Thanks, again. I'm pressed for time at the moment. As soon as I have a little more time (perhaps tonight), I'll follow your directions and let you know how it goes.

---

### Post by lakelovers on 2008-03-26
When I gave the command for ndiswrapper to pars the .inf/.sys files, it said the driver bcmw;5 is already installed, When I went to ndiswrapper -l, I got bcmwl5 & bcml5 were both invalid drivers.Some how in the process I lost the wired connection to the router. I went to the "network" to reset the connection but didn't know how to manipulate it. My problem is that my knowledge is so shallow that I get stuck in corner. I'll keep trying. Sorry I'm giving you so many problems to deal with.

I'm back online using wicd. It works great. now I'll move on following your directions.

I copies other bcmwl5 files from the CD and they return "not vialed drivers" when I do "ndiswrapper -l.

---

### Post by sillyxone on 2008-03-26
I'm not an expert neither so let's give you some tool to play with:

- kill NetworkManager: "sudo killall NetworkManager"
- manually get an IP from router on all devices (wire, wireless): "sudo dhclient"
- check if you have an IP/connection: ifconfig

Can you post the result when you run "ndiswrapper -l"? Is the wireless light is currently on? Can you post the result when you run "ifconfig"?

calm down, enjoy, it's a fun learning process.

---

### Post by lakelovers on 2008-03-26
The wireless card light is not on. During this whole process the wireless power light was on periodically and the connection light was on steady at times. I think that was when I used messing around with bcm43xx. I current have a wired connection with the router. 

ann@ann-laptop:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:22:B8:E6:98  
          inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::214:22ff:feb8:e698/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2271 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2662 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:870688 (850.2 KB)  TX bytes:540953 (528.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by sillyxone on 2008-03-27
LOL, I just tried ndiswrapper with a fake name "bcmwl6", and it allowed me to install and gave the "invalid driver" message. 

So, run "ndiswrapper -r bcmwl5" again to remove the invalid driver, then make sure you are in the directory of the bcmwl5.inf and bcmwl5.sys files before adding the driver again (or use absolute path).

for example: 
```
sudo ndiswrapper -i /home/lakelover/wireless_driver/bcmwl5.inf
```

---

### Post by lakelovers on 2008-03-27
Okay, bcmwl5.inf was accepted this time but I'm still getting an invalid firmware notice when I open ndiswrapper in the restricted driver manager. I may be trying to load the wrong ndiswrapper file. I've been selecting "ndiswrapper (shellscript) and ndiswrapper-1.9 (perl script) both give me the invalid notice. Which ndiswrapper file should I open in the restricted driver manager? Or, am I missing something else in the process?

When I do "ndiswrapper -l" I get. . .

bcml5 : invalid driver!
bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)
bcmwl5.sys : invalid driver!

---

### Post by chuckH on 2008-03-27
Hey did you try this?

[http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&message.id=6807&c=us&l=en&cs=19&s=dhs](http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&message.id=6807&c=us&l=en&cs=19&s=dhs)
1350 & Linux is the main topic.

---

### Post by lakelovers on 2008-03-27
Chuck. . . basically, I think that's what I've done.

---

### Post by sillyxone on 2008-03-27
> 
When I do "ndiswrapper -l" I get. . .

bcml5 : invalid driver!
bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)
bcmwl5.sys : invalid driver!


so far so good, we're getting there. Now you need to remove the two invalid drivers:
```
sudo ndiswrapper -r bcml5
sudo ndiswrapper -r bcmwl5.sys

```
then, activate it
```
sudo modprobe ndiswrapper

```
the wireless light should be on then and you should be able to use wicd to browse the network list. To make the activation permanent:
```
sudo ndiswrapper -m
```

---

### Post by lakelovers on 2008-03-27
Wonder of wonders! You got my wireless working. You have ended my five-day excursion into hell. By the way, it's my wife's laptop so you know why I say it was a trip into hell. Thank you, thank you.

Last note: when I put the command in to make ndiswapper permanent, I got:

"module configuration already contains alias directive"


Rats. . . when I rebooted I lost the wireless connection but use wicd to reinstate it. Now, I need to make it permanent but as I said the permanent command didn't seem to work.

---

### Post by sillyxone on 2008-03-27
> 
Last note: when I put the command in to make ndiswapper permanent, I got:

"module configuration already contains alias directive"


that's OK, all it does is write ndiswrapper configuration into modprobe list and create a file named ndiswrapper in /etc/modprobe.d/ which alias wlan0 to eth1. When I say permanent, I mean you don't have to modprobe it when restart (that's mean you see the wireless light automatically on when restart).


> 
Rats. . . when I rebooted I lost the wireless connection but use wicd to reinstate it. Now, I need to make it permanent but as I said the permanent command didn't seem to work.

If on startup, the wireless light if off and wicd cannot see any wireless network, there is something wrong that modprobe couldn't query the device on boot.

If on startup, the wireless light is on and wicd see the list of networks but don't connect any of them, it's just a matter of configuring wicd (remember to check the box "Automatically connect to this network" in Wicd configuration panel).

> 
By the way, it's my wife's laptop so you know why I say it was a trip into hell.

you're a brave man, I don't dare to set Ubuntu on my wife's laptop ... yet. She watches movie online a lot and Firefox crashes on Flash's movie every now and then. However, I heard FF3 fixed that problem so Ubuntu will be on her laptop soon.

---

### Post by lakelovers on 2008-03-27
My wife was having lot of problem with WindowXP. Then the HD crashed. I put i a new dirve re-installed windows and it wouldn't down load anything and I got fed up trying to get information from the Windows forums. That's why I put Ubuntu on her computer. We'll see how she does with it; I may have to go back to Windows to keep the peace. So far she'd doing okay.

I'm still trying to get ndiswrapper to be permanently installed.

---

### Post by lakelovers on 2008-04-24
My wife's computer cannot find the wireless internet connection when her computer is turned off and restarted. I have to re-enter the command "sudo modprobe ndiswrapper" to re-establish the wireless connection. Also, the command "sudo ndiswrapper -m" doesn't make the ndiswrapper permanent. How can I get ndiswrapper to activate automatically when the computer is restarted?

---

