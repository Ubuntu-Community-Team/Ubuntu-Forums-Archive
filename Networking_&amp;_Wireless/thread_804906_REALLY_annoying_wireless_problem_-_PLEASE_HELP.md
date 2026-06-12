---
title: "REALLY annoying wireless problem - PLEASE HELP"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by DayleJames on 2008-05-23
Hey there all.
I have a really strange problem, and I'm really hoping someone can help because it's driving me ever so slightly insane.

I have a (work provided) HP Compaq 8710w laptop. I have just installed Ubuntu 8.04 onto it, and mostly it's working.

However, and would you believe it, the wireless network card isn't.

It has an Intel 4965 in there, which (based on everything I've read in these forums) should work out of the box. And sure enough Ubuntu recognises the device and shows it as in place (output of relevant commands at the bottom of this message).

However, I can't connect to wireless networks. I don't think the problem is necessarily with the device driver though.

On this laptop there are touch buttons across the top of they keyboard which do things like control volume and such. One of the buttons is the wireless device enable/disable switch.

In windows it works perfectly, but in Linux it's unresponsive. I can't enable my device and I think that's why it isn't working.

Look up the laptop to see the kind of buttons I mean, but I think they're software controlled. It's like the WLAN switch is constantly switched to off and I can't switch it on.

Someone somwhere must have come across this. I really hope someone has a suggestion because after a couple of days of fruitless searching I'm at my wits end.

Thanks in advance for any suggestions.
Dayle

-----

jamesda@jamesda-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jamesda@jamesda-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1b:38:c2:32:84
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=0.3-0 ip=172.24.214.106 latency=0 module=e1000 multicast=yes
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1d:e0:51:c6:47
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g
jamesda@jamesda-laptop:~$

---

### Post by mapes12 on 2008-05-23
I apologise in advance for stating the blindingly obvious BUT.....

**have you removed the ethernet cable?**

If not then take it out then at the terminal:

```
sudo /etc/init.d/networking restart
```

Does the wifi card strike up?

---

### Post by DayleJames on 2008-05-23
No please, state the obvious. I really hope I'm missing something obvious, because the alternative is that fixing it might take me the rest of my life. :)

I have just re-tested disconnecting my laptop from the network and restarting networking. Nothing changed.

Interesting to note that the networking restart command returns OK to me extremely quickly... as in, pretty much instantly.

Thanks for the suggestion though. I really appreciate it. I'm at the end of my wits.

HP site has no Linux support for it's notebooks whatsoever. AWESOME.

---

### Post by mapes12 on 2008-05-23
> *-network DISABLED
description: Wireless interface
product: PRO/Wireless 4965 AG or AGN Network Connection
vendor: Intel Corporation

As you have already discovered intel adapters are well supported in Ubuntu wifi land.

Now, how to get the thing going?

```
ifup wlan0
```

Any good?

---

### Post by DayleJames on 2008-05-23
Nah man. Just tried it.
I have been looking feverishly for some software which will control the enable wi-fi button on the top of the machine, but to no avail.

When I try to bring the device up I get...

jamesda@jamesda-laptop:~$ sudo ifup wlan0
[sudo] password for jamesda: 
Ignoring unknown interface wlan0=wlan0.
jamesda@jamesda-laptop:~$ 

That tell us anything ?

My assumption was that it couldn't bring it up, because the device wasn't physically enabled by way of the wireless button on the machine itself...?

---

### Post by mapes12 on 2008-05-23
> *-network DISABLED
description: Wireless interface
product: PRO/Wireless 4965 AG or AGN Network Connection
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:10:00.0
logical name: wmaster0
version: 61
serial: 00:1d:e0:51:c6:47
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g

> configuration: broadcast=yes driver=iwl4965 

From the above it appears that Ubuntu recognises the adapter and has a suitable driver for it. But why has it been disabled??

hhhmmm..........those keys you mention. Any luck on Googling others with the same machine running Linux?

---

### Post by DayleJames on 2008-05-23
Yeah... hilariously every post I find says that it worked no problem.

There is no none-standard configuration on my laptop. I am dual booting XP (which works perfectly) with Ubuntu, and this is the only issue.

The buttons are kinda like quick launch buttons, which you just lightly tap to change volume/start certain application etc.

One of them is the equivalent of a wlan switch on most laptops.

In windows when I tap it it goes blue, and wireless is enabled. Touch it again and it goes off. Simple stuff right ?

But when I boot into Linux pressing/touching that button doesn't do anything.

It's almost as if the wlan on/off button has been made into a software controlled touch pad, which is disabled if you don't have Windows.

I have found threads from people saying that they have gotten Linux working on this very laptop. Linlap says that its compatible, with no comments about this... [http://www.linlap.com/wiki/HP-Compaq+8710W](http://www.linlap.com/wiki/HP-Compaq+8710W)

How is this possible ? I'm not doing anything strange. It should just work.

I've been through the BIOS to see if there's anything else there to help, and I've searched Google high and low to some reference to the wi-fi button and linux. All with no result.

Man this is annoying. :)

---

### Post by mapes12 on 2008-05-23
> There is no none-standard configuration on my laptop. I am dual booting XP (which works perfectly) with Ubuntu, and this is the only issue.

Like you I've gone through the web links and yep, your machine should work with Ubuntu straight out the box.

The only thing I can point to is the dual boot configuration. You might think that different partitions are isolated. Yes, but the boot loader can leave legacy data that disables some configurations.

Suggestion: are you brave enough to wipe the drive and do a clean Ubuntu install?

To keep a secure copy of windoze I can recommend this imaging utility:

[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

It's free and much better than Ghost (IMO).

---

### Post by DayleJames on 2008-05-23
Not an option I'm afraid.

Work laptop, which has a windows image on it containing certain tools etc.

Hell, in Windows I'm not even allowed to change the screensaver the group policy is so tight.

It is a dual boot system, but I wouldn't have expected this to occur. If it was inherited some configuration from Windows I would have expected this to make it more likely to work, not fail.

Oh well, thanks so much for taking the time to talk to me.

I guess I'll keep looking.
SIGH

---

### Post by yogo on 2008-05-23
> **DayleJames said:**
> Not an option I'm afraid.

Work laptop, which has a windows image on it containing certain tools etc.

Hell, in Windows I'm not even allowed to change the screensaver the group policy is so tight.

It is a dual boot system, but I wouldn't have expected this to occur. If it was inherited some configuration from Windows I would have expected this to make it more likely to work, not fail.

Oh well, thanks so much for taking the time to talk to me.

I guess I'll keep looking.
SIGH

All I can really think is to find out what actually gets executed from within windows and then map that command to a keyboard shortcut in Ubuntu like alt + Shift or the windows logo key etc.

---

### Post by DayleJames on 2008-05-23
That's a good thought.

Any idea how that might be achieved ?

---

### Post by yogo on 2008-05-23
I would call HP tech support, they should have someone who would be able to look that up.

If you find what is issued, it will be simple to add a similar command for a keyboard shortcut.

---

### Post by DayleJames on 2008-05-23
Just for reference...

I just contacted HP support. They tell me that they don't support Linux. It falls outside their support boundries, and therefore they can't help me.

Sorry. Have a great day.

Not very helpful.

So I guess I'm stuck. Since I can't put Linux as the primary OS on this machine I'm going to have to bail on Ubuntu for now and think of something else.

Thanks for all your help guys.
Dayle

---

### Post by ubume2 on 2008-05-23
Do a 
```
sudo gedit /etc/network/interfaces
```

What does it show?

---

### Post by okdok on 2008-06-26
For starters, I am running the latest updated version of Hardy on an HP Compaq 8710w using the intel PRO 4965 and I typing this using the wireless network card.I have an NVIDIA Quadro FX 1600M card using the restricted drivers.

I was experiencing the same problem. I performed a clean install, and the wireless networking LED would not light. Wireless networking appeared to be disabled.

After opening up the computer log and pressing the 'wireless button' (I say this when it is not really a button, but a picture), I noticed that it did in fact work. The log responded. I then manually used the network manager to manually connect to an SSID and it worked pefectly from then on. (THE BLUE LED DOES NOT LIGHT)

I suggest the following approach:

1. Open computer log. 
2. Press the button firmly and verify that the log responds
3. Left click on the networking icon on the toolbar - top right
4. If you do not see 'Connect to other wireless network', Press firmly again.
5. You should see 'Connect to other wireless network'
6. Type in your SSID and encryption type in the wizard

This should initiate and enable the interface. You should not have to repeat this process if you do not touch the button. I have to note that now if I press the button it will turn off my interface and if I press it again, it will bring it back up. NEVER DOES THE LED COME ON. This can be confusing to notice.

I would love to know if there was a simpler command line rather than relying on the GUI :-?

Disclaimer: Since I got it to work, I was not able to replicate the problem and confirm my steps. I apologize for any errors/omissions.

Hope my experience helped!

---

### Post by Dr. Cox on 2008-07-25
> **okdok said:**
> 

1. Open computer log. 
2. Press the button firmly and verify that the log responds
3. Left click on the networking icon on the toolbar - top right
4. If you do not see 'Connect to other wireless network', Press firmly again.
5. You should see 'Connect to other wireless network'
6. Type in your SSID and encryption type in the wizard

This should initiate and enable the interface. You should not have to repeat this process if you do not touch the button. I have to note that now if I press the button it will turn off my interface and if I press it again, it will bring it back up. NEVER DOES THE LED COME ON. This can be confusing to notice.


yep, same here. have an hp notebook with those useless touch-button led all in one disasters as well.

ubuntu doesn't make the lights go on and off... however, the functions themselves are there......

i can also switch on and off my wifi, change volume, etc....

NEVER EVER though, any light changes.

i got my wireless to work with wicd which has an excellent page on sourceforge!
switch your wifi on and try the nm-applet. if that randomly disconencts and reconnects try wicd. worked for me. not very technical but worked.

cheers and good luck.

---

### Post by okdok on 2008-07-31
I can now get my HP 8710w intel wlan light to come on after installing the following package:

linux-backports-modules-hardy-generic

This was an effort to solve another error with the wireless connection failing after a prologued period. I found the solution listed at:

[http://ubuntuforums.org/showthread.php?p=4691359](http://ubuntuforums.org/showthread.php?p=4691359)

This fixed my error code which was pefect and resolved the wlan indicator light as well! :guitar:

Cheers!

---

