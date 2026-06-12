---
title: "Linksys WUSB 11 v. 2.6 and WPC11 v. 4 don't work in Feisty"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by fwheeler_1 on 2007-04-20
Hi-  I've been using (KX)Ubuntu since 5.10 (at least the versions that were available then).  With both 6.06 LTS and 6.10, the above WiFi cards have worked automatically with native drivers--no ndiswrapper needed.  They are both in the WiFi wiki as being supported in Ubuntu Dapper and above.  

Now with my new install of 7.04, neither of them work.  With a "ifconfig" or "iwconfig", nothing shows up, except for the loopback adapter.  With 6.10, the WPC 11 (which is a pc card) reports after a "lspci":

06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)

With the USB adapter, in 6.10 all I get with a "lsusb" command is:

Bus 001 Device 003: ID 077b:2219 Linksys WUSB11 V2.6 802.11b Adapter

So, I don't know what driver it is using in 6.10.  But, I can say for sure that I am very frustrated that they won't even be detected, let alone work, in 7.04

Has anyone had a similar experience and gotten either of these to work with Feisty 7.04?  I've search the forums and tried Google, but can't find anyone else with this issue--but there does seem to be alot of wifi problems associated with this release.

Thanks in advance, FW

---

### Post by kd5gje on 2007-04-20
I have the same issue with my wireless PC card, the WG311T.  It worked in 6.10, but no more.  I will let you know if I find anything.

---

### Post by kd5gje on 2007-04-20
I got mine working.  I uninstalled network manager and installed wicd.  Works like a champ now

[http://adam.blackhole.cx/wicd/wb/](http://adam.blackhole.cx/wicd/wb/)

---

### Post by fwheeler_1 on 2007-04-20
Thanks for the reply; I'll give it a try.  Glad you got yours up and running.  --FW

---

### Post by numerodictulibertas on 2007-04-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78255](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78255) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				See this bug report thread for more information:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78255](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78255)

For the WPC11v4 the underlying problem is easy to fix.  Because it caused problems with some setups, the native driver (r818x) was placed on the module blacklist, so that if you're using the NDISwrapper driver from Windows then that would load instead.

To use the native driver, you need to remove the r818x blacklist entry, like so:

```
sudo editor /etc/modprobe.d/blacklist
```

Page down to the bottom, and you'll find some lines that look like this:

```

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187

```

Any line that begins with "#" is ignored, so add "#" in front of the r818x line to turn off the blacklisting of this module.  Save the file, eject and re-insert the card, and it should be recognized.  Again, see the thread I linked above for more info.

---

### Post by fwheeler_1 on 2007-04-27
Thanks, Numerodictulibertas!  I really appreciate your help.

I was just logging in to post an update. . .somehow, I'd bumbled on to some of the same info you gave, plus one other thing that really helped me maintain a connection.  I've continued to try network manager, but I've found that it drops connections a lot.  So, I've gone to manually starting the network using iwconfig.  

Additionally, another thread discovered that for the essid, an additional character needs to be appended to the end (any character will do, although 'x' seems to be the current favorite).  Thus, if your essid is "ducky", you'll need to use "duckyx".

So, without further delay, here is what is currently working well for me (after I plug in the card):

```
sudo modprobe r818x
sudo iwconfig wlan0 essid duckyx
sudo dhclient wlan0
```

With Numerodictulibertas' excellent suggestion of commenting out the blacklist by adding a # in front of r818x, it shouldn't be necessary to modprobe r818x any longer.

I will experiment more with this an report any progress.  Thanks to Numerodictulibertas, and Cynical, soundguy666 and chili555 in another thead for all of the suggestions/comments that made this possible for me.  You guys are awesome.  --Fw

---

### Post by Dr.Awesome on 2007-04-27
> **fwheeler_1 said:**
> Hi guys-  I see you've been struggling with the same problem I have been in another thread.  I think I've finally got a pretty good picture of what is going on.  The short version is the native driver was blacklisted for some reason.  It can be "unblacklisted" and then the module can be loaded.  Then you can see and configure the card.  I've had the best luck configuring it manually (e.g. not using network-manager, although n-m will see the card after a manual config).

For the long story, please see the thread I've been working in ( [http://ubuntuforums.org/showthread.php?t=414594](http://ubuntuforums.org/showthread.php?t=414594) ) and spead the word to others.  I'm posting this using the card, which has been running fine for about 2 hours.  Good luck to all, Fw

I went to your thread and I can now access the wireless network on net-manager, but I still can't access my wireless network to get online.  When I followed your instructions in the terminal, I got the following output:

warren@ubuntu:~$ sudo iwconfig wlan0 essid holysmokesx
warren@ubuntu:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 6598
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:0c:41:af:80:28
Sending on   LPF/wlan0/00:0c:41:af:80:28
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
warren@ubuntu:~$ 

Any suggestions?

-D.A.

---

### Post by fwheeler_1 on 2007-04-27
Hi D.A.-  Yes, here are a couple of ideas:

1.  Follow numerodictulibertas' suggestion of editing the blacklist file by adding a # in front of the driver and reboot.  After doing this, it is no longer necessary to manually load the wireless module (the "sudo modprobe r818x" part of my post.  Use only the iwconfig and dhclient commands.  Once the card is working correctly using the native driver, there are ways to make the iwconfig and dhclient commands work on boot up, too.

2.  From your post, it looks like your card already has an IP number (all the DHCP stuff).  Did you remember to remove the Windows driver for your card that you installed using ndiswrapper (or the gui equivalent)?  If you didn't, the laptop is trying to use two drivers (the Windows one and the native Linux one) for the same card at the same time, and that is a no-no.

Keep trying and good luck, --Fw

---

### Post by fwheeler_1 on 2007-04-29
Update to using Linksys WPC11 v. 4 with Ubuntu Feisty (7.04)

The difficulties encountered with this card are multifactoral:

1.  Potential bugs and other factors with the driver (r818x) that worked well with Dapper LTS (6.06) and Edgy (6.10) caused kernel devs to blacklist (e.g. add r818x to the /etc/modprobe.d/blacklist file) it.  While this aided in allowing the Windows version of the driver to be easily added, it took away native driver support for those that came from an earlier version of Ubuntu.

2.  There is a bug in the way the driver handles the essid of the access point in that the last character of the essid is dropped.  The recommended workaround is to add a bogus character to the essid name.  Thus, for an access point named "ducky", "duckyx" would be the essid name that would work.

3.  Network manager changes the way that network interfaces interact with the system.

Because losing wireless with my notebook is a showstopper, I have migrated back to Edgy 6.10 on my HD.  So everything described here is based on using the Live CD.  Since I am (at best) a user with moderate Linux admin skills, there may be some redundancy in the following description for those who are using a HD installation of Feisty.  I will attempt to add comments next to code that I think is redundant if the installation is on a HD instead of using the live CD:

Open /etc/modprobe.d/blacklist with gedit as root:

```
sudo gedit /etc/modprobe.d/blacklist
```

Add # in front of blacklist r818x to unblacklist the driver, then save file:

```
#blacklist r818x
```

Open /etc/modules with gedit as root:

```
sudo gedit /etc/modules
```

Add the driver r818x at the bottom of the file, then save file:

```
r818x
```

Load the wireless module r818x as root (if using an installation on a HD, this may be unnecessary if the computer is rebooted as adding the driver to the modules file should load it automatically at each boot)

```
sudo modprobe r818x
```

For Network-Manager to manage network adapters, they must be commented out (thanks to Buffalo Soldier for this one, in multiple threads).  Open /etc/network interfaces as root and comment out all interfaces by adding # in front of all interfaces except lo, which is the loopback interface.  For example:

```
sudo gedit /etc/network/interfaces
```

Add # to everything but loopback, then save file:

```
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp
```

Finally restart networking as root (When using a HD install, it may not be necessary to do this if the system is rebooted):

```
sudo /etc/init.d/networking restart
```

Plug in the WPC11, and Network manager will spring to life.  In my case, it automatically finds my access point (ducky), but will not associate because it drops the last character of the access point name.  To fix this, right click on the Network Manager icon in the upper tool bar (unless you changed this), select "Connect to Other Wireless Network" and in the dialog box for access point type in your name, with an extra character at the end (in my case, duckyx).  I suggest that no encryption be used until you get all of this worked out.

Network manager will find your access point and connect.  At this point, both ducky and duckyx will be present in Network manager.  Open Network manager with a left click, then select access point listed without the extra character (in my case, ducky).  Occasionally, Network manager goes into search mode (probably because roaming is selected in the network interface dialogue box by default) every once in awhile, so I lose about 4-6% of my packets upon sustained pinging of my router.  If you desire, you can use Network manager to switch to manual configuration, but remember to add the extra dummy character at the end of your access point name.

I'll update as new info becomes available.  Good luck and, as always, please post your experiences.  

--Fw

---

### Post by fwheeler_1 on 2007-04-29
Update to using Linksys WUSB11 v. 2.6 with Ubuntu Feisty (7.04) removed.

---

### Post by 416hammy on 2007-05-05
On my IBM Thinkpad A21m with a WPC11 v4, I have un-blacklisted the r818x driver per the above instructions, and I do get multiple hotspots listed when I am in roaming mode.  However, when I click on my own unsecured hotspot it will not connect (the animated icon does not show either indicator as green).

If I manually set the SSID, it will not connect.  If I manually set the SSID with a trailing "x" my laptop locks up when it tries to connect.

Someone please help! ](*,)

---

### Post by fwheeler_1 on 2007-05-06
Try booting up from the Live CD, then using the instructions in post #6 of this thread (manual configuration of the card that bypasses network-manager).  If that works, then you should be able to manually configure the card by directly editing the config files for a HD install.  -Fw



> **416hammy said:**
> On my IBM Thinkpad A21m with a WPC11 v4, I have un-blacklisted the r818x driver per the above instructions, and I do get multiple hotspots listed when I am in roaming mode.  However, when I click on my own unsecured hotspot it will not connect (the animated icon does not show either indicator as green).

If I manually set the SSID, it will not connect.  If I manually set the SSID with a trailing "x" my laptop locks up when it tries to connect.

Someone please help! ](*,)

---

### Post by 416hammy on 2007-05-07
> **fwheeler_1 said:**
> Try booting up from the Live CD, then using the instructions in post #6 of this thread (manual configuration of the card that bypasses network-manager).  If that works, then you should be able to manually configure the card by directly editing the config files for a HD install.  -Fw

No dice.  Same errors.

I'm sick of fighting this and have reinstalled Edgy pending some future news that this driver is properly supported.

This "blacklist" approach is such a cop-out. #-o

---

### Post by standards on 2007-05-08
for what it's worth, i had this same problem (feisty not detecting my wifi card), i searched the forums, found this thread, followed fwheeler_1's advice in his post a few replies back, unblacklisted the driver, and am now typing with the wpc11 v4. long live the ubuntu forums.

---

### Post by talen.quickblade on 2007-05-11
My problem seems similar, yet different. I am using a WPC11 v3 card.

Booting using the live CD, wirelss networking operates as expected. I can connect to hotspots, both unsecured and those secured with WEP 64 bit hex keys successfully. I have not needed to unload anything. Everything just works. Following installatin to the HD... now that is a totally different story.

After installation the mere presence of the wifi card causes a kernel panic. The machine boots fine without the card, inserting the card after logging on produces the expected results: I am able to view hotspots in my area. However I am unable to connect to any of them. Any combination of the above mentioned blacklist changes or modprobe commands do not yield any different results.

After much poking and proding I discovered that I am able to connect to my 64 bit wep accesspoint using a combination of iwconfig to set essid (without the extra character) and the key, followed by a dhclient command on the adapter (eth0 in my case). It works, and its a crappy hack that I should not have to even worry about. But the wireless cart CANNOT be in the machine when it boots. Maybe I can track down the reason for the kernel panic next and hack a way around that as well.

I am a bit disappointed to see this tank of a wireless adapter having problems where I know it should not.  I understand that cutting edge hardware dosent always have the best support on linux platforms... but to have the problem on the other end of the scale... I suppose we cant win them all.

---

### Post by fwheeler_1 on 2007-05-11
Hi-  Yup, there are plenty of problems with wireless when using Feisty.  But, one thing you should know is that Linksys changes chipsets between versions all the time.  So, v. 3 (your card) may not have the same chipset as v. 4, which is the version that this fix is for.  If v. 3 is a different chipset, you'll probably need other things to make your card work.  Good luck, Fw

---

### Post by eu_susan on 2007-05-17
Hello, 
I've done what fwheeler_1 posted and now the wireless connection is appearing at the network connections. But, the internet isn't connecting... I've already set it up, put the ESSID, DHCP, etc. but it doesn't work. 
What must I do?

Thanks!

---

### Post by fwheeler_1 on 2007-05-18
Hi eu_susan-  Would you be able to boot from the Live CD, un-blacklist the driver (post #5 in this thread), and manually configure the card (post #6in this thread)?  If this works, it might be best to use this approach, rather than using network-manager.  -Fw

---

### Post by fwheeler_1 on 2007-05-18
> **eu_susan said:**
> Hello, 
I've done what fwheeler_1 posted and now the wireless connection is appearing at the network connections. But, the internet isn't connecting... I've already set it up, put the ESSID, DHCP, etc. but it doesn't work. 
What must I do?

Thanks!


Hi eu-susan-  If you want to stick with network-manager, here is another thing to try.  I sounds like you can see the access point, but not connect.  In this case, please try the procedure outlined in my original post to connect to the access point by adding an extra bogus character to your essid using the "Connect to Other Wireless Network option found in network-manager:

> Plug in the WPC11, and Network manager will spring to life. In my case, it automatically finds my access point (ducky), but will not associate because it drops the last character of the access point name. To fix this, right click on the Network Manager icon in the upper tool bar (unless you changed this), select "Connect to Other Wireless Network" and in the dialog box for access point type in your name, with an extra character at the end (in my case, duckyx). I suggest that no encryption be used until you get all of this worked out.

If the above procedure works for you, you may need to do it each time you want to associate with your access point.  Good luck!

--Fw

---

### Post by wavz on 2007-05-19
Adding the bogus character to the network manager worked, but after adding the extra character try and connect to the new connection then go back to the original essid and connect to that and it should work. I actually went back to 6.10 untill they fix the bug with fiesty because even with this work around my network connection would drop out for no reason every 10 to 20 seconds for reasons I dont understand. So back to the tried and true till fixes are on the way! :guitar:

                                                                                                               Wavz

---

### Post by eu_susan on 2007-05-19
Thanks fwheeler_1 and wavz!

I just followed the steps posted at #5 and #6 and now it is all working fine.
I've also tried to come back to the original ESSID and it worked too.

Thanks again!
:)
Susan

---

### Post by sundial on 2007-06-07
I had the same problem and tried this.  THe WPC 11 v4 worked for a while and I was able to update my new install of Ubuntu.  After a while the second light on the card failed to come on and no matter what I did trying to reconfigure the card using the Network software with Ubuntu, the light stayed off and i had no connection to my access point.  I had to reverse all of the changes I made and now have no internet connectivity with my laptop system.

Any suggestion as to getting the Laptop and WPC 11 V4 to connect with a network access point?

Sundial:(

---

### Post by fwheeler_1 on 2007-06-08
Hi Sundial-  To use Network Manager, please try the steps listed in post #9 of this thread.  An alternative option is to configure the card manually, following the steps in posts #5 & 6.  Both of these suggestions use the native driver for Linux.  If these don't work for you, please search the forum for "ndiswrapper linksys wpc11 v. 4"--there are a couple of threads that describe how to use a Windows driver for the card plus ndiswrapper (a program that allows Windows network drivers to be used on Linux) that several folks have had success with (sorry, don't have the thread links handy).

Good luck, FW

---

### Post by sundial on 2007-06-11
> **fwheeler_1 said:**
> Hi Sundial-  To use Network Manager, please try the steps listed in post #9 of this thread.  An alternative option is to configure the card manually, following the steps in posts #5 & 6.  Both of these suggestions use the native driver for Linux.  If these don't work for you, please search the forum for "ndiswrapper linksys wpc11 v. 4"--there are a couple of threads that describe how to use a Windows driver for the card plus ndiswrapper (a program that allows Windows network drivers to be used on Linux) that several folks have had success with (sorry, don't have the thread links handy).

Good luck, FW

My thanks to all who tried to help out on this wifi card problem.  The latest is I bought a Dlink G650 as recommended by several people. and it too will not work on my setup.  It looks like there is no "Out of the box" solution in Linux.  I want to go back and try to set up the ndiswrapper using my linksys wpc11 v. 4 card, but i fear the instructions I have read to date are just so much gibberish.  I am new to Linux though I have been using PCs and computers for decades.  I just do not have the background to deal with the terminology that I find in most of the directions found on this Forum.  Telling me to compile the xxx is just terminology that is not related to any action I can take.  How do you compile something?  Is there a program I am to use to do that?

I would hope someone can point me to a set of directions written for ground zero beginners.

Again, my thanks to all.

---

### Post by bearius on 2007-06-13
I wanted to say big thanks to this amazing community. I am a complete newbie to Ubuntu and linux in general. I was also having a problem with my Linksys WPC 11 Ver. 4 but after a few searches on the net and in these threads I followed the very thorough and easy to follow instructions in post #9 in this thread and I am now fully connected and posting from my new Ubuntu lappy. It is amazing what power dedicated people wield in this world. Too bad not every community acts that way. Peace to all and many many thanks - Bearius :D

---

### Post by CheeseEatingBulldog on 2007-06-13
Just to thank you all for this thread, I was shocked to find my otherwise always detected card not found when I booted Feisty. But that blacklist edit and and added extra character to the essid in the /etc/network/interfaces file did away with all my problems, thank you!

---

### Post by fwheeler_1 on 2007-06-18
Thanks to all for feedback on the procedures outlined in this thread for the WPC11 v.4--I'm glad most of you got your card working!

@sundial:  With regards to a step-by-step guide for ndiswrapper, please see the following link:

[https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#wireless-ndiswrapper](https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#wireless-ndiswrapper)

Hopefully, this is the type of thing you had in mind, and it will get you going with the card.

Good luck, FW

---

### Post by chetter72 on 2007-06-30
hey all
 the adding the last letter to the ssid worked for me thanks to all who helped especially Kevdog

---

### Post by 416hammy on 2007-08-21
> **chetter72 said:**
> hey all
 the adding the last letter to the ssid worked for me thanks to all who helped especially Kevdog

I managed to unblacklist the driver and use the additional ssid character hack with success, but now every time my laptop comes back from **suspend** mode, wlan0 is disconnected and I need to change the dummy character in the ssid manually to a new character to get reconnected.

This is a pain, since I need to use suspend mode frequently.  Does anyone have a simple way to automate the ssid name change to reset the wlan0 connection? :confused:

---

### Post by sunsetgun78 on 2007-10-10
I have an IBM Thinkpad T21 with Feisty Fawn.  I also have a Linksys WPC11 v.4 wireless card that I can't get working in it.  I have tried lots of stuff but am still doing something wrong.  I blacklisted the two drivers, attempted to you used ndiswrapper and the graphical interface for windows drivers -- tried the drivers that came with it and the ones for the Realtek chipset.  At one point I saw networks listed and my own network has WEP.  The icon made it look like the computer was connected, but the wireless card had no blinking lights - only one steady one.  

I was advised I should have found a WPC11 v3 but I jumped on the first Linksys card I saw.  Can anyone suggest anything else for me to do.  I am new at Linux - started with OpenSuSE and switched to Ubuntu.

Thanks! :)

---

### Post by kevdog on 2007-10-10
There are two solutions to this problem

#1 - Attempt to use the native r818x or r8187 driver

#2 - Use ndiswrapper along with win98 driver for the rtl chipset.  

If you can explain in better detail what you want to do, I can help you.  In doing so can you post
lshw -C usb
cat /etc/modprobe.d/blacklist
modinfo ndiswrapper
ndiswrapper -v

Again, either of the two solutions should work, however option #2 might be the safest, but it is by far the harder to set up.

---

### Post by 416hammy on 2007-10-22
UPDATE:

I finally gave up on the WPC11 after I installed Ubuntu 7.10 and still could not get wifi working 100%.

I spent $40 on a [**_[COLOR="Blue"]D-Link WNA-1330[/COLOR]_**]("http://www.dlink.com/products/?pid=476") card, and it did everything straight out of the box!  WPA worked first-try! =D>

If anyone else is sick of their Linksys-Ubuntu infighting, dump the Linksys and go get this D-Link card. :)

---

