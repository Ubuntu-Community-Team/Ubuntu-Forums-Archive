---
title: "Wifi GUI broken after suspend -- Centrino Advanced-N 6205"
date: 2016-12-04
forum: Networking &amp; Wireless
---

### Post by jimmypants on 2016-12-04
Environment:

[LIST]
[*]wNIC = Centrino Advanced-N 6205 [Taylor Peak] 
[*]Driver = iwlwifi 
[*]OS = Ubuntu Studio (Xubuntu) 16.04.1, up to date (important & recommended, but not unsupported). 
[*]Housing = Lenovo ThinkPad T530 
[*]Me = Newbie.  (Doh!) 
[/LIST]

Goal:  Ability to easily switch wifi networks using the GUI.  I need to  be able to switch wifi networks frequently at work (contractor).

**Main Symptoms:**
[LIST]
[*]When I **wake the computer from suspend, wifi works** ...but... **the network GUI controls in the system tray are messed up.** 
[*]I am **not able to see a list of available wifi networks**, which makes it **impossible to switch to another wifi network**. 
[/LIST]

**GUI Symptoms** of the network controls in the system tray:[INDENT](*I would post a screenshot, but ImageMagick is not working - though looks like there are 2 of them - and I don't know how to use anything else.*)

[/INDENT]

[LIST]
[*]The wifi icon is not the normal "concentric arcs" thing, instead showing the thick up/down arrows. 
[*]"Wifi Networks" = grayed-out.
[LIST]
[*]No list of available wifi networks. 
[/LIST]
  
[*]"Connect to hidden wifi network..." = not grayed-out. 
[*]"Enable Networking" = checked, not grayed-out. 
[*]"Enable WiFi" = checked, not grayed-out." 
[*]"Connection Information" = not grayed-out.  ...and...  Upon clicking, shows my current connection information.  ...but...  Puts a number "1" after my SSID. 
[/LIST]

Also, some background info, in case it provides clues:
I thought that I had seen somewhere in my power settings that my computer is forced into a yet lower power state of Suspend (like a deeper sleep/suspend, not the regular sleep/suspend, not hibernate) after a certain amount of time spent in Suspend, which I had set to 3 hours...  ...But now I cannot find those settings.  Maybe this is something I am remembering from when I was test-driving Ubuntu Unity?  Using Ubuntu Studio (Xubuntu) now.  Anyway, I have absolutely no plans to ever hibernate and I have SSD drives, so I did not create a swap file when installing because it seemed unnecessary and/or bad for my SSDs.  I have 16 GB of RAM and plan to increase to 32 GB (maximum possible on this machine) within a couple months.

I ran the Wireless Info Script, but I am not able to inspect the text file because, "The document was not UTF-8 valid."  (Why can't I view this simple text file?  Is this yet another problem that I have to figure out??)  So anyway, attached is the archived version.

Also, borrowing from another post ([https://askubuntu.com/questions/796516/unity-wifi-gui-connects-ok-but-doesnt-display-any-other-networks](https://askubuntu.com/questions/796516/unity-wifi-gui-connects-ok-but-doesnt-display-any-other-networks)), I tried:
```
 iwlist wlp5s0 s | grep SSID
```
...and got:
```
 wlp5s0    Interface doesn't support scanning.
```
...and tried...
```
sudo lshw -class network
```
...and got... 
```
  *-network
       description: Wireless interface
       product: Centrino Advanced-N 6205 [Taylor Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 34
       serial: ****
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.4.0-51-lowlatency firmware=18.168.6.1 ip=**** latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:34 memory:f3000000-f3001fff
```

One person in that linked post said, "This is a bug that has yet to be fixed: "
[INDENT][https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/1569959](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/1569959)
[/INDENT]
.

---

### Post by jimmypants on 2016-12-04
********  Successful Workaround:   ********
** Restart the Network Manager service:**
```
sudo systemctl restart network-manager.service
```

Terminal code above is copied from that post I had linked from AskUbuntu.com.
This restart of the network manager made the GUI work correctly for me.

...***but***, as the poster who suggested this said, I expect the problem to occur every time I come back from suspend.
...and I expect that I will have to run this code every time.
So...

**Can anyone point me to where I can learn how to write a script that will run this code automatically every time I wake from suspend, possibly upon authentication?**
...or just post the script in this thread, if you know how to do it?
I have no idea how to do this or where to learn, but I thought I saw that somebody else was making scripts that do other fun things.

If we can create a script that works, then I might feel comfortable marking this thread as "solved".
...but I do not want to mark as such until I have a long-term solution, either 1) a script that runs automatically and successfully or 2) a software update rolls out that fixes the problem.

---

