---
title: "Wireless problems"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by Trevor Johnston on 2009-11-09
So I just installed Ubuntu 9.10 (on a HDD partition) and everything seems to be working fine except my ability to use wireless. At all.
I click on the network manager and it only shows "wired connections", can I be helped?

---

### Post by cjohnston on 2009-11-09
I assume that if you right click on the network manager icon the 'enable wireless' button is checked?

---

### Post by Trevor Johnston on 2009-11-09
That option doesn't exist

---

### Post by Cuddles McKitten on 2009-11-09
Have you had your wireless working in Ubuntu previously or is this your first time trying to get it to work?

Type ```
lspci -v | less
``` into a console and give us the output on your wireless card.  It should look something like this: ```
02:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
        Subsystem: Intel Corporation Device 1201
        Flags: bus master, fast devsel, latency 0, IRQ 32
        Memory at f4100000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
        Kernel driver in use: iwlagn
        Kernel modules: iwlagn

```

---

### Post by Trevor Johnston on 2009-11-09
ya I got
```

Network Controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
Subsystem: Dell Device 000c
Flags: bus master, fast devsel, latency 0, IRQ 17
Memory at f1ffc000 (64-bit, non-prefetchable) [size=16k]
Capabilities: <access denied>
Kernel driver in use: b43-pci-bridge
Kernel modules: ssb

```

I'm having to go from XP to Ubuntu to get info then back to XP to give you guys the info  so it would be kind to get as many steps at one time as possible though of course I'm willing to do whatever it takes.

---

### Post by Cuddles McKitten on 2009-11-09
Broadcom cards tend to have difficulty with firmware needing to be installed, but I've only ever dealt with it on another distro a while ago.  Here are some links that might help:

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)
[http://ubuntuforums.org/showthread.php?t=871906&highlight=broadcom+wireless](http://ubuntuforums.org/showthread.php?t=871906&highlight=broadcom+wireless)
[http://ubuntuforums.org/showthread.php?t=1314852&highlight=broadcom+wireless](http://ubuntuforums.org/showthread.php?t=1314852&highlight=broadcom+wireless)


If you need to download the firmware manually, the firmware itself should be able to be copied to a disk to port to your Linux partition; b43-fwcutter can be found in the repos to install it.  If you can connect through a wired connection, I'd recommend using that.

---

### Post by Geocron on 2009-11-09
[COLOR=Red]TRY THIS BEFORE ANY OTHER METHOD [/COLOR]
i have a broadcom wifi card
i find that the wifi does not work with a fresh install EVEN if the card is RECOGNIZED 
to fix this this all i do is pug in a Ethernet cable (with internet on it) and up date
then go to the System>administration>Hardware drivers 
and activate the b43 driver (if you dont see b43 driver u probably don't have a broadcom)
then update again (by going to  System>administration>Update manager)
after that i can see wifi points and get on them 

[COLOR=Red]i recommend that you TRY THIS BEFORE ANY OTHER METHOD [/COLOR]

---

### Post by Trevor Johnston on 2009-11-09
Ok so I started doing stuff and my computer died (apparently a 9-cell battery means 6 minutes of battery life) and now I can't even start Ubuntu because this error comes up.
```

[   3.017444] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

```

.... I feel screwed in so many ways right now.

---

### Post by Trevor Johnston on 2009-11-09
So I did a complete reinstall of Ubuntu and am back to the beginning. I looked in my /lib/firmware and b43 is there as well as b43legacy but I'm still not getting a wireless anything. I did a complete update and activated the proprietary drivers.. im gonna use a screenshot to show you my network manager showing nothing that says connect to wireless, but first how do I work with screenshots in Ubuntu?

---

### Post by Trevor Johnston on 2009-11-10
So I did so research and now I'm pretty sure I have bad firmware installed. I got new files but how do I replace the old ones?

---

### Post by Trevor Johnston on 2009-11-10
please I would like help O.O pretty please ^.^ .  I know there are a ton of other forum posts out there with broadcom wireless problems but they all assume the wlan option is there but not connecting to anything. I don't have the wlan option at all, not even the two computer looking things in the top right corner.

---

### Post by Richardthe675th on 2009-11-15
I have similar props with my newly installed Ubuntu 9.10 on my new Lenovo netbook BUT I now have wirelees working! Being a complete noob I'm not sure what I did to make it work, and certainly Network Manager isnt working properly as, like you, I have no Network Manager icon under system-administration tab or anywhere else and no network manager driven graphics.

Navigate to system-preferences-startup applications and select Network Manager. Should be enabled (ticked). Press Edit. My command line says "nm-applet --sm-disable" (no quotation marks. note the space in the middle of the command. and the double dash). Restart for any changes to take effect.

You have got an internet connection via ethernet cable, right? Navigate to system-administration-synaptic package manager and search for network-manager (not quicksearch - click top right to expand the window to full size and click the magifying glass). You should see "network-manager" in the left window and a load of progs in the right. Check that the "network-manager" and "network-manager-gnome"progs in the righthand window are enabled. If not right click on them, select enable then click apply.

Still not working? remove and then reinstall "network-manager" and "network-manager-gnome" through synaptic manager.


navigate to system-administration-update manager and update your software.


Click on the tiny network icon on the top of your screen and see if it gives to a wireless dialog this time. It could see my network, and asked for the encription key.

Something in the above got my BT home network going. I had already searched for, found and enabled the broadcom driver.

Hope this works for you.

If anyone knows how to get NM working properly with icon under Administration, proper graphical interface etc I'd be grateful. 

best of luck - apart from this prob my new system is great, and I have learned something about Linux trying to fix it.

---

