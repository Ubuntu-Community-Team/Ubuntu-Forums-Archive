---
title: "[solved] Linksys WMP54G v4.0 PCI Adapter drops connection"
date: 2014-12-13
forum: Networking &amp; Wireless
---

### Post by tcll5850 on 2014-12-13
I've found a similar issue with what appears to be the same card I'm using:
[http://ubuntuforums.org/showthread.php?t=541182](http://ubuntuforums.org/showthread.php?t=541182)

I'm posting from the very computer that's doing this btw...
I've just recently had to restart because it just refused to connect though I was just online 2 minutes prior.

I'm not sure what's causing it to lockup and fail to resolve the network even though they show up.

if it's related to hibernation causing the lockup, then that might be the problem.
(I have had lockups on resume, which is fixed with a sleep then wake, but that wasn't the case here)
what's happened here was a resume from hibernation, a few google searches and forum posts while skyping, then a random lockup

I did do '$ nmcli mn' which retuned with a STATUS of Connecting/Disconnected

is there anything I can do to stop it from locking up like this??

---

### Post by tcll5850 on 2014-12-15
confirmed, sleep-mode restores the random lock
(as in, use it when wireless locks up)

it locked up again as I was writing a post on another forum.
(randomly disconnects and refuses to reconnect to the visible networks)

---

### Post by tcll5850 on 2014-12-16
just happened again and I lost my post because of it

---

### Post by tcll5850 on 2014-12-20
I'm now turning this thread into a log until I can figure out how to fix this
just to show off how often this occurs so others having the same problem can know if this is or isn't their issue.

I'm posting this message because it just happened again...

DOES ANYONE KNOW HOW TO FIX?? :(

---

### Post by tcll5850 on 2014-12-20
just lost my skype call because it happened again and DC'd me

---

### Post by tcll5850 on 2014-12-21
ok, you know what... screw the log...
I think 5 posts is enough to state just how frequently this happens... heh

so yea... it's literally 1 minute I'm online, the next minute, the adapter or something refuses to connect to the clearly existing network.
all of my other 7 devices have no problem and are still connected when linux refuses to connect...

why??
what??
and how??

somebody please answer this so I can finally fix this stupidly annoying bug >_<

EDIT:
forgot to mention:
disabling and re-enabling wifi has no effect at all
disabling and re-enabling network, it attempts to connect, but fails... (is it even trying, because the network is right there)

---

### Post by flaymond on 2014-12-21
The best way to fix this is ***clean reinstall*** your Ubuntu. It will fix most problem on your last session after you clean install.

---

### Post by tcll5850 on 2014-12-21
erg... that's the noob's way though... I'm more technical than that... just tell me what to do, and I can aim to fix this. :)

I'm a programmer, and have done alot of customization I don't feel like losing...
I can tell you I've installed and uninstalled a bunch of Desktop Environments before finally stopping on XFCE with Compton...

but yea ask me questions and tell me how to find the answers if needed
I can fix this.. I just need to know how, what to do, and where to look...

if you don't know, can you direct me to someone who does :/
I really want to avoid reinstalling as I don't want to delay the people waiting on my program...

this should be a simple fix if I can find it... :/

---

### Post by tcll5850 on 2014-12-25
ok, I think an update kinda fixed the lockup issue...
but now instead of having to sleep, all I have to do is disable and enable wifi before it'll connect again.

is there a script that can detect when it disconnects so it can automatically disable and enable wifi on disconnect??


this really gets in the way of Nitrous.io, which is an online development interface.
when it DCs, Nio comes up with a red bar that states I can't save my work...

this happens quite often btw, I can't leave my compy for about 5 minutes w/o a DC.
(and no, it's not the router as my computer is the only thing w/o net)

---

### Post by jeremy31 on 2014-12-25
> **tcll5850 said:**
> erg... that's the noob's way though... I'm more technical than that... just tell me what to do, and I can aim to fix this. :)

I'm a programmer, and have done alot of customization I don't feel like losing...
I can tell you I've installed and uninstalled a bunch of Desktop Environments before finally stopping on XFCE with Compton...

but yea ask me questions and tell me how to find the answers if needed
I can fix this.. I just need to know how, what to do, and where to look...

if you don't know, can you direct me to someone who does :/
I really want to avoid reinstalling as I don't want to delay the people waiting on my program...

this should be a simple fix if I can find it... :/

Most of us consider ndiswrapper to be a very bad solution, I call it a band-aid on a broken leg.  I am not a programmer but maybe you can redo ndiswrapper to be useful or reverse engineer the windows drivers to make it work

I have a WNA3100 usb that uses ndiswrapper as the only option and it is terrible but I only tried it to see if there were any options to make it better

---

### Post by tcll5850 on 2014-12-25
/confused

ok wait, you're saying my network connects just fine and then randomly disconnects and won't reconnect w/o user input because of a driver issue??
I was thinking it was more of a network-sided application issue (not sure what XFCE runs for networking) :P
bleh

yeh, I think I'd call my not working Panda Ra-link USB w/less N adapter a driver issue over this... heh
just sayin :P


so anyways, what can I do to fix exactly??
(I'm not sure if I'm using ndiswrapper or not, but something's definitely sucking and screaming hard) :P


if you guys need info to help me fix, tell me what to do to get the info and I'll help you out on your end :)
(I'm still a linix noob... heh)

---

### Post by jeremy31 on 2014-12-26
> **tcll5850 said:**
> /confused

ok wait, you're saying my network connects just fine and then randomly disconnects and won't reconnect w/o user input because of a driver issue??
I was thinking it was more of a network-sided application issue (not sure what XFCE runs for networking) :P
bleh

yeh, I think I'd call my not working Panda Ra-link USB w/less N adapter a driver issue over this... heh
just sayin :P


so anyways, what can I do to fix exactly??
(I'm not sure if I'm using ndiswrapper or not, but something's definitely sucking and screaming hard) :P


if you guys need info to help me fix, tell me what to do to get the info and I'll help you out on your end :)
(I'm still a linix noob... heh)

Look at the sticky post "Before posting in networking and wireless".  Run the command to download and run the wireless script and post the results, it will tell us what chipset, drivers and other wireless info needed and please [http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168) as some terminal output will appear as smilies otherwise

---

### Post by tcll5850 on 2014-12-26
ok, that kinda helped me out with getting info on my driver >.>

```

01:0a.0 Network controller [0280]: Ralink corp. RT2500 Wireless 802.11bg [1814:0201] (rev 01)
	Subsystem: Linksys WMP54G v4.0 PCI Adapter [1737:0032]
	Kernel driver in use: rt2500pci


```

and yea, I think I'll reword the title as that sticky thread had a better title than I could think up... heh
thanks for that! :)


EDIT:
or if not this, perhaps I'd have better luck trying to get my [Panda 300Mbps Wireless-N USB RT3572 Adapter w/ WPS button] working... heh
(that is the purpose of this crappy 802.11bg card after all) :P

the included drivers fail to build (Error 2)
oddly enough though, the adapter worked on my first upgrade to ubuntu 14.04
(the upgrade broke everything else, so I reinstalled zorin 6 before upgrading again due to support issues) bleh

---

### Post by tcll5850 on 2014-12-27
just had to sleep again as disabling wifi wouldn't reconnect...

why can't this work like it did before and NOT drop the connection
yea, it just randomly started dropping the connection, and I don't know why...

my NIO page is frozen now because of it, and I havn't saved my code...

EDIT:
trying a few fixes I found on an askubuntu page:

---

1:
```
gksu gedit /etc/pm/power.d/wireless
```
insert:```
#!/bin/sh

/sbin/iwconfig wlan0 power off
```
then run:```
sudo chmod +x /etc/pm/power.d/wireless
```

---

2: (for Meego, but worth a try)
```
cd /etc/
gksudo gedit rc.local
```
insert: ```
ifconfig wlan0 down
ifconfig wlan0 up
```


EDIT2: don't get me wrong, I'm not out-ruling ndiswrapper, and might just use it to get my panda working

---

### Post by jeremy31 on 2014-12-28
Have you tried Ubuntu 12.04 to see if it works correctly?
Are there error messages in dmesg about failure to flush queue?

---

### Post by tcll5850 on 2014-12-28
> Are there error messages in dmesg about failure to flush queue?

not sure where that's located... >.>

this power management thing seems to be working, though I'm expecting it to act up...

---

### Post by jeremy31 on 2014-12-28
> **tcll5850 said:**
> > Are there error messages in dmesg about failure to flush queue?

not sure where that's located... >.>

this power management thing seems to be working, though I'm expecting it to act up...

You can search dmesg using terminal with ```
dmesg | grep queue
```

---

### Post by tcll5850 on 2014-12-28
thanks :)

I think this answers your Q :P
```
tcll@tcll-AY589AAR-ABA-a4317c:~$ dmesg | grep queue
[   65.191267] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   68.227122] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   72.652738] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   72.812943] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   72.973151] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   85.328841] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   86.546389] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   98.808111] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  108.344984] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  132.367488] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  136.390649] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  140.385729] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  146.400355] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
tcll@tcll-AY589AAR-ABA-a4317c:~$ 

```

---

### Post by jeremy31 on 2014-12-28
> **tcll5850 said:**
> thanks :)

I think this answers your Q :P
```
tcll@tcll-AY589AAR-ABA-a4317c:~$ dmesg | grep queue
[   65.191267] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   68.227122] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   72.652738] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   72.812943] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   72.973151] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   85.328841] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   86.546389] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   98.808111] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  108.344984] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  132.367488] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  136.390649] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  140.385729] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  146.400355] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
tcll@tcll-AY589AAR-ABA-a4317c:~$ 

```

How long after a reboot did you run the command?

---

### Post by praseodym on 2014-12-28
Try Wicd instead of the network-manager:
```

wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon01441.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon01441.tar.gz
cd wicd-1.6.x_addon01441
sudo ./install_wicd_addon
sudo service network-manager stop
sudo killall wpa_supplicant
sudo service wicd restart
```
Choose wlan0 as interface name and wext as driver.

---

### Post by tcll5850 on 2014-12-28
I think I've already fallen in love  with Wicd! XD

if I can get my Panda USB N adapter working, I can get rid of this stupid B/G PCI card. :3
(it's taking up the port for my Turtle Beach surround sound card)
^ this MBd only has 1 PCI port

---

### Post by tcll5850 on 2014-12-30
gave it a good 2 days at least before reporting anything, and I have to say, it works perfectly! :)

I've removed network-manager so I'll never have to deal with that nightmare again. XD
and it's been a smooth ride ever since. :D

thanks for your help guys :)

good to know I now have a good network interface for once I get my panda going ;)
(can't wait to remove this linksys so I can have 3D audio again)

---

