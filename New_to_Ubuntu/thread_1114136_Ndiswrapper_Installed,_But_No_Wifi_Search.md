---
title: "Ndiswrapper Installed, But No Wifi Search?"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by Zubb on 2009-04-02
Hiya Guys :popcorn:

Im new To this Forum, and Im really excited about using Linux and this forum is the perfect place for me :D

Im having a problem though.

Im using a Broadcom Corporation BCM4311 802.11b/g WLAN 

So i followed this Tutorial.. [http://ubuntuforums.org/showthread.php?t=760568](http://ubuntuforums.org/showthread.php?t=760568)

The Driver is the correct one, and i installed ndiswrapper perfect, Followed it all the way to the end, apart from the "mount to CD" part, thats confused me, but i didnt think it mattered.

and i went through the tests at the end to see if Wifi was working, and it lit up on my inspiron, so i thought it would work when i restarted.

I restarted and i still have no internet (wireless) when i left click on it, it doesnt show any wireless network in range, and when i go in the terminal and type in "ifconfig wlan0 s" it scans but finds nothing, but im sat right next to my router, also when i right click it and click "edit wireless networks" its just a box with blank sections and i cant fill them in :(

I tried to get this working years ago, and gave up and now im trying again, But i dont know what im doing wrong :(

Thanx Guys.
Zubb.

---

### Post by WakkiTabakki on 2009-04-02
If you sit next to the router, whats the purpose with wireless? (sorry, couldn't help it)

Mounting the CD is only if you couldn't get the driver off the internet (thus get it from the CD instead). So if you downloaded the driver, you wouldn't need to mount the CD...

Check that the driver is installed properly and detects the device by starting a terminal and type:
```
ndiswrapper -l
```
It should output something like
```
netwpn11 : driver installed
	device (1385:5F01) present
```
(ofcourse you'd have something other than 'netwpn11' and '1385:5F01').
If the above seems right, do you happen to run Ubuntu 64bit and installed the 32bit wireless perhaps? The manufacturer of my device (a quite new Netgear USB wireless) doesn't provide 64bit drivers, so no luck for me. Thus 'stay clear of Netgear' has been my device since getting that device :|


And finally scan the logs for any messages related to ndiswrapper by typing the following in a terminal
```
grep ndis /var/log/* > ~/ndisMessages.txt
```
And then post the contents of the file ndisMessages.txt (which you should find in your home folder) within QUOTE-tags here. Well, first look through the file so you don't post anything sensitive...


/N

---

### Post by sailor2001 on 2009-04-02
also, I installed "wifi radar" from synaptics.. handy apt

---

### Post by anewguy on 2009-04-02
You may also need to check under System/Administration/Network and be sure wireless shows there and that roaming mode is enabled.  Also, if you left-click on the network manager icon on the upper status bar, try clicking on enable wireless.

Just some thoughts of things to try.

Dave

---

### Post by Zubb on 2009-04-03
Thanx For You help Guys!

I think i screwed up in the process so i re-installed Ubuntu and followed everything through on the tutorial.

And i got it working :D

It works perfect and i can connect wirelessly.

Thanx Again Guys!

Zubb

---

