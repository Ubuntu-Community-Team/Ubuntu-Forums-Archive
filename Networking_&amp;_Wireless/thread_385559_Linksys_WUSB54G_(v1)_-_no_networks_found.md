---
title: "Linksys WUSB54G (v1) - no networks found"
date: 2007-03-15
forum: Networking &amp; Wireless
---

### Post by Natume on 2007-03-15
**Issue Resolved**

In spite of all of the posts on the forum (and the instructions provided on the ndiswrapper wiki), I'm having a fair deal of trouble getting my linksys usb wireless g to do anything useful.  At the moment, I'm at home (as opposed to college, where I usually am, and where I have direct access to the campus internet via an in-dorm ethernet connection), and trying to get my computer on the wireless network.  To the best of my knowledge, I have the version 1 wusb54g unit, seeing as it registers with an ID of 1915:2234 (without any descriptive information afterward, unlike the devices that follow it) on performing an 'lsusb'.

Likewise, ndiswrapper has been installed, and the drivers from the CD that came with the unit loaded on - successfully, I believe.  When the unit is plugged into the usb port, an 'ndiswrapper -l' registers that the wusb54g drivers are present, as is the hardware.  In the networking section, under administration, the wireless unit has been checked off, the ESSID set to the name of the home network, no password input, and the format set to hexadecimal.  The IP address stuff is set to automatic.

The only other information that I think might be useful is that the card registers (in both an 'ifconfig' and 'iwconfig') as eth1, whereas the main ethernet card (not plugged into an ethernet port, at the moment, nor has it been when I've tried to get the wireless working), registers as eth0 (and has for as long as I've used Edgy).

So, it seems that it detects the hardware, and the drivers have been installed, for the correct version, no less.  A 'modprobe ndiswrapper' registers no errors, and 'dmesg' confirms that ndiswrapper has been loaded.  When trying to scan for a network using 'sudo iwlist scan', no networks are found (or so it says, for that card; eth0 and lo can, of course, not scan for networks, and it tells me such).  I've tried it on all the channels, from 1 to 14 (where it currently is set) to no avail.  (Granted, I've forgotten over the evening the command to switch the channel.)  Likewise, installing and trying to use Wireless Assistant to scan for networks returns none.

At the moment, the power light is on, but the link light has not blinked any more than once after each plugging in.  I'm not entirely certain where to go from here to try to get the thing to work, but I figure that any advice would help.  It should be noted that come Sunday ( March 18 ), I'll be back at college, and on the wired connection, so I'll just try what I can until then, and if I can't get it up now, I'll have to try again come summer.

---

### Post by Natume on 2007-03-16
No need to bother with the help now.  I was being a little slow, and not thinking to do more research on islsm_usb, seeing as the wiki of cards that work mentions that.  After figuring out what to do, namely to blacklist islsm_usb, a reboot solved my issues.  The card is now listed as wlan0 instead of eth1, and it scans properly.  Wireless assistant connected me to my home network flawlessly.

**Current Issue**

On second thought, the internet seems to be failing spectacularly.  As somebody had mentioned in the stickied thread about installing a linksys usb adapter on Dapper, the computer will lock up within 10 minutes to an hour of use, even if the internet use is very, very light.  All three times it's done so have been different for me.  At first, it locked up while in ubuntu : the cursor wouldn't move, the screen was not updating, etc.  Had to do a manual shutdown for that.  The second time around, the link light on the linksys was on constantly (not blinking, even), and the computer fans were starting to stress, so I unplugged the linksys (after disabling it in Networking, not that it mattered) which caused the computer to lock up.  Third time around, same fan issues, so I decided just to shut it down ; went fine until the last bar of the ubuntu splash was unloaded, and then failed to turn off (it just hung up at the flash screen), which resulted in another manual shutdown.

...The second time around, my firefox and thunderbird accounts got screwed.  I luckily was able to recover my bookmarks and reinstate the settings for firefox... and it seems that my e-mails may still be saved somewhere in my thunderbird folders, but getting them back is going to take a bit of work.  No doubt, that was because I was in the middle of using both of them during the lockup.  Anyway, now the issue is getting the linksys to not lock up my computer while in use.  The person in the previously mentioned thread seemed to have found a solution, but I'm honestly not sure what it was.

---

### Post by cliff01 on 2007-03-17
OK, I' right where you were, right down to the 1915:2234 device ID. I, however, cannot get my wireless usb to come to life! I did the blacklist islsm_usb thingy, but no change. I've been trying to get this to work for about 2 weeks now and I'm feeling really STUPID! If you have any other "tricks" or suggestions please let me know. Congrats on getting yours to work.

---

