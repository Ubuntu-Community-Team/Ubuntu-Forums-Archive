---
title: "GUI installation tutorial for wg111v2 and Ubuntu 8.04"
date: 2008-07-05
forum: Networking &amp; Wireless
---

### Post by aimwin on 2008-07-05
[COLOR="Red"]--updated 17 October 2010 ---If you are not using older 8.04 and 8.10 PLEASE DON'T WAST TIME READING THIS THREAD -----------

WG111v2 is working with WPA with no problems with Ubuntu 9.1, 10.04 and 10.10
very reliable and stable.

----------- I have actually use USB - WG111v2 with Dell computers so it can access wireless Internet immediately, and update its "built in Broadcom wireless" and VGA cards. Since the RJ45 - wired LAN Internet is not functioning in these new Dell machines when you first install ubuntu 10.04 or 10.10 more details at 
[http://ubuntuforums.org/showthread.php?t=1579240](http://ubuntuforums.org/showthread.php?t=1579240)
-----------------------------------------------[/COLOR]



Latest EDIT 25/07/2008

***_pytheas22 SAID"My WG111v2 just works when I plug it in. I don't need to do anything else; ndiswrapper is not necessary. It does have some stability issues on 64-bit (on 32-bit it's absolutely fine)....and...I'm able to use automatic mode(NetworkManager) to connect to my Netgear router with WPA/TKIP encryption"_***

Thanks "pytheas22" a lot. with his experiences enable me to wrote this new EDITed Instruction.




Please read his post below as well, since that is his direction for me.
He made many good contributions for newbies like me, if you have time, please go to his profiles and read through his posts on different issues.

[COLOR="Blue"][B]So my conclusion so far my wg111v2 and WPA-personal is not reliable, but can connect successful. I have to unplug and plug usb wg111v2 again to get internet RE-connection every 10-15 minutes.

And I have reliable automatic mode(NetworkManager) ***_for WEP 128kbit HEX connection_***[/B][/COLOR]
[COLOR="Teal"](IF YOU HAVE INSTALL NDISWRAPPER AND STILL HAVE NDISWRAPPER IN THE SYSTEM - BLUE LED BLINK EVERY 10-15 SECONDS- IT WON'T WORK, THAT IS WHY I DID NEW FRESH INSTALL, but if you want to uninstall ndiswrapper, phytheas22 gave instruction in below post)[/COLOR]

================== instruction start here ==================

I install new Ubuntu 8.04,
After complete login and on full normal desktop display.
Just plug in wg111v2 to any USB port.

It work after 10-15 seconds.
At the Network Manager icon, with left click, it show the wireless network only after 15 seconds or so.

and [COLOR="Red"]there is no blinking LED at all on wg111v2[/COLOR].
[COLOR="Magenta"]don't panic, it works[/COLOR] -
in other post other folks confirm this too.

I first log in using automatic mode, WPA, AES, DHCP.
(click on the wireless network radio button to choose the net work you want)

[U]If you have connected successfully then ignore the rest of the post.(pytheas22 and others confirm the success)
BUT IF YOU CANNOT CONNECT or later has problems read further.[/U]

[COLOR="Red"]**_I have Problems._**[/COLOR]

[COLOR="Blue"]It did not connect. It show the sign not connected, red x, or sometimes the signal chart bar scale, as if it is connected, but 0% connection when you move the mouse pointer over the chart bar scale.[/COLOR]

[COLOR="Red"]I change to manual mode. with the same password setting.
It connected instantly.[/COLOR]

If you have problems still, shutdown (don't use restart), and try again.

After I wrote the original instruction, and a few "shutdown". 
I could now connect to the internet using "automatic mode" with WPA-AES but not stable. only reliable with the manual mode for my ECS desknote.

But I found later **_after update to the latest packages by Update Manager_**,
*_it is not reliable for my ECS Desknotebook any longer_*, f**or all WPA connection.**
and I have to use WEP 128bit HEX instead, which is reliable.

ECS desknote, Pentium 4 (1.8 Ghz)
Netgear wg111v2
Acces Point is NetGear DG834GSP v3 Optus (Melbourne,Aus)-wireless router ADSL2+
SETTING Password type=> WPA+WPA2, DHCP, Mac address fileter enabled.
I am only 5 weeks old (by 10/JUNE/2008 ) Ubuntu user. 


==========================================================================

[COLOR="Blue"]Below post is just the old post I leave it here for the moment so the GURU knew what I did. Other [COLOR="Red"]newbies please ignore the rest[/COLOR] of this post.
****************************************************************[/COLOR]

[B][I][COLOR="Red"]Do not waste time to use GUI installation wpn111 for wg111v2, it doesn't work with ndiswrapper driver for this moment 11/07/2008
[/COLOR][/I][/B]

 EdgeOfEpsilon(First Cup of Ubuntu) post confirm the same result, but he/she has successfully install V2 (still wait for his/her confirm if his v2 = wg111v2).

[B][COLOR="Red"]He said he used the manual command line installation from this tutorial for wpn111,
and it works for him with V2

[http://ubuntuforums.org/showthread.php?t=652910&highlight=wpn111](http://ubuntuforums.org/showthread.php?t=652910&highlight=wpn111)[/COLOR][/B]

new EDIT
I uninstall ndisgtk and the other related 2 packages.

And I tried wg111v2 with above link, manual installation.
It made my wg111v2 BLUE LED 5 blinking every 10 secs.

BUT CANNOT CONNECT TO MY NETGEAR WIRELESS ROUTER,

MY WPN111 reinstall and connect perfectly.

Any GURU can you help
????



===============================================================================

I gave up and conclude that wg111v2 can not be install with my below tutorial for wpn111.

Unless there is an upgrade to Ubuntu packages that UPDATE MANAGER do update for us.


So at the present you got to use command line to do the installation.

Please look at the details tutorial at

[http://ubuntuforums.org/showthread.php?p=5289197#post5289197](http://ubuntuforums.org/showthread.php?p=5289197#post5289197)
[COLOR="Red"]
I believed that other wireless card which has only windows drivers should work the same way as wg111v2 and wpn111.[/COLOR]

YES IT WORK FOR ME BUT [COLOR="Red"]ONLY FOR 3 HOURS, THEN IT STOP FOREVER -- READ FURTHER ON PLEASE[/COLOR]

I was using wg111v2, installed with above tutorial for wpn111,
connecting to internet and WRITING AND EDITING the wpn111/wg111v2 tutorials perfectly for 3 odds hours, then it stop, the blinking BLUE LED, had stop blinking.

I spend another 6 hours odds now still cannot find out what went wrong.

I have the second wg111v2, I use it, it won't work too.

So I do:

1. I remove all drivers, wg111v2 and wpn111, and reinstall only wg111v2, it blink once when the driver was installed. And it won't blink again, at all. 

2. However the Network Manager or the Network Icon on the task bar is showing up wireless net work, and when we try to connect it shows the password window, WEB 128bit HEX, I key password in, chose Shared, then connect. It tried to connect and stop after 1-2 minutes.

3. So I removed wg111v2 and the driver, then installed wpn111 driver.

4. Plug wpn111 and right click disable and later enable Network Manager Icon. Wait 15 seconds or so, then left click Network Manager Icon again, wireless network showed up, I click my wireless network, select WEB Hex, key in password, select shared, and it took almost 1 minute and it connected perfectly.

I try the above steps, 1-4 steps, 3 times, it repeated the same result.

I did try to do exactly the same as the first time that is install wpn111 driver and the USB wpn111. Test it with 100% good connection immediately, no hick up at all. But wg111v2 never work again. 

I plug wg111v2 and reboot computer then choose XP Severice Pack 3 OS.

No surprise, it login with the same network perfectly without doing anything.

And I am writing this post with wg111v2 connection from XPs3 boot.

I am new to Ubuntu, so I can give you only what I have successfully done and not successful.

Good Luck
Long Live UBUNTU and all the Linux guru_s

Can the GURUs comment on that, please?

---

### Post by pytheas22 on 2008-07-07
My WG111v2 just works when I plug it in.  I don't need to do anything else; ndiswrapper is not necessary.  It does have some stability issues on 64-bit (on 32-bit it's absolutely fine) that might lead you to try ndiswrapper.  But you shouldn't need to do anything at all to get it to work, if you have the same chipset as mine.  It's possible that there are multiple versions sold under the name WG111v2, but I thought they were all exactly the same.  What is the output of:
```

lsusb
```

---

### Post by aimwin on 2008-07-11
> **pytheas22 said:**
> My WG111v2 just works when I plug it in.  I don't need to do anything else; ndiswrapper is not necessary.  It does have some stability issues on 64-bit (on 32-bit it's absolutely fine) that might lead you to try ndiswrapper.  But you shouldn't need to do anything at all to get it to work, if you have the same chipset as mine.  It's possible that there are multiple versions sold under the name WG111v2, but I thought they were all exactly the same.  What is the output of:
```

lsusb
```

Yes it work on my new installation of Ubuntu 8.04 only, 
not my old Ubuntu 8.04 that has been installed with ndiswrapper though,
but because I don't know how to uninstall ndiswrapper properly.

I tried all the uninstall option, GUI (ndisgtk) and the manual ways.
But in the list of loading modules it still stay up there almost the top.
I can't remember the command that I list loading modules now so I can't gave you that listing.
--------------------------------------

Another point though, the wg111v2, will not connect using automatic connection mode, on my desknote with WPA-personal.
But it work fine with Manual mode.

I found that Manual mode has extra setting to choose DHCP, which could give the successful connection.

Do you know how to force the automatic connection to use DHCP, if we can try that we may know the real answer.

Thanks a lot

---

### Post by pytheas22 on 2008-07-11
I'm glad you got the card working and thanks for writing out instructions above.
> 
Do you know how to force the automatic connection to use DHCP, if we can try that we may know the real answer.

I'm pretty sure that the automatic connection mode uses DHCP too--the only difference between automatic and manual is that automatic is supposed to guess the wireless security type automatically, instead of using whichever protocol you specify.  Sometimes it guesses wrong, however, which I think it is doing in your case.  I'm able to use automatic mode to connect to my Netgear router with WPA/TKIP encryption without a problem, so I don't think it's the WG111v2's fault that you can't connect with automatic mode.  Maybe there's something special going on with your router that causes connection in automatic mode to fail.
> 
I tried all the uninstall option, GUI (ndisgtk) and the manual ways.
But in the list of loading modules it still stay up there almost the top.
I can't remember the command that I list loading modules now so I can't gave you that listing.

As for uninstalling ndiswrapper, you have several options.  First, use Synaptic (System>Administration>Synaptic Package Manager) to uninstall the packages "ndiswrapper-utils" and "ndiswrapper-common" (ndisgtk will also be automatically removed, since it can't exist without ndiswrapper).  Alternatively, you can do the same thing with the command:
```

sudo apt-get remove ndiswrapper-utils ndiswrapper-common
```

Or you could "blacklist" the ndiswrapper module.  This wouldn't remove ndiswrapper from your system, but would just disable it, preventing the ndiswrapper module from loading.  To do that, you have to open the file "/etc/modprobe.d/blacklist" and add the line "blacklist ndiswrapper" to it.  Then reboot, and ndiswrapper will be deactivated until you remove it from the blacklist.

---

### Post by aimwin on 2008-07-25
Thanks Pytheas22 again

I uas WPA - PERSONAL and with automatic mode(NetworkManager nm-applet 0.6.6) it work ok with my ECS DeskNoteBook now. But it will stop working after 5 or 10 minutes.
I have to disable and enable NetworkManager before it work again.
And more than 70% I have to actually pull(un plug) the wg112v2 from the usb port and plug in again.

It will connect and work again and it will be dead again in not more than 10 minutes.

So I finally update fresh CD installed Ubantu 8.04 to the lastest packages using update manager,

And the problems still exist.

So I am going back to the manual mode for NETWORKMANGER again.

And it is similar problems, I have to unplug and plug USB-wg111v2, to get the internet reconnect again, after every 10-15 minutes of successful connection.

[B][U][I][COLOR="Red"]So my conclusion so far my wg111v2 and WPA-personal is not reliable, but can connect successful.
[/COLOR][/I][/U][/B]

I will try on my other notebook about uninstall Ndiswraper and or blacklist it later.
Thanks alot.

---

### Post by pytheas22 on 2008-07-25
> I uas WPA - PERSONAL and with automatic mode(NetworkManager nm-applet 0.6.6) it work ok with my ECS DeskNoteBook now. But it will stop working after 5 or 10 minutes.
I have to disable and enable NetworkManager before it work again.
And more than 70% I have to actually pull(un plug) the wg112v2 from the usb port and plug in again.

It will connect and work again and it will be dead again in not more than 10 minutes.

I have this same behavior on 64-bit.  I'm not sure, but certain websites seem to trigger the card to crash, which makes me think that it's not a problem of crashing after a certain period of time, but of being unable to handle some specific kinds of traffic.  If I leave my computer idle for three hours with the wg111v2 on and come back, it works fine.  But as soon as I visit certain sites (facebook is an example), it crashes, and like you, I have to unplug it for it to work again.

I should also mention that although the wg111v2 seems to work better on 32-bit, it has crashed on me a few times on my 32-bit computer.  But I thought that maybe it was my router.

So to see if our experiences are similar or not, I have these questions for aimwin:

1. do you notice the wg111v2 crashing when you visit certain websites?
2. does it crash when your computer is idle or only when you're surfing the Web?
3. are you using 32-bit or 64-bit?

Also, it would be helpful to see the output of dmesg right after the crash.  Run the command "dmesg | tail" and post the output here.  I'll do the same the next time mine crashes.

Finally, I should mention that a couple of years ago, I used the wg111v2 under ndiswrapper (it had no native driver then) on Mandriva 2006, and had similar problems (crashing when I visited certain websites).  At the time I thought it was a problem with ndiswrapper and ended up just buying a better wireless card (I only tried the wg111v2 again recently because I found it in my basement and wondered if its Linux support had improved by now), but it is a strange coincidence.  If you try using ndiswrapper for the wg111v2, aimwin, see if you have problems.

---

### Post by tomjennings on 2008-09-15
There are two different chipsets used in the wg111v2! Different USB IDs... the one with the prism chipset works fine (driver p54xxxxx) the bad one uses rtl8187 and fails when attempting to move "a lot" of data through it.

So how to make the rtl8187 driver reliable? is the question...

---

### Post by aimwin on 2009-10-31
> **pytheas22 said:**
> I have this same behavior on 64-bit. ..........
So to see if our experiences are similar or not, I have these questions for aimwin:
1. do you notice the wg111v2 crashing when you visit certain websites?
2. does it crash when your computer is idle or only when you're surfing the Web?
3. are you using 32-bit or 64-bit?
.............  If you try using ndiswrapper for the wg111v2, aimwin, see if you have problems.

Dear pytheas22 
I don't know how I miss those questions.
Sorry 

I found no problems at all with WEB 128 settings.
It works with no flaw regardless how long and to any sites.

Since I identified WPA instability for this wg111v2, I change the the access Modem/router to WEB 128, so I have never test WPA again.

To those Newbies and Oldbies looking for WPA issues please check 
[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

---

