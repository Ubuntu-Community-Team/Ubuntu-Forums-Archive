---
title: "Wireless drops randomly (more frequently under heavy use)"
date: 2008-01-18
forum: Networking &amp; Wireless
---

### Post by Warpedflash on 2008-01-18
I am using a T21 Thinkpad with a Belkin PCMCIA card and the wireless works ok with outof the box with ubuntu but it drops out if i have have than may 5 tabs open or i try and dwnload anything over 3MB.
i have been looking around the forums and from other threads i though i would try a different network manager and settled with Wicd which works fine and connects fine but i still have the problem of the connection dropping. 
if i use 
```
/etc/init.d/networking restart
```
and then try and connect it T/O when trying toget an IP address.

```
 lspci -nn | grep Network
```
02:00.0 Network controller [0280]: RaLink RT2600 802.11 MIMO [1814:0401]

```
lshw -C network | grep driver | sed 's/ /\n/g' | grep driver=
```
WARNING: you should run this program as super-user.
driver=e100               
driver=rt61pci

All help is appreciated!
Warpedflash

---

### Post by Warpedflash on 2008-01-19
bumping for more help....

---

### Post by Warpedflash on 2008-01-19
Update: It refuses to connect to anything through the wireless after it dissconnects....
i have to reboot, restarting X dosent work...

---

### Post by rustybronco on 2008-01-19
you could try and install ndiwrapper using the proper drivers for your wireless card.
ndiswrapper how-to [http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

kevdogs guide has quite a few how-to's on ralink chipsets and how to connect from the command line.
[http://ubuntuforums.org/showthread.php?t=596797](http://ubuntuforums.org/showthread.php?t=596797)

wieman01's guide for gutsy.  [http://ubuntuforums.org/showpost.php?p=3450169&postcount=1](http://ubuntuforums.org/showpost.php?p=3450169&postcount=1)

i'm running the 2.6.24.2 kernel in my fiesty install with wicd as the network manager and it is working just fine ( can download to my hearts content ).***note*** just updated to the 2.6.24.4 kernel, i'll let you know of any issues. ***update***no issues with downloading.
how to install hardy kernel [http://ubuntuforums.org/showthread.php?t=646755](http://ubuntuforums.org/showthread.php?t=646755)
but only if you don't mind breaking things and the possibility of fixing or reinstalling the os.

This is what I get out of my linksys pcmcia card using the 2.6.24. kernel in fiesty.

dale@fiesty-laptop:~$ lspci -nn | grep Network
02:00.0 Network controller [0280]: RaLink Ralink RT2600 802.11 MIMO [1814:0401]
dale@fiesty-laptop:~$ 

WARNING: you should run this program as super-user.
driver=donauboe (ir driver)        
driver=rt61pci
dale@fiesty-laptop:~$ 

I don't know it didn't help fix your problem, but it's a few things to ponder

---

### Post by rustybronco on 2008-01-19
Let me know what worked best for you please.

---

### Post by oly on 2008-03-31
I get this exact same problem, i hope its fixed for hardy i have had the problem on 4 machines 2 laptops and 2 desktops both using variants of bcm43xx and rt2500 drivers and one using ndiswrapper so its does not seem to be driver specific.

I get same sort of problem in that it happens randomly some days after a few minutes others after several hours heavy load does seem to cause it to happen more often, but i have also had it work for a whole day under very heavy load.

whats most annoying is getting it to reconnect after it drops i have tried allsorts like restarting netwrok services removeing the driver module for the card and reinserting and sometime it will fix it temporarily but most of the time does not.

I dont even now how to go about finding the cause or what to file it as a bug against.

Made a mistake thought this was for hardy not feisty, i am having the probs with hardy so will re-search for hardy with same issue

---

