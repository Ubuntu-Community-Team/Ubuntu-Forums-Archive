---
title: "[SOLVED] Ubuntu Feisty Linksys WUSB54G v4 connection issue"
date: 2007-07-01
forum: Networking &amp; Wireless
---

### Post by JawsThemeSwimming428 on 2007-07-01
Hi...here's the story. I have been using Dapper Drake since it came out. We run a wireless network at my house, Linksys Wireless-G router with 3 PC's. When I installed Dapper after it came out I had some issues using my network card. Needless to say after about a month of posting on here I finally got it working with the help of some knowledgeable individuals. 
 The other day I tried to install openSuse 10.2 to dual boot because I wanted to see the difference. Well I installed it and I didn't realize that it was overwriting my existing Dapper installation. Well, Dapper is gone. So I finished installing Suse and wasn't very impressed (and was pretty mad it destroyed Ubuntu), so I decided to reinstall ubuntu. I installed Dapper off of an install CD I had mailed to me when it came out but I was having another issue with the wireless. So I figured it would be easier to install Feisty because it has better wireless support. 
  I downloaded the ISO and burned it to a DVD. Feisty installed very quickly and everything was pretty good, except my screen is slightly to the left (for example the shutdown button in the top right corner is only half visible because the screen is slightly off), that's another issue though. Then I plugged in my WUSB54Gv2 card only to find out it is the one version not supported in Feisty. Luckily, one of the other PC's had a v4 card so I just switched them.
  Ok now to the current problem, I now have a WUSB54Gv4 Linksys wireless adapter card. I plug the card in and the first time it said it was "Attempting to join wireless network {ssid}". It wasn't able to join. So I went into System -> Administration -> Networking and changed the settings to have my essid, dhcp, and it is set to Roaming enabled (not sure if that is right). Now, the network connection icon in the top says that it is connected to my wireless network. However, I cannot access the Internet through firefox and I cannot ping that machine. I am not quite sure why it says I am connected to my network because it isn't! I am not quite sure what to do, or what I did wrong. Anyone that can help me out I would be very grateful! Thanks in advance.

---

### Post by JawsThemeSwimming428 on 2007-07-14
I am still having the same issue with the wireless. I am not all that familiar with Linux networking and what needs to be done so if someone can even just give me some basic things to do that might be all it is!! I really appreciate any help.

---

### Post by JawsThemeSwimming428 on 2007-07-14
I just noticed something, I don't know if this might help, but up in the top right corner of the screen next to the Shut Down icon when I put my mouse over the wireless icon it says "Wireless network connection to 'linksys' (86%)". However, I cannot get online. Also, when I right click the wireless icon and go to Connection Information, everything is 0 except the MAC address (obviously). At the top of this screen it says that I am using Wireless Ethernet (rausb0) and that the driver is rt2570. Thanks in advance!

---

### Post by Rebeca on 2007-07-15
> it is set to Roaming enabled (not sure if that is right)

Uncheck that, click on OK, and then see if it works.

The native support should work, but if it doesn't, you can also try this: [http://ubuntuforums.org/showthread.php?t=478558](http://ubuntuforums.org/showthread.php?t=478558)

---

### Post by JawsThemeSwimming428 on 2007-07-15
I follow the directions until the point below and I get the following error message...is it saying ndiswrapper is too old or the wireless driver?

h@h-desktop:~/Desktop/WUSB54Gv4_20051110/Drivers/WUSB54Gv4$ ndiswrapper -v 
module version is too old! 
utils version: '1.9', utils version needed by module: '0' 
module details: 
filename:       /lib/modules/2.6.20-15-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko 
version:        1.38 
vermagic:       2.6.20-15-generic SMP mod_unload 586  
You may need to upgrade driver and/or utils to latest versions available at 
[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net) 
h@h-desktop:~/Desktop/WUSB54Gv4_20051110/Drivers/WUSB54Gv4$ 


I'm considering reinstalling Dapper Drake. The Feisty install I did requires a lot of reboots because things hang, the screen is off center (the screen seems to be moved slightly to the left because I can barely view the trash icon in the bottom right corner and I can barely see the Shutdown Icon in the top right). I tried enabling the restricted NVIDIA driver but I click ok to enable and nothing happens. Also, a lot of the time when I click on Network in System-> Administration it doesn't do anything. I have to reboot for the function to work. Is this just my install or are these common problems with Feisty? I think Dapper was easier to set up and more stable. Any help would be much appreciated! Thanks.

---

### Post by kevdog on 2007-07-15
Can you post 
lshw -C network

Thanks

Dapper isnt more stable than feisty.  You are having a driver problem no doubt!

---

### Post by JawsThemeSwimming428 on 2007-07-15
I hope your right! After I posted I had to run out for about 25 minutes during which I left Feisty running. I just came back now and I am on my other PC (I have two PC's KVM'd, one running Feisty and the other running Windows XP), the Windows one, I tried to go on my Feisty PC to run the command you said and I clicked on Applications-> Accessories-> Terminal and it seemed like it started to load it ( the starting Terminal box came up on the bar at the bottom) and then it just went away and never loaded anything. So I was going to reboot and I went up to the Shutdown Icon and clicked it to bring up the Shutdown menu and that didn't do anything either. I did have control of the mouse but no button/function would work. Don't know if that has anything to do with this but why did that happen?

 Anyway, heres the output of the command after I hard rebooted:

h@h-desktop:~$ sudo lshw -C network 
Password: 
  *-network               
       description: Ethernet interface 
       product: RTL-8139/8139C/8139C+ 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 2 
       bus info: pci@02:02.0 
       logical name: eth0 
       version: 10 
       serial: 00:16:76:46:92:a2 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s 
       resources: ioport:de00-deff iomemory:fddff000-fddff0ff irq:20 
h@h-desktop:~$ 

Thanks for the help!

---

### Post by JawsThemeSwimming428 on 2007-07-16
I'm still trying to get online! I am not quite sure what else to do. If anyone can get back to me I would greatly appreciate it!

---

### Post by Rebeca on 2007-07-16
Did you do the first steps as indicated in the thread I linked you to? Because it looks as if you are using an older version of ndiswrapper (1.38, which is the current version in the repositories). You have to download the latest version from their website: [http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)

You can download it to your windows PC and then transfer it to your linux PC.

Then, in your linux PC:

cd to the directory the ndiswrapper-1.47.tar.gz file is in, for example:

```
cd /home/h
```

And, then:

```

tar -zxvf ndiswrapper-1.47.tar.gz
cd ndiswrapper-1.47
make distclean
make
sudo make install
```


> I have to reboot for the function to work. Is this just my install or are these common problems with Feisty? I think Dapper was easier to set up and more stable.

I wouldn't suggest downgrading.

I've noticed Feisty does consume a bit more resources than Dapper since I use an older machine. How much memory does your PC have? If it doesn't have too much, you can try a memory upgrade or you can simply switch to a lighter window manager (like [icewm](http://www.icewm.org/) or [fluxbox](http://fluxbox.sourceforge.net/)) or you can try running [xubuntu](http://www.xubuntu.org/) instead.

---

### Post by JawsThemeSwimming428 on 2007-07-16
I'm at work right now, but I will try installing ndiswrapper-1.47 tonight. Also, the PC has  P4 3.0GHz processor with 1GB of RAM. Thanks and I will post tonight!

---

### Post by JawsThemeSwimming428 on 2007-07-16
Rebeca,

 I did what you said and I downloaded ndiswrapper-1.47. I ran make distclean (no errors), I ran make (no errors), and then I ran sudo make install (no errors). However, when I run ndiswrapper -v it gives me the same message it did last time:

module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
filename: /lib/modules/2.6.20-15-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version: 1.38
vermagic: 2.6.20-15-generic SMP mod_unload 586
You may need to upgrade driver and/or utils to latest versions available at
[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net) 

I did install version 1.47, at least that is what the file said it was (downloaded from SourceForge). The only thing I can think of is do I have to remove or uninstall ndiswrapper version 1.38 before I install 1.47? I thought it would just overwrite it. If I do have to remove the older version, how do I do that? I am not all too familiar with installing and uninstalling software in Ubuntu. Thanks!

---

### Post by JawsThemeSwimming428 on 2007-07-17
I tried installing ndiswrapper-1.47 one more time. However, I got the same error message as posted above. Anyone that can help me out I would greatly appreciate it!!!

---

### Post by Rebeca on 2007-07-20
Hm. It seems you do have ndiswrapper-utils. (To make sure, you can look for it in Synaptic.) Oh, you might need to install build essentials. To do that, you will need to get connected to the internet directly (if possible) and you have to type the following in the terminal:

```
sudo aptitude update
sudo aptitude install build-essential
```

Then, go through the previous steps and it should work.

If you want to try removing the older version first, you can do that through Synaptic (System > Administration > Synaptic Package Manager). In there, search for ndiswrapper and ndiswrapper-utils. Right-click on each to see what options you have.

Through Synaptic Package Manager, you can install and uninstall many programs.

If my poor advice doesn't work again, there's more information in the ndiswrapper website:

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/)

> the PC has P4 3.0GHz processor with 1GB of RAM

That's more than enough for Feisty considering I run it on an older, slower machine. I'm not sure why your computer could have stability issues with Feisty. You could try keeping a terminal window open, and then once things don't seem to respond, type 

```
dmesg
```

It might give you some useful information. (See [here](http://en.wikipedia.org/wiki/Dmesg) for an explanation of the command.) You can post what you get on the hardware forum and explain your issue in full.

---

### Post by JawsThemeSwimming428 on 2007-07-20
I can't get directly connected to the Internet, that is my issue. I have another PC running Windows XP I have been using to post on here. How can I do it without a direct connection to the Internet?

---

### Post by JawsThemeSwimming428 on 2007-07-22
Update:

 With the help of some people in the Forums I got my wireless card to work. Thanks!

---

