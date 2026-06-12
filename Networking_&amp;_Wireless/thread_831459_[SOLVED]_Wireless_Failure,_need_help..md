---
title: "[SOLVED] Wireless Failure, need help."
date: 2008-06-16
forum: Networking &amp; Wireless
---

### Post by TheOnlyMerlin on 2008-06-16
I have a HP Pavilion zv6000 laptop, running Hardy Heron.

I am not able to see any wireless networks in Ubuntu.  I click on System >> Administration >> Hardware Drivers, and this is what I see.

(1)
[IMG]http://i282.photobucket.com/albums/kk259/TheOnlyMerlin/temp/HardwareDrivers.jpg[/IMG]

I click on the "enabled" check mark next to my wireless card (seems like an obvious solution), then I get this:

(2)
[IMG]http://i282.photobucket.com/albums/kk259/TheOnlyMerlin/temp/HardwareDrivers2.jpg[/IMG]

I click on "enable" then get this:

(3)
[IMG]http://i282.photobucket.com/albums/kk259/TheOnlyMerlin/temp/HardwareDrivers3.jpg[/IMG]

I then go to restart.  When I do, I am in the same situation, and the above screens will do the exact same thing.  help!

-TheOnlyMerlin

---

### Post by TheOnlyMerlin on 2008-06-17
Sorry, apparently where I had the pictures posted didn't work out well.  They should be visible now.

---

### Post by FuturePilot on 2008-06-17
Make sure you have all the repos enabled in System&#8594;Administration&#8594;Software Sources.

---

### Post by TheOnlyMerlin on 2008-06-17
Under software sources I have:
***"Ubuntu Software" Tab***
 "Downloadable from the internet" all check except for "source code" (main, universe, restricted, multiverse) 
And I have "Cdrom with Ubuntu 8.04 'Hardy Heron'" checked under "Installable from CD-ROM / DVD"
***Under "Third Party Software" Tab***
{Checked} **[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy** partner
{Unchecked} **[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy** partner (source Code)

***Under "Updates" Tab***
**Ubuntu Updates**
{Checked} Important Security Updates
{Checked} Recommended Updates
{Unchecked} Pre-released Updates
{Unchecked} Unsupported Updates

**Automatic Updates**
{Checked} Check for updates: Daily
{Only notify about available updates}

**Release Upgrade**
Show new distribution releases: Long term support releases only.

Tell me if you need anything form the Authentication or statistics tabs.

---

### Post by FuturePilot on 2008-06-17
Hmmm. Ok, all that looks fine. Maybe it's not what I thought.

---

### Post by TheOnlyMerlin on 2008-06-17
Any other ideas?

---

### Post by TheOnlyMerlin on 2008-06-17
Additionally, I have had this computer working wirelessly in Gutsy, but it doesn't work now in Hardy.

Also, I don't have access to the internet until I can get wireless working. My LAN connection is broken.  I cna probably get everything else I have working once I get internet.

---

### Post by rlzyoner on 2008-06-17
You could try manually using ndiswrapper to use the b43 wireless drivers.
Download ndiswrapper and from a terminal type
ndiswrapper -i /path/to/bcm/driver (This will be on your windows partition)

Now type ndiswrapper -l (Ensure the BCM is on the list)

Now type ndiswrapper -m (Load the driver)

To ensure this happens automatically from now on, 
type sudo gedit /etc/modules
and modify this file by typing
"ndiswrapper" - without the quotes and then save.

Reboot the machine and all should be ok.
Its been a while since I've had to do that so just check ndiswrapper's FAQ's etc for some guidance also

Hope this helps.

---

### Post by TheOnlyMerlin on 2008-06-17
Yay!  Problem resolved!  thanks!

---

