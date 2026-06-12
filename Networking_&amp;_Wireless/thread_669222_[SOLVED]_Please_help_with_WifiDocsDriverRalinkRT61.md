---
title: "[SOLVED] Please help with WifiDocs/Driver/RalinkRT61"
date: 2008-01-16
forum: Networking &amp; Wireless
---

### Post by TRANQU111TY on 2008-01-16
I'm such a noob and been googling for hours trying to get my wireless stable. 

I decided to use this [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61)

When I get to the **Compilation of the Module** section that has the command line **$ make all**, I get this on my terminal.
```

make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/jason/RT61_Linux_STA_Drv1.1.0.0/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/jason/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.o
/home/jason/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c: In function ‘RT61_probe’:
/home/jason/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:197: error: ‘struct net_device’ has no member named ‘get_wireless_stats’
/home/jason/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c: In function ‘RT61_open’:
/home/jason/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:326: warning: ‘deprecated_irq_flag’ is deprecated (declared at include/linux/interrupt.h:66)
/home/jason/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:326: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
make[2]: *** [/home/jason/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/jason/RT61_Linux_STA_Drv1.1.0.0/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [all] Error 2

```

Is that supposed to happen? (I may have run through the whole tutorial a few times trying to work it so I hope that hasn't buggered it up)

If that **is fine**, I make my way to section called **Installation of the module** and pop in the command line:

```
sudo cp *.bin rt61sta.dat /etc/Wireless/RT61STA/
```

and this simple error comes up:

```
cp: cannot stat `rt61.ko': No such file or directory
```

I'd appreciate it if someone could help me get through this.

I'll try to learn about linux more.

---

### Post by rustybronco on 2008-01-16
> **TRANQU111TY said:**
> _
make[1]: Entering directory `/usr/src/linux-headers-**2.6.22-14-generic**'
make[2]: *** [/home/jason/**RT61_Linux_STA_Drv1.1.0.0**/Module/rtmp_main.o] Error 1
The rt61sta driver is the driver used with 7.04 (fiesty) your kernel is 7.10 (gutsy) I don't know if it's the problem, but I believe it to be.
If it was me trying to get this to work, I would compile it from source because in **MY** limited experience the rt61sta driver will not let you use roaming mode.

Quote from the above link.
> These instructions have been tested on Ubuntu 6.10 (a.k.a. Ubuntu Edgy Eft), they **could** work on other release of Ubuntu.

are you sure you have the correct chipset that uses this driver? not to question, just to make sure.
lspci -nn  will give you the chipset

if you would like to have an answer to you errors please check the forums at serialmonkey  [http://rt2x00.serialmonkey.com/phpBB2/](http://rt2x00.serialmonkey.com/phpBB2/)

If you follow this tutorial    [http://ubuntuforums.org/showpost.php?p=3609183&postcount=1](http://ubuntuforums.org/showpost.php?p=3609183&postcount=1)  substituting the proper hourly tarball,  should make it work.

get the CVS hourly tarball from here [http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads](http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads)

***NOTE*** you may have to blacklist the rt61sta driver.

let me know if I can help.

---

### Post by TRANQU111TY on 2008-01-17
What about using the [Sticky: HOWTO: RT2500, etc. wireless cards]("http://ubuntuforums.org/showthread.php?t=564419") to install the driver for my rt61? Btw it is a D-Link DWL-G510 Rev C. PCI wireless card so I'm guessing I would be using the rt61pci.

Anyways thanks for your reply I will try the tutorial you gave me.

---

### Post by TRANQU111TY on 2008-01-17
I have completed the tutorial down to the section where it has told me to blacklist so I put in rt61sta and restarted. There were more steps but I decided not to take them as my internet is working (not sure how stable it is yet though). Does that mean I do not need to complete the final steps and it is installed properly?

---

### Post by wieman01 on 2008-01-17
What 'final steps' are you referring to?

If the wireless connection works even after a reboot, then you are fine I guess.

---

### Post by TRANQU111TY on 2008-01-17
Just to clarify I'm using this tutorial [http://ubuntuforums.org/showpost.php?p=3609183&postcount=1](http://ubuntuforums.org/showpost.php?p=3609183&postcount=1).

I've completed all the steps down to the blacklisting section which has the command line:

```
sudo gedit /etc/modprobe.d/blacklist
```

My net seems fine so far. Still seems to be running slower than windows (browsing) but wireless has not dropped out yet.

---

### Post by rustybronco on 2008-01-17
> and change all occurrences of "rausb1" to "rausb0" and then yet again, restart
when I did that tutorial I never changed "rausb" or what ever it came up as and it was working fine for me, as it's working you should be allright leaving well enough alone.
if you run into connectivity or speed issues you may want to change from the network manager to wicd or rutilt, just don't do it willy-nilly, see how stable it is first.

> Still seems to be running slower than windows (browsing)  could be related to issues **some** people are having with firefox?
has your download speed changed?

post the output of **lspci -nn**
looks like it a rt61 [http://forums.whirlpool.net.au/forum-replies-archive.cfm/488201.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/488201.html)

---

### Post by raiwo on 2008-01-17
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.24/+bug/144239](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.24/+bug/144239)

---

### Post by TRANQU111TY on 2008-01-17
```
00:00.0 Host bridge [0600]: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub [8086:2770] (rev 81)
00:01.0 PCI bridge [0604]: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port [8086:2771] (rev 81)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc R580 [Radeon X1900 XT] (Primary) [1002:7249]
01:00.1 Display controller [0380]: ATI Technologies Inc R580 [Radeon X1900 XT] (Secondary) [1002:7269]
03:05.0 Network controller [0280]: RaLink RT2561/RT61 rev B 802.11g [1814:0302]
03:06.0 Multimedia audio controller [0401]: Creative Labs SB X-Fi [1102:0005]

```

If my internet is under load (few pages loading at once, pidgin running) it disconnects. I have also noticed my download speeds are really unstable/jumpy. It sometimes download consistently at 160kB/s for 10 seconds or so, then all of a sudden it drops down to less then 1kB/s and then up to 30kB/s etc. I have a 1.5MBIT connection and in Windows it was always stable.

---

### Post by wieman01 on 2008-01-17
If all this does not help, please try out my Ralink tutorial if you have not done so yet. If you need a hand, drop me a line. 'ndiswrapper' does a fairly good job.

---

### Post by rustybronco on 2008-01-17
```
03:05.0 Network controller [0280]: RaLink RT2561/RT61 rev B 802.11g [1814:0302]

```

> If my internet is under load (few pages loading at once, pidgin running) it disconnects. I have also noticed my download speeds are really unstable/jumpy. It sometimes download consistently at 160kB/s for 10 seconds or so, then all of a sudden it drops down to less then 1kB/s and then up to 30kB/s etc. I have a 1.5MBIT connection and in Windows it was always stable.try installing 
wicd [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php) 
or rutilt [http://ubuntuforums.org/showthread.php?t=554089&highlight=rutilt](http://ubuntuforums.org/showthread.php?t=554089&highlight=rutilt)

I had the same issues with a rt2600 (rt61pci driver) and wicd solved the issues for me.
[http://ubuntuforums.org/showpost.php?p=4122646&postcount=9](http://ubuntuforums.org/showpost.php?p=4122646&postcount=9)
if not and it is a bug in source I'm out of answers.

---

### Post by TRANQU111TY on 2008-01-17
> **wieman01 said:**
> If all this does not help, please try out my Ralink tutorial if you have not done so yet. If you need a hand, drop me a line. 'ndiswrapper' does a fairly good job.

Before I use your tutorial, do I need to blacklist the driver I am using now? That basically means the system won't use it right?

---

### Post by wieman01 on 2008-01-17
> **TRANQU111TY said:**
> Before I use your tutorial, do I need to blacklist the driver I am using now? That basically means the system won't use it right?
Yes, that is right. But you can remove the driver from the blacklist anytime you like. So install 'ndiswrapper' first and then follow the steps outlines in the tutorial.

---

### Post by TRANQU111TY on 2008-01-17
> **wieman01 said:**
> Yes, that is right. But you can remove the driver from the blacklist anytime you like. So install 'ndiswrapper' first and then follow the steps outlines in the tutorial.

I'm afraid it did not work for me as I wasn't able to see my wireless modem.

I am giving Wcid a shot. Working well so far.

---

### Post by rustybronco on 2008-01-17
> **TRANQU111TY said:**
> I'm afraid it did not work for me as I wasn't able to see my wireless modem.

I am giving Wcid a shot. Working well so far. If it's working fine :) if not and you have the time to play with it (and don't mind the possible re-install ) you can try the hardy kernel.   [http://ubuntuforums.org/showthread.php?t=646755](http://ubuntuforums.org/showthread.php?t=646755)
if not try weiman01's suggestion for ndiswrapper. 
you learn, we learn from it and help others.

---

### Post by TRANQU111TY on 2008-01-17
Wcid was working fine until it disconnected and had a hard time trying to reconnect. Ever since it has disconnected, this internet experience has been the worst for me. Is it possible that changing the WPA Supplicant driver would help? 

So far this tutorial has worked the best for me [http://ubuntuforums.org/showpost.php?p=3609183&postcount=1](http://ubuntuforums.org/showpost.php?p=3609183&postcount=1). I need to get some sleep now but I will continue to try your other options. Goodnight for now :)

---

### Post by rustybronco on 2008-01-17
> **TRANQU111TY said:**
> Wcid was working fine until it disconnected and had a hard time trying to reconnect. Ever since it has disconnected, this internet experience has been the worst for me. Is it possible that changing the WPA Supplicant driver would help? 

So far this tutorial has worked the best for me [http://ubuntuforums.org/showpost.php?p=3609183&postcount=1](http://ubuntuforums.org/showpost.php?p=3609183&postcount=1). I need to get some sleep now but I will continue to try your other options. Goodnight for now :)go with ndiswrapper as wieman01 suggested.

---

### Post by TRANQU111TY on 2008-01-18
> **rustybronco said:**
> go with ndiswrapper as wieman01 suggested.

I'm afraid I had no luck with it. I guess I'll continue to find better ways until I hit a brick wall. Perhaps I already have hit it?

---

### Post by wieman01 on 2008-01-18
> **TRANQU111TY said:**
> I'm afraid I had no luck with it. I guess I'll continue to find better ways until I hit a brick wall. Perhaps I already have hit it?
So what happened? What steps did you perform? And what does this yield:
> sudo ndiswrapper -l
> sudo lshw -C network

---

### Post by TRANQU111TY on 2008-01-18
> **wieman01 said:**
> So what happened? What steps did you perform? And what does this yield:

I managed to complete all the steps without any errors but there was no sign of a wireless connection.

I have reformatted again to try another tutorial.

---

### Post by TRANQU111TY on 2008-01-21
I needed to use the internet so I installed XP again. 

I was using 64Bit Ubuntu and I'm Just wondering what would happen if I installed the 32Bit Ubuntu? Would it make a difference to the wireless connectivity?

---

### Post by wieman01 on 2008-01-21
> **TRANQU111TY said:**
> I was using 64Bit Ubuntu and I'm Just wondering what would happen if I installed the 32Bit Ubuntu? Would it make a difference to the wireless connectivity?
Oh yes, to say the least. I was not aware that you were using 64-bit otherwise I would have pointed that out earlier. 32-bit could well make a difference.

---

### Post by TRANQU111TY on 2008-01-21
Oh great, just finished the last % on the 32Bit, I'll see how I go.

---

### Post by TRANQU111TY on 2008-01-21
I'm definitely seeing an improvement over 64Bit. For example my download speed was fairly consistent with a 30sec file download. This never happened when I was using 64Bit. Browsing also seems to be faster. I guess if this keeps up I won't need to search for alternative to NetworkManager or the driver. :) Thanks for your help.

---

### Post by wieman01 on 2008-01-21
> **TRANQU111TY said:**
> I'm definitely seeing an improvement over 64Bit. For example my download speed was fairly consistent with a 30sec file download. This never happened when I was using 64Bit. Browsing also seems to be faster. I guess if this keeps up I won't need to search for alternative to NetworkManager or the driver. :) Thanks for your help.
I have not done much, mate. Really... :-) Post here if there is any other issue I can help with.

---

### Post by TRANQU111TY on 2008-01-21
I am sure there is nothing wrong with the speed of the internet but it dropped out after consistently downloading at max speed for 10 minutes. It's back to normal now. Will see if it happens again and if so I will probably have to try some alternatives. 

I think it could be a problem with the applet (NetworkManager) not the driver. Would it be correct to say that?

PS. I can't believe how fast my browsing speed is while I'm downloading. Probably beats Windows.

---

### Post by wieman01 on 2008-01-21
> **TRANQU111TY said:**
> I am sure there is nothing wrong with the speed of the internet but it dropped out after consistently downloading at max speed for 10 minutes. It's back to normal now. Will see if it happens again and if so I will probably have to try some alternatives. 

I think it could be a problem with the applet (NetworkManager) not the driver. Would it be correct to say that?

PS. I can't believe how fast my browsing speed is while I'm downloading. Probably beats Windows.
It could be the driver or interference with other wireless networks around you. Changing the broadcast channel might help to avoid interference and disruptions. Also other router settings such as the beacon interval, etc. could be the culprit, but it is hard to tell.

Try changing the channel (to another one outside the range of other networks), if that doesn't do the job then we could replace the driver with 'ndiswrapper' (see signature).

---

### Post by TRANQU111TY on 2008-01-21
> **wieman01 said:**
> It could be the driver or interference with other wireless networks around you. Changing the broadcast channel might help to avoid interference and disruptions. Also other router settings such as the beacon interval, etc. could be the culprit, but it is hard to tell.

Try changing the channel (to another one outside the range of other networks), if that doesn't do the job then we could replace the driver with 'ndiswrapper' (see signature).

I don't think that is the problem. The only proof I have is Windows XP never dropped out. So it must be the driver?

---

### Post by wieman01 on 2008-01-21
> **TRANQU111TY said:**
> I don't think that is the problem. The only proof I have is Windows XP never dropped out. So it must be the driver?
It could be, yes. 

Tell you what... why don't you give my tutorial a go. I'll guide you through it and we'll replace the 'rt61'. Want to try?

---

### Post by TRANQU111TY on 2008-01-21
I actually just followed your tutorial and it worked flawlessly. Will let you know how it goes. Looks really promising so far. Once I enabled roaming, it detected my router straight away and in seconds I was browsing the net, thats a first :)

---

### Post by wieman01 on 2008-01-21
> **TRANQU111TY said:**
> I actually just followed your tutorial and it worked flawlessly. Will let you know how it goes. Looks really promising so far. Once I enabled roaming, it detected my router straight away and in seconds I was browsing the net, thats a first :)
Excellent. It should definitely work. If not, you know where you find me. :-)

---

### Post by TRANQU111TY on 2008-01-21
Yes it is excellent thank you. Well I've learned that it doesn't work in 64Bit but works flawlessly in 32Bit for me :)

---

### Post by TRANQU111TY on 2008-01-22
I'm sorry to say this but the wireless connection kinda drops out every now and then when I'm using it. Try an alternative to Network Manager? Any suggestions?

I'm just playing around with settings on my router, frequency etc, to see if it helps.

---

### Post by wieman01 on 2008-01-22
> **TRANQU111TY said:**
> I'm sorry to say this but the wireless connection kinda drops out every now and then when I'm using it. Try an alternative to Network Manager? Any suggestions?

I'm just playing around with settings on my router, frequency etc, to see if it helps.
What are the settings for the wireless network on the router? Could you post a list of them here?

---

### Post by TRANQU111TY on 2008-01-26
Thanks for all your help wieman01.

I am pretty sure I have solved all the connection drop out and slow down issues.

The thing that worked was changing my **Channel ID** on my router to **Channel 6 (2.437GHz)**.

---

### Post by wieman01 on 2008-01-27
> **TRANQU111TY said:**
> Thanks for all your help wieman01.

I am pretty sure I have solved all the connection drop out and slow down issues.

The thing that worked was changing my **Channel ID** on my router to **Channel 6 (2.437GHz)**.
Interference... pretty common issue nowadays. Thanks for letting us know, mate. See you around.

---

