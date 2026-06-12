---
title: "[wireless] so close, but I'm stuck"
date: 2005-06-21
forum: Networking &amp; Wireless
---

### Post by DFreeze on 2005-06-21
Hi

so many questions about wireless, so many valuable answers, and still I can't apply it to my situation. This is where I'm at:

I have two NICs, one basic 10Mbit 3com (using it to type this) and a D-Link G520+ wireless device. My router is a D-Link G604t. If I'd known only a little earlier that this friggin' ACX111 chip is nasty with linux I wouldn't have bought it.

Wireless was activated natively, and it could sense the presence of my AP. But I couldn't get it to connect with the internet and I want WPA, so I installed NDISwrapper. I put GTKWifi in my panel as well and now I'm back where I was before. The wireless card is working (iwconfig shows it fine), GTKWifi 'sees' my AP, but no luck with internet. I set my DNS setting just as with the 3com (only set it to DHCP instead of staticIP).

NDISwrapper is working, has been 'modprobed', I've tried to deactivate the 3com card, but the only difference is that the message from Firefox changes from 'looking up ...' to 'connecting to ...'. Either way it times out without the webpage shown...

What do I have to do to get it working?

Should I physically disconnect the 3com, or are there some more tools to output useful information so I can trace the hiccup?

Any help would be appreciated.

---

### Post by aamir on 2005-06-21
I've heard of problems with attempting to run wireless connection and wired ethernet, I don't think you can have both enabled at once

---

### Post by DFreeze on 2005-06-22
GTKwifi can't get it to work with DHCP, even when I disable eth0. It finds the Wireless network, tries to connect to it, but fails.

It looks like a problem with my ap, but for testing sake I've made it as open as possible. It should work with DHCP (my XP laptop with an ACX111 adapter works flawlessly), but it doesn't. 

Can it be a permissions thing in my linux box?

---

### Post by aamir on 2005-06-22
try installing wifi-radar I know that works with dhcp and see if it picks up a connection....

you can also try running wavemon to see what the wireless signal looks like

---

### Post by PJB on 2005-06-22
[QUOTE=DFreeze]GTKwifi can't get it to work with DHCP, even when I disable eth0. It finds the Wireless network, tries to connect to it, but fails.

It looks like a problem with my ap, but for testing sake I've made it as open as possible. It should work with DHCP (my XP laptop with an ACX111 adapter works flawlessly), but it doesn't. 

Can it be a permissions thing in my linux box?[/QUOTE]
 You can also try a lan testing program like Look@Lan to see wat is going on.

---

### Post by DFreeze on 2005-06-23
I just had some progress, albeit not because of something I did. I fired it up after work and suddenly GTKWifi showed the name of my AP! So it had a connection of some kind...

I immediately launched Firefox, but I couldn't get google to show up (or any other website for that matter). 

So I don't really know what it means that I connected with the AP, I guess it's a good thing... But I can't figure out why it will not browse the internet, while, when switching to the wired card, browsing is instantly ok.

---

### Post by Lunde on 2005-06-23
[QUOTE=DFreeze]Hi

so many questions about wireless, so many valuable answers, and still I can't apply it to my situation. This is where I'm at:

I have two NICs, one basic 10Mbit 3com (using it to type this) and a D-Link G520+ wireless device. My router is a D-Link G604t. If I'd known only a little earlier that this friggin' ACX111 chip is nasty with linux I wouldn't have bought it.

Wireless was activated natively, and it could sense the presence of my AP. But I couldn't get it to connect with the internet and I want WPA, so I installed NDISwrapper. I put GTKWifi in my panel as well and now I'm back where I was before. The wireless card is working (iwconfig shows it fine), GTKWifi 'sees' my AP, but no luck with internet. I set my DNS setting just as with the 3com (only set it to DHCP instead of staticIP).

NDISwrapper is working, has been 'modprobed', I've tried to deactivate the 3com card, but the only difference is that the message from Firefox changes from 'looking up ...' to 'connecting to ...'. Either way it times out without the webpage shown...

What do I have to do to get it working?

Should I physically disconnect the 3com, or are there some more tools to output useful information so I can trace the hiccup?

Any help would be appreciated.[/QUOTE]

I've did this 4-5 times and there is "no problems" (Well some errors in syslog, but works fine). There's a complete guide here:

[http://www.houseofcraig.net/acx100_howto.php](http://www.houseofcraig.net/acx100_howto.php)

Note: don't choose the driver in this howto, but go get the latest driver at:

[http://rhlx01.fht-esslingen.de/~andi/acx100/](http://rhlx01.fht-esslingen.de/~andi/acx100/)

Hope this helps

---

### Post by DFreeze on 2005-06-23
Yes, thanx for the info! I've read about the ACX100 driver (which also works for the ACX111) and have the HouseOfCraig manual on my PC. But my AP supports WPA, which I want to implement when I have the wireless going, and that's still not possible with this driver. That's why I chose the NDISwrapper direction.

Any tips on finding the reason why communication with the internet will not work, even while connected to the AP?

---

### Post by DFreeze on 2005-06-27
"Houston, we have a liftoff"

I'm typing this while connected through my wireless NIC. Off course you all want to hear my success story and learn from it, but I'm afraid there's not much to learn...
 
I followed a [link](http://http://www.ubuntuforums.org/showthread.php?t=30671&highlight=wirelesstrouble)  of a person in wirelesstrouble, and found some useful tips. 

One I did right away was delete my wireless-tools and apt-get them again. That gave me the ubuntu-version of the tools. But that also deleted my GTKWifi, so I desparately tried to reinstall that. So far, no luck, but in the process I suddenly realized I was actually connected through my wireless! I pulled the wire out of the other NIC to see if I was not mistaken, but here I am...

It's still a bit feeble, though. It seems I get disconnected after a while (about half an hour) and only rebooting gets the wireless going again. But it's a start.

Thanks for all the answers on this and the hundreds of other threads! 

There were some other useful hints for further configuration of the network. For example, to disable all network configuration during boot, making it much faster at startup. Then write a small script to connect manually, after login. But I'll do that some other time.

---

### Post by DFreeze on 2005-07-02
I'd hoped this thread would slide to the back of the forum as one of the 'solved issues'. Alas, things just don't always go as hoped...

I'm back on my wired NIC, with no clue of what other command to try. I've typed all commands known to me so many times that they're programmed in my muscle memory by now... :) 

Trouble started when I tried to remove all settings from the graphical configuration applet in GNOME and make my own script. I was at the same time trying to get SWAT going, so maybe I messed up the system by changing configurations in all different files...

One thing that I found odd is the output of my ifconfig by now. The wired NIC has a 'normal' IP, but the wlan0 shows some IPv6. I've read a lot about disabling that, but I don't know how to.

```
goswin@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:DA:73:0A:24
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:daff:fe73:a24/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:49 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6502 (6.3 KiB)  TX bytes:1062 (1.0 KiB)
          Interrupt:19 Base address:0xdc00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:953 errors:0 dropped:0 overruns:0 frame:0
          TX packets:953 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:73908 (72.1 KiB)  TX bytes:73908 (72.1 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:11:95:13:CF:A4
          inet6 addr: fe80::211:95ff:fe13:cfa4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:45 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6300 (6.1 KiB)  TX bytes:6006 (5.8 KiB)
          Interrupt:18
```

This is when it's connecting at all... Above output I got when changing the order of priority in /etc/network/interfaces. Both NICs got an IP but none of them connected to the internet anymore. When putting eth0 back to front in .../interfaces I could surf again, but wlan0 doesn't even want to connect anymore. It can't get an IP from the AP whereas the eth0 card gets one instantly...

NDISwrapper sais the driver is loaded and the hardware is present.

Could it be that hotplug reinserted the ACX100 driver? I mean, I removed all settings in the graphical app, so maybe hotplug found some unconfigured hardware and put it back to default settings...

Sidenote: I don't know if it has anything to do with the above, but occasionally my mouse starts stuttering. It gets almost irresponsive, sometimes giving me a second of motion. After some time it stops again, but it' s @$% annoying!

Allthough I learn a lot from linux by following CLI walkthroughs, I guess I misconfigured my system here and there by now. I guess I'm one of the people eagerly awaiting more graphical configuration tools (at least ones that work consistently, which can't be said from the graphical network app in GNOME...)

Any help appreciated!

---

### Post by skipper on 2005-07-02
[QUOTE=DFreeze]

Could it be that hotplug reinserted the ACX100 driver? I mean, I removed all settings in the graphical app, so maybe hotplug found some unconfigured hardware and put it back to default settings...

[/QUOTE]

Best way to find out is to fire up a shell and type:

lsmod | grep acx

If the acx driver is still loaded you will soon know.

Not sure how ubuntu manages modules, but debian used to have a nice app called modconf. If you have this, use it to remove the acx-pci module. If not, you probably need to delete it (or rename it) from /lib/modules/<kernel version>/kernel/drivers/net/wireless/acx/

Good luck!

---

### Post by DFreeze on 2005-07-02
You were right, it did show up in my modlist!

$ lsmod|grep acx gave me:
acx_pci               153312  0

How can I manually remove the modules? I've removed the directories before, but is that the appropriate way (rm ../acx)?

Does the system automatically use NDISwrapper with wlan0, when acx is removed?

I just did the iwconfig essid / mode managed / channel 6 (yes 6) / ap 00:0..... yadayada once more and iwconfig accepts the commands. But when feeding the ap MAC address it just doesn't show up when doing iwconfig afterwards. It's still 00:00:00...

---

### Post by skipper on 2005-07-02
Assuming you are not logged on as root (the sudo simply gives you temporary root permissions):

sudo rmmod acx_pci

will get rid of it temporarily. As suggested in my previous email, suggest you rename or remove the actual module (I think it's called acx_pci.ko) in the directory I posted previously, then run:

sudo depmod -a

then reboot.

Oh, the other thing to check is that the ndiswrapper module is being loaded on boot. You may need to add this to /etc/modules if it is not loading on boot (which you can verify using the lsmod command).

Make sense?

---

### Post by skipper on 2005-07-02
[QUOTE=DFreeze]
How can I manually remove the modules? I've removed the directories before, but is that the appropriate way (rm ../acx)?

Does the system automatically use NDISwrapper with wlan0, when acx is removed?
[/QUOTE]

Oops...I should have read your post. Not sure if it is the appropriate way with ubuntu, which is why I suggested renaming it, however it works :-). Don't remove/rename the entire directory, just the module. Debian had a nice utility called "modconf" (which is available in universal) which allowed you to add and remove modules in a much more controlled way.

With regard to automatic loading of ndiswrapper, ndiswrapper -m adds an entry to the /etc/modprobe.d/ directory, however this did not seem to work for me, and I had to manually add an entry to the end of /etc/modules (strange).

Have a look at my HOWTO which was posted earlier today for more details.

---

### Post by DFreeze on 2005-07-02
I've done as you said, rmmod acx, renamed the .ko file and added the ndiswrapper line to the /modules file. 
[FONT=Courier New]lsmod | grep acx[/FONT] didn't show anything anymore and [FONT=Courier New]lsmod | grep ndiswrapper [/FONT] gave my ndiswrapper module.

Had a peek at your HOWTO as well. Good thing that you got it going. I never thought it would be such a pain for so many people to get wireless up and running.
Ah well, if so many people experience this, the development of better tools and drivers is even more stimulated...

Rebooting gave listed my AP again in GTKWifi (1.07), which didn't work anymore before. Moreover iwlist scanning gave me my AP as well! However, my connection to the internet is lost now... The wired NIC also doesn't get google anymore, although it has received an IP from the router. 

[FONT=Courier New]ifdown eth0[/FONT] and [FONT=Courier New]dhclient wlan0 [/FONT] list some attempts and ends with the line:
[FONT=Courier New]No DHCPOFFERS received.
No working leases in persistent database - sleeping .[/FONT]

[FONT=Courier New]ifup eth0[/FONT] again and it gets an IP immediately...

I'm typing this with my laptop, which also has an ACX111 wlan chipset, but has XP on it. The laptop can connect to my AP all the time, so it's not a setting in the AP that doesn't make it connect, I guess...

Any hints where to go from here? 

The most frustrating part of it is that it worked a couple of days ago! How's that for annoyance!

---

### Post by skipper on 2005-07-03
My guess is that your router may have run out of DHCP addresses to lease (assuming it is providing DHCP services). You might have to increase the range of addresses it makes available. First thing is first though, remove as many variables as possible by setting up your wlan with a static address (one that is within your subnet, but not used by anything else on the LAN), and make sure you can ping your router.

---

### Post by DFreeze on 2005-07-03
I have enough DHCP leases left, for sure. One thing though: I know about pinging, but I can't get it done from my linux box. It sais something like: 'sendmessage not permitted'. 

But another thing: yesterday nothing worked, today (nothing changed, I just fired it back up once more) I was on the net with the wireless for a minute or two. Then it stopped again, and then eth0 didn't get on the internet anymore. So apparently I'm not in control of the behaviour of my system.

Can it be something is messed up in GNOME? Because almost every time I use the linux box, my desktop gets irresponsive after some time (mostly about 20 minutes). I can't access menus of click on desktop items anymore. Can there be a connection between both problems? How could I restore possible damage?

---

