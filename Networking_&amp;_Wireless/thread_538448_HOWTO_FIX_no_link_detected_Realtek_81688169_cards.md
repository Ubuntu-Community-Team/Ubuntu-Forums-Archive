---
title: "HOWTO FIX no link detected Realtek 8168/8169 cards"
date: 2007-08-30
forum: Networking &amp; Wireless
---

### Post by noob12 on 2007-08-30
A number of users have been independently reporting an issue where they see no link detected and/or no link light on their Realtek 8168/8169-based wired ethernet cards when booting Ubuntu on a dual-boot Windows host.  The card works in Windows but in Ubuntu it shows no link light and **ethtool** reports no link detected.  (This can also affect you on initial installation of a single-boot system, but after running Windows on the host.)

[SIZE="2"][COLOR="Green"]Several users have now reported that this works for some Realtek 8139 cards as well.[/COLOR][/SIZE]

(You can check if you have this type of card by typing the command **lspci -nn** and looking for your wired ethernet card in the list.)

Here is a fix for the most common causes.

First check that your ethernet cable is connected at boot.  There is a  known bug in the Ubuntu driver for this card that the cable must be connected to an active link at boot time for the card to work ([https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86798](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86798))

If your ethernet cable is connected at boot time and you are experiencing the no link problem, try this:  Shutdown, power down.  Unplug your host (this cuts power to the card if wake-on-lan power is maintained).  Wait 15 seconds.  Plug in.  Boot ubuntu.

If that routine works, you are probably affected by the following (excerpt from gentoo wiki [http://gentoo-wiki.com/HARDWARE_RTL8168](http://gentoo-wiki.com/HARDWARE_RTL8168)).  Note the second and third paragraphs.  Then read the Windows-side workaround/solution in the first paragraph.

> 
As of 27 May 2007, in kernel 2.6.21.3, you may experience the issues with the r8169 driver if you dual boot Windows on some systems. Windows by defaults disables the NIC at Windows shutdown time in order to disable Wake-On-Lan, and this NIC will remain disabled until the next time Windows turns it on. The r8169 driver in the kernel does not know how to turn the NIC on from this disabled state; therefore, the device will not respond, even if the driver loads and reports that the device is up. To work around this problem, simply enable the feature "Wake-on-lan after shutdown." You can set this option through Windows' device manager.

Edit: Problem with dual-booting with Windows exist also in 2.6.19.5 and 2.6.20.8 kernel, so it is safe to assume that it will concern all 2.6 kernels until the kernel developers update the drivers for RTL8168 to the version that will be able to turn on the NIC from disabled state. (Corey)

Second edit: Powering off and unplugging the machine for a few seconds (around 10 usually does it) seems to reset the card, so it will work in Linux again until you boot Windows again.


[COLOR="Red"]ADDED NOTE: Please use the poll above only if your situation actually matched the one described here (same symptoms, same hardware and dual boot)[/COLOR]

---

### Post by peterroots on 2007-08-30
I seem to have what seems like the same problem using a Toshiba texra with an
Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83) (according to lspci)
and also with a Xircom realport ehternet10/100 pcmcia card.
This solution did not work for me (the inbuilt card worked initally but then stopped but still works in windows).  I tried the toshiba control, hardware setting to select wake on lan enabled and also tried in the hardware section of mycomputer-> properties.
the xircom had no wake on lan setting and the built in card had opitons of dissabled, os control or force. I tried force first of all then tried os controlled. Niether worked
If anyone out there has any ideas they would be greatfully received.
(an old Dlink DE-650 seems to work fine).

---

### Post by noob12 on 2007-08-30
Please do start a new thread if your situation doesn't match the one here (meaning you don't have the same symptoms and same hardware in a dual boot situation with Windows).  It probably requires completely separate diagnosis.  I and others on the forum will help.

---

### Post by peterroots on 2007-08-31
Thanks for your comment, I posted here as the situation seemed the same just slighly different hardware.
Anyway the problem is now solved, only thing is I am not sure which extra things I did acutally fixed it and which were superfluous!
First I am using a Toshiba Tecra (not a texra - finger slipped yesterday!)
 After trying the suggested fix and rebooting both with and without an active net connection plugged in to either the built in port or the plug in port I had no network connection and the built in port did not show up on the knetworkmanager. Stoped and started knetworkmanager several times with and withought the net cable plugged in - no change
In settings network, I could see the built in but realised it was no longer activated on boot so I changed this an rebooted - still did not work but was visible on knetworkmanager.
stoped and started knetworkmanager again - still no luck.
I then selected manual settings on knetworkmanger and found that here the card was not acitvated on boot even though I had changed it on system settings network! so I changed that as well and rebooted again (with a net cable plugged in).
This time it all worked.
Now I can plug and unplug network cables to my hearts content and things work as they had originally (just after installing Kubuntu)
So many thanks for pointing me in the right direction!

---

### Post by 3ntity on 2007-09-05
Thanks, this did the trick :)

---

### Post by toketin on 2007-09-24
i've tried to do it in windows, because i've a network card, Dfe-528Tx of D-link that uses the modules 8139cp and 8139too, it's seen by ubuntu, but the system doesn't recognize it, maybe it's a problem with windows, i've tried but the adavanced option of my card are these:
[[IMG]http://img442.imageshack.us/img442/7131/immagineef8.th.jpg[/img]](http://img442.imageshack.us/my.php?image=immagineef8.jpg)
the second and the last three option are enabled but ubuntu doesn't still recognize the card.... how can i do?

---

### Post by noob12 on 2007-09-24
This fix will only work for the specific problem whose symptoms are described here; everything will look right (you'll see the interface in i**fconfig -a**) but **ethtool** will show that you don't have a link detected, and the shutdown/unplug test will solve the problem.  If the shutdown/unplug test didn't work for you, you probably have a different problem.  If you post  a new thread with the details and PM me, I'll try to help you.

---

### Post by SpiritIsReality on 2007-09-29
howdy
noob12 ... thankyou sooo  much for being here. 
I found hope here on a search. 
pals

---

### Post by SpiritIsReality on 2007-09-30
howdy
>If your ethernet cable is connected at boot time and you are experiencing the no link problem, try this: Shutdown, power down. Unplug your host (this cuts power to the card if wake-on-lan power is maintained). Wait 15 seconds. Plug in. Boot ubuntu
>>unplug your host from the power source. thanks

---

### Post by jcordone on 2007-10-17
Hello,

I have an Acer Aspire 5100 laptop with a RTL8139/810x (according to Windows) network adapter.  A while ago it stopped working for Ubuntu.  After trying everything I could think of, including reinstalling Linux, I finally tried what works to reset most machines.  I unplugged everything from my laptop, including the power cord, and removed the battery for a few seconds.  After reinstalling the battery, and reattaching everything, the network adapter worked fine under Linux.

Every single time that I boot from Windows XP, my network adapter will not work under Linux again, until I finally unplug and remove the battery to reset it!  This seems to reset something in my system so that Linux can use the network card again.  And I can reboot between Linux sessions, without any problems, however, after booting Windows just once, it will not work again under Linux, unless I reset it as described above.

I don't remember if I downloaded any windows updates before this started happening, but it makes one wonder, just a bit.  :mad:

--jcordone

---

### Post by noob12 on 2007-10-19
Follow the instructions to enable Wake on Lan on the windows side.

---

### Post by gregfaust on 2007-10-20
Followed the instructions and resolved my problems using Ubuntu 7.10 Gutsy Gibbon with a Realtek RTL-8139/8139C/8139C+

Thanks!

---

### Post by cytacc on 2007-10-25
thank you guys.You really help me!that works!

---

### Post by julian67 on 2007-10-26
This solved it for me. I have a Realtek 8139 and dual boot XP and 7.04. An update to the Windows Realtek driver had left the "wake on lan after shutdown" disabled and the Linux driver couldn't properly bring the card up (though DHCP and routing was all OK but no traffic). I had rolled back the Win driver as a temp fix. sam75 kindly pointed me towards this thread and  I have now applied the Win update and enabled the "wake on lan after shutdown" and all is good in Xubuntu again.

---

### Post by Tsume on 2007-11-01
I have an 8139 and this fix worked.

I'm kinda sad that I had to spend 30 minutes googling for this solution, this card is probably the most common 100mbps NIC in the world, and dual booting is a very common practice.

Enabling WOL on Shutdown in Windows works.

---

### Post by julian67 on 2007-11-01
> **Tsume said:**
> I have an 8139 and this fix worked.

I'm kinda sad that I had to spend 30 minutes googling for this solution, this card is probably the most common 100mbps NIC in the world, and dual booting is a very common practice.


The change to the Windows driver is a) recent, and b) not an automatic update (it has to be explicitly selected by user). So while the card is common the problematic config change may not be.  It's worth remembering that MS describe this as a driver update and do not state anywhere I could find that the config of the card would be changed.  They deserve all the criticism they get for doing undocumented and obscured things via the update process while showing no regard for the customers.  I'd got as far as realising that the driver update was causing the problem (and had rolled back the driver) and had filed a bug report and then someone kindly pointed me to this thread. I would never have noticed this change as I don't use wake on lan. You should save your disdain for MS, and give the Linux and Ubuntu community some credit for working around this and more importantly for doing things in an open and honest way that benefits everyone.

---

### Post by The Storm on 2007-11-05
Hi all,

This fix worked for me too, thanks. :)

---

### Post by iansane on 2007-11-06
I know this is an old topic but isn't wake on lan a security risk? What if i have a reason for not wakeing on lan? Is it like when I have my phone modem plugged in and everytime the phone rings the computer turns on so everytime my ISP sends out a signal it will turn on? I don't know, just curious.

---

### Post by s0ulreaver on 2007-11-06
The fix worked for me as well on an HP Pavilion a1030n.
Can this issue be fixed? Is this going to be fixed later on in Ubuntu?

---

### Post by braedsjaa on 2007-11-07
This worked for me. THANX :KS

For the information of others: my machine is a Fujitsu Siemens desktop with Realtek **8139** NIC dual booting with WinXP with several recent updates. 
Anyway, now it is happily upgrading itself to Gutsy as I write this :-D

Posts on other forums and blogs also point to the new windoze driver as the problem.
I too was wondering what the side effects are of allowing wake-on-lan, and I presume that disabling it *does* make a lot of sense and is possibly part of Microsoft's efforts at improving security (though it would have been nice if they pointed out the config change, or indeed tell us *any* details at all about the "upgrade"). Maybe it serves me right for assuming that all upgrades are a good idea even when I have no problems?

---

### Post by ParanoiaPersonified on 2007-11-07
This worked for me with the following:

02:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)

I haven't voted (due to the different version of card), but will do so if advised.

Cheers for the help - very useful for a complete linux n00b!

---

### Post by noob12 on 2007-11-09
Thanks. Yes, it is reported to work for Realtek 8139 cards as well.  Please do vote.  I wish the forum folks would make this sticky.  I keep having to refer people manually.  Google "Realtek no link ubuntu" does a better job than the forum at finding this currently.

---

### Post by ryamar1177 on 2007-11-13
This thread saved me from using windows forever! I was so frustrated because I could not figure out why the LAN connection worked about 6 months ago but on the new update to 7.10 would fail... leave it to M$ to set up some strange parameter that we would have to work around!

Thanks very much to the Ubuntu community!!!

---

### Post by anders_r_r on 2007-11-20
Unplugging the cable for a short time didn't solve the problem. However, enabling Wake-on-LAN in Windows did the job. 

I am an absolute Linux beginner. So far, my only Linux experience is booting from a Kubuntu live CD on a PC running Windows 98 with a Realtek 8139 installed.

Thank you very much for providing the solution to this problem!

---

### Post by mcwtlg on 2007-12-01
Just another reason to dislike M$.  I was working just fine on the dual boot box (my wife uses the Windows side) and I noticed updates.  I saw a new network driver update so I took it.  That was two days ago.  I just now got it fixed.

Thank you for posting this.  This only shows me yet again that the Linux community (esp the *buntu folks) are tops.  I just wish my wife would use Linux.  I would just trash the whole Windows thing for good.

---

### Post by jssand2 on 2007-12-01
Thanks to the experts ... this advise worked perfect

Easy fix .... changed the windows hardware properties for the NIC to "Wake on LAN" ENABLED.

Reboot and works as before.

---

### Post by skarp7c1 on 2007-12-17
Great I have found this. After installing windows on another hard drive and rebooting into Ubuntu to add it into grub list, I couldn't connect to the internet anymore.

Worked perfectly, just enabled wake on lan in windows, rebooted and was done.

Thanks a lot.

---

### Post by bimmerd00d on 2007-12-17
Fixed my 8139!!!!!! AWESOME.

---

### Post by akmgg on 2007-12-17
FIXED my Realtek 8139 - enable wake on LAN

THANKS!!!!!!!!!!!!!!!!!!

---

### Post by Jive Turkey on 2007-12-20
This solution worked for me, my card appeared to be configured properly on ubuntu 7.10 but wouldnt actually connect to my router.  I booted into windows and unticked the box for "Let windows power down this device"

rebooted to ubuntu and it works now

---

### Post by alladnsane on 2007-12-29
My problem was very similar with dual boot XP and Gutsy.  Everything worked fine till yesterday then wham - no internet in Ubuntu.  Ubuntu recognized my eth0 card but wouldnt connect to dsl modem.  ISP refused support to linux.  unticked the box for "Let windows power down this device" in the device manager network card section of windows and now my connection is back up...not a realtek card though....

02:00.0 Ethernet controller [0200]: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter [1969:2048] (rev a0)

Actually my problem is only partially fixed.  I can use my ethernet in Ubuntu but I do still have to shut the system right down and power off with the switch at back of PC or unplug it after being in windoze

---

### Post by csmth on 2008-02-03
I am glad to hear the "enable wake on LAN" solution but it is weird for my HW (AsRock CORE1333), because my driver don't have "wake on LAN" after "OffLoad TCP LargeSend".

I can't use this solution.

---

### Post by djxstream on 2008-02-23
hours upon hours of troubleshooting after the link went dead...didnt think upgrading to XP SP3 RC2 was the culrpit....thank you!!!!!!!!!!

---

### Post by ijf8090 on 2008-02-27
This worked for me - Ubuntu 7.10\Vista dual-boot on Compaq Presario C700T. Appreciate the help - would never have figured it out myself....

Next stop the Broadcom wireless drivers

:)
Ian (very new user)

---

### Post by ijf8090 on 2008-02-29
That should read next stop the Atheros 5007EG wireless drivers and that's even less fun than the Realtek drivers. 

After several days poking around they're still not working. Apparently lpsci mis-detects the chip set - it may be 5006EG ([http://ubuntuforums.org/showthread.php?t=662877](http://ubuntuforums.org/showthread.php?t=662877)) . 

Booted Windows to check - it is 5007EG. 

I did try madwifi solution - but still having problems - I think it may be because Windows shuts off the Wi-fi adapter when it shuts down....
 

May have to use ndiswrapper - which has not worked well for me up to this point - anybody know where I can find XP 32-bit  drivers.


This is such fun....

BTW - Compaq online support was less than helpful. 'We don't support anything but installed OS'.  Out of stubborness - I asked where this was documented and 30 minutes later they referred me to a very obscure link which said that Vista could legally be downgraded to XP, but they would not support it...

Also thinking about getting a USB wireless adapter - I've heard DLink is good. Any other suggestions?

Ian
Not so much an Ubuntu god - more like a Garden gnome<s>....

---

### Post by Loosewheel on 2008-02-29
I had the same problem dual booting Vista and PCLinuxOS. No network when booted up in Linux. It happens that a windows update for the NIC was the deal. I rolled back the driver in Device Manager and all was well.

---

### Post by FishRCynic on 2008-03-01
8139 - hardy - appears that the updated driver killed winxp mce connection too :-) - hp a530n wiith integrated networking - no connection in windows or hardy - (older machine out of mothballs for i386 testing) . Setting all the link options in driver to enable corrected issue in winxp.  (was using my old faithful wireless inexq ur055g for network connection) am rebooting in to hardy to check resolution but hit the routine drive check (as it is an older 160gb eide this might take a while and i would prefer not to skip at this point - there may be drive issues as well) will update as to result.

03/02/08
this did work as the hardy live cd now has no problem setting up the 8139 for networking.
The harddrive unfortunately decided it was no longer serviceable. (another lilt)

---

### Post by larsdk on 2008-03-13
I (obviuosly) have the same problem, but I cannot see the "Wake on lan" on the advanced windows properties of the 8139 NIC. 

I can only see these options (related to wake up)

Wake Up on ARP/Ping
Wake Up on Link Change
WakeUp using APM Mode

Is it any of those?

Any help very much appreciated
Lars

---

### Post by Jerry41 on 2008-03-19
> **djxstream said:**
> hours upon hours of troubleshooting after the link went dead...didnt think upgrading to XP SP3 RC2 was the culrpit....thank you!!!!!!!!!!

DITTO!

My HP Pavilion a1243w with a Realtek 8139 NIC (Dual boot XP / Ubuntu)  had been working for several weeks & I was becoming acquainted with Ubuntu a little at a time, when one day I logged on and got a message that there were updates to be installed. When I clicked to install, I was informed that there was no internet connection.I had apparently  LOST a working connection.

THANKS for the information, I  changed my setting to , "enable wake on LAN", and now it works fine. BUT it took me about two months to find this thread with the easy fix - after TWO complete reinstalls of Ubuntu. 

With the number of successes on this thread, maybe it should be sticky.

---

### Post by Jerry41 on 2008-03-21
"No internet connection"  was my original search which found no help. There seems to be no interest in making this sticky, and I find no reference to it on any of the excellent instructions for connecting to the internet. 
I would certainly suggest trying "enable wake on LAN" if you are unable to connect to the internet via wired dsl and a Realtek NIC.

---

### Post by smultronstallet on 2008-03-23
I've independently come to this solution for many Realtek Ethernet cards that aren't able to establish a connection, yet still appear normally in the operating system. This is a slightly faster way:

[LIST=1]
[*]Shutdown the computer completely
[*]Unplug the power cord from the computer
[*]Press the power button while computer is unplugged
[*]Re-plug in power cord and boot back up
[/LIST]

Pressing the power button while the computer is unplugged drains all of the residual power left in the computer immediately (which removes all power from the Ethernet card in question). This is a little faster than waiting the 30-45 seconds needed to let it stay unplugged otherwise. Hope this helps.

---

### Post by must4rdgas on 2008-04-10
I followed this and have managed to get the no connectivity light to disappear on my DSL router, so now all is well on the router side.

But I still can't get pppoeconf to work. Still can't find access concentrators. :(

---

### Post by mennonot on 2008-05-15
I just installed Xubuntu 8.04 and encountered the no link problem with my Realtek RTL8139/810x Family Fast Ethernet card. These instructions fixed it for me:

[INDENT]Shutdown, power down. Unplug your host (this cuts power to the card if wake-on-lan power is maintained). Wait 15 seconds. Plug in. Boot ubuntu.[/INDENT]

Thanks.

---

### Post by Porwah on 2008-05-15
Thank you so much for your post.

Unfortunately, I've tried that repeated times.  There's nothing unusual about that process that I could missing, is there? 

I mean two nights ago I rebooted 20-30 times! Last night, not as many times, but definitely rebooted a good number.  Yea, and I've tried unplugging  the (AC) cord for a good 15 seconds too at times in that process too.  

(Incidentally, it doesn't matter if I pull the plug or not, I never see the LED's on the nic lit when the PC is powered down.  I don't know if that means anything at all.)

Gah! Doh! @$!#! It's very frustrating when it looks like the solution you suggest works for other users with the same nic and similar issues.  It wouldn't surprise me if I'm missing something really stupid here.

OOPS.  If this post sounds out of context, it's because I thought you were responding to my similar thread/issue here:
[http://ubuntuforums.org/showthread.php?t=794701](http://ubuntuforums.org/showthread.php?t=794701)

---

### Post by Feli26 on 2008-06-05
lol how easy, thanks man :)!

---

### Post by Porwah on 2008-06-05
I actually got Ubuntu to get on the network when I booted when the noapic boot parameter.  It seems there was some IRQ issue.

---

### Post by xalen on 2008-06-17
> **Porwah said:**
> I actually got Ubuntu to get on the network when I booted when the noapic boot parameter.  It seems there was some IRQ issue.
Does the noapic option work for other users?  Anybody found it doesn't work?  A permanent fix for this would be nice.  If the noapic boot parameter does work I'll write how to permanently add it to your boot options or perhaps someone else could.

Edit: Hey guys.  I don't think the noapic option worked for me.  Still scratching my head. The circumstances that I don't get a connection don't seem to be constant.  But I'm looking at that release candidate down there vvv :)

---

### Post by ajkessel on 2008-06-22
None of the solutions listed here worked for me. The link light always turned off halfway through boot-up. The machine is not dual-boot, and I don't have a Windows box in which to try configuring the device. Finally, I solved it by adding the following to the appropriate stanza in /etc/network/interfaces:

pre-up /usr/sbin/ethtool -s eth1 autoneg off

Documented in slightly more detail [here]("http://adam.rosi-kessel.org/weblog/2008/06/21/a-much-simpler-fix-for-the-r8169-link-down-problem").

---

### Post by ajkessel on 2008-06-22
I just noticed that my autoneg off solution doesn't give me gigabit ethernet. If I force the speed to 1000 with ethtool -s eth1 speed 1000, the link goes down again. So I've got no way to make a link at 1000BaseT. The same card in another machine, however, autonegotiates at gigabit automatically with no problem.

Any ideas? Is there a driver fix in the works?

---

### Post by ajkessel on 2008-06-24
Update -- 2.6.26-rc5 fixes the problem for me.

---

### Post by kde4-core-user on 2008-06-27
THX! After a long search and vicious headache, this fixes my problem finally !!!

---

### Post by Crosbie on 2008-06-27
Confirmed for 8139 - thanks so much for this.  Had a second card, same chipset, tried that - it worked!  At first.  Then the other one worked instead!  Okay, so switch to that.  Now neither work!  Only when I unplug the computer to take one out - the other one starts working again!  This was really foxing me - should have known Windows was borking it each time. :)

---

### Post by kiev on 2008-07-04
RL8169c does not work (((((((((((((((((((((((((((((((((((((((((

---

### Post by manlypain on 2008-07-19
I believe this is related to this topic.  i have this same link issue from time to time but a reboot usually fixes the issue.  Does anyone have a stalled dns request issue as well.  If i open to many tabs in FF or make to many dns requests it will stall for 30-45 seconds.  It does not slow down, it stops being able to make dns requests.  I can make requests by IP but no dns lookups.  I ran nslookup during one of these stalls and that failed as well.  I just want to know if anyone else is having the same issue.  My realtek is an onboard nic using the r8169 driver.  The MB is a Gigabyte GA-EX38T-DQ6.   I used the DNS servers from my ip and swapped to opendns as a testing measure.  no matter what dns servers i use i still have this issue.  I don't have this problem using any of the other computers i have on this network.

---

### Post by agentphish on 2008-07-20
Worked on a Compaq C762nr laptop. Strangely I had to switch ports on my router before I got it to work. I have no idea why that would be.

Dual booting Ubuntu and Vista.

Now to get the Atheros WiFi working.

---

