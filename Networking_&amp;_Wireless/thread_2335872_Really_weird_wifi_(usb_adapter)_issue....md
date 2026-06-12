---
title: "Really weird wifi (usb adapter) issue..."
date: 2016-09-02
forum: Networking &amp; Wireless
---

### Post by Nixarter on 2016-09-02
OS: Ubuntu, Win 7, Kali, Mint  I've tried a LOT of troubleshooting techniques, but nothing has helped so far.  :(  

The basic problem:  My usb adapter ( Alfa AWUS051NH v2 ) constantly disconnects/reconnects.  In Windows, it does this for a few minutes before finally either connecting or failing/freezing.  It's an automated loop and I really can't do anything to stop it. *(see "Other Thoughts" below)  It usually connects (though it takes several minutes).  If it doesn't, I have to physically unplug the device and plug it back in (or restart).  In Ubuntu, I only get a message... and it promptly disappears.  This also happens in a loop.  The device appears and disappears and I cannot do anything.  Unfortunately, it usually does not connect.  In Kali and mint it's the same as Ubuntu.  No other USB devices have any issue at all.  Nothing else ever disconnects or gets into any kind of loop.  This includes other wifi adapters.  But They lack some features of the Alfas, so I have to get my alfa issues resolved.  


what I've tried:       

     **Drivers**  Downloading the Nix drivers on my win machine (when the adapter decides to work), and then copying it to a shared drive and installing from there.  No luck.  Win drivers are updated.  I've tried different variants (including generics) as well, but still no dice.      
     **USB cables**  I have tried different cables, and 2:1 cables (y cables? whatever they're called) to increase power, but it isn't a power issue.      [B]
USB Ports/versions[/B]  1.0, 2.0, 3.0.  Front, back, different MOBO connectors.  no effect.      
     **OSes**  little to no change.      
     **Interference**  I've unplugged all devices, and even tried booting from a USB drive to rule out SATA controllers.  I've even tried disabling all non-essential controllers, and even removed my video card to use the internal (i5 integrated) GPU.  My mobo even has PS/2 connectores... so I used those instead... STILL no dice.      
     **Power-Saving mode**  Disabled these options on the MOBO level and OS level.  I also changed some other low-level settings in my BIOS (UEFI).  no dice.      
     **Uninstalled other drivers**  I did this early on.  At any given time, the only networking device installed is some version of a driver for this wifi adapter.


What makes me confused is that no other devices/adapters have this issue... only the Alfa.  To make matters even more confusing... [i]only this particular computer[i] has these issues.  Other computers instantly see the device and connect, and never get into this loop.  So the adapter is perfectly fine... and so is my computer.  It even works with this computer, but there is just the weird looping issue.  So what gives :o  

Some solutions that I would rather avoid...      

**easy as Pi...**  Simply set up a spare raspberry Pi run with the adapter, and run a patch cable to my computer's LAN port.  It would basically be a convoluted hybrid null modem/wifi adapter.  It's complicated, and it may cause routing or latency issues in certain situations (gaming).      

**LAN**  The house is wired with cat6, but I would have to buy a big switch ($$).  Since the module isn't a problem with other computers, I could just have this computer on the LAN, and use the wifi adapter for other things.  But I don't want to do that. But those are really work-arounds rather than fixes.  


*Other thoughts.  In Windows, if I manage to right-click at just the right split-second, I can get a dialog box to pop up for the adapter.  Doing this inhibits the loop somehow and the device connects immediately.  Bogging down my computer heavily can sometimes have the same effect.  The only computer that has issues is my fastest gaming computer.  Is it possible that it is just a latency issue?  Perhaps the drivers wait a certain number of cycles (instead of time- or perhaps an issue with a crystal oscillator) for a response.  If it doesn't get one in time, it resets the connection... thus, our loop.  I don't know how any of that could be exploited, though.  Perhaps some kind of interrupt script?  Anybody have any other potential fixes?  Any input would be greatly appreciated.  I've been annoyed by this for quite some time, and I've run out of ideas.

edits: took a few tries to fix some odd formatting issues.  The content itself hasn't changed, minus some corrected typos.

---

### Post by coffeecat on 2016-09-02
*Thread moved to **Networking & Wireless**.*

If you need help troubleshooting this device in Ubuntu, please have a look at this thread and run the wireless script **in Ubuntu** as described there and post the wireless-info.txt output:

[https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

**Edit:** speaking for myself, if I had a device that misbehaved in Windows, Ubuntu, Mint and Kali, I'd throw it out and not waste further time with it. **endedit**

> **Nixarter said:**
> edit: after several attempts, a forum bug screws up the formatting every time.

Er, no. A cursory glance around the forum will show you that others are not having this problem. It's not a forum bug; the problem is at your end, possibly a browser extension. Make sure you are not blocking any scripts, particularly yahooapis.com. If that is unrewarding, see if one or other of your browser extensions is interfering.

---

