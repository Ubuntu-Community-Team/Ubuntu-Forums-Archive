---
title: "WUSB54G v1 Not Recognized by lsusb"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by Phoenix Rising on 2008-04-26
Hi all,

I have just installed 8.04 on a PC that has two wireless adapters.  One of them is a PCI card that shows up just fine using lshw, and the other is a Linksys WUSB54G v.1 USB peripheral.

In Windows, the USB peripheral works, the PCI card doesn't.

In Ubuntu, lshw shows the PCI card, but lsusb **does not** show the USB peripheral.

Without droning on and on about all the different tutorials and how to's I've followed over the last 12 hours, I'll just make this brief:  **how can I get Ubuntu to recognize that there's something plugged in?**

Again, Windows can recognize and use the hardware.  Ubuntu does not.

The lsusb command doesn't list anything to do with the device.  Here's some output:

Bus 005 Device 005:  ID 1058:0903 Western Digital Technologies, Inc.
Bus 005 Device 002:  ID 1915:2234
Bus 005 Device 001:  ID 0000:0000
Bus 004 Device 001:  ID 0000:0000
Bus 003 Device 001:  ID 0000:0000
Bus 002 Device 002:  ID 046d:0a01 Logitech, Inc. Logitech USB Headset
Bus 002 Device 001:  ID 0000:0000
Bus 001 Device 004:  ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 001 Device 001:  ID 0000:0000

(And please, no jokes about the lame keyboard/mouse setup - my Mac keyboard won't work on this thing for some reason :( )

I would expect at least one of those entries to read, "Linkssys" something or other, but it doesn't.  The second one if the list has an ID but no string associated with it thereafter, which leads me to think that could be my device, but I don't know for sure.

I've installed an INF driver using ndisgtk (installed the base packages first of course, from the Ubuntu 8.04 CD), and after it's installed, the notice reads something to the effect of "hardware not found".

If some of this doesn't make sense, forgive me - I've been working on this all night and now that it's 8:20AM, I'm going to bed.

Any input you could provide would be greatly appreciated.  Thank you.

---

### Post by Phoenix Rising on 2008-04-26
**RESOLVED**

Here's how I solved this problem for any Googlers who see this post.

First of all, I wasn't able to find anything explicitly for the first version of this device (i.e. the unmarked version), so I was skeptical that any of the guides would work.  Nevertheless I tried several different guides, all of which failed at some point.

At first I thought that Ubuntu wasn't seeing my Linksys wireless device; I was wrong, it saw the device fine, *it just didn't know what the hell it was.*  After installing the driver properly, everything worked very easily.

**Step 1**
This may or may not be necessary - I don't quite know due to all the stuff I've followed, but it works.  First, blacklist the rt2500pci and rt2500usb drivers.  Exact steps are a little fuzzy in my head, but as I recall, I edited:

> /etc/modules.d/blacklist

And added this toward the end:
> blacklist rt2500usb
blacklist rt2500pci

**Step 2**
Make sure that ndiswrapper is installed.  If you were like me you had no access to the internet on the actual machine itself so you had to get drivers from another computer and burn them do a CD (which will later be used as a coaster).

I was lucky to find two *.deb files on the Ubuntu 8.04 install CD.  Look under /pool/n/ and you should find two ndiswrapper packages.  Double-click those from within the GUI if it's running and install those two packages.

**Step 3**
Make sure that ndiswrapper is loaded at boot as part of a module.  Open:
> /etc/modules

And make it look like:
> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
ndiswrapper

**Reboot**.  

**Step 4**
While that's going, head over to Linksys.com.  Type "WUSB54G" in the search box.  Third link from the top should be the product page - click that, then click "Driver" on the right-hand side.  It'll ask for the version of the device you're using.  Turn the Linksys unit over and slide the mount thingy down and you'll see the label just as it's pictured on the site. **If there's no version number after "Model No. WUSB54G" your version number is 1**.  Download the correct driver version.

Here's where Microsoft's proof of monopoly status comes in: it's an *.exe file.  *sigh*  Go find a Windows box somewhere (I rebooted my MacBook Pro into Windows and did it from there) and open the *.exe file, which is just a self-extracting zip file.  (Note:  You *may* be able to just use unzip on your Ubuntu machine to unzip this file.  I don't know as I didn't want to waste a CD trying.)

You'll have a Drivers/ directory as part of the unzipped content.  Copy that onto a CD and insert that into your Ubuntu machine.

**Step 5**
Your machine has been rebooted and you now have the correct driver in the CDROM drive.  Open terminal (Applications -> Accessories -> Terminal) and cd into the CDROM's mount point:

> cd /media/cdrom0/...

Now you're into the right place; all you have left to do is install the driver using ndiswrapper.

**Step 6**
First you need to remove any existing NDISWrapper driver being used for the device.  Execute:

> sudo ndiswrapper -l

And unless you know what you're doing and *really* need something in that list, execute the following:

> sudo ndiswrapper -r <driver name>

Where <driver name> was one of the drivers listed by the -l output.

**WARNING WARNING WARNING:** The -r flag stands for **remove**.  This will DELETE a driver that you specify.  In my case this was necessary.  It may or may not be in your case.  If you are in doubt, ask some one who knows more than you and me combined.

Next, install the Linksys driver.
> sudo ndiswrapper -i WUSB54G.inf

Make sure that the entire directory tree is intact and exactly as it was when you first downloaded the driver.  You should have more than just the *.inf in that directory - a couple *.sys files and maybe some *.cab files too.

**Step 7**
Now you need to execute:
> sudo ndiswrapper -m

This tells NDISWrapper to use the drivers listed (or so it's been explained to me that way).

**Reboot.**

**Final Step**
Now that you've rebooted and you're back to the Ubuntu desktop, click the wireless network icon toward the top-right of your screen.  You should see a list of all wireless networks in range (assuming they're broadcasting an SSID.)  Just connect like you would on a Mac or Windows machine now.  Enjoy!

**To the Community:**
Feel free to pick this apart and add to, detract from, take away, correct, whatever - I'm fairly new to Ubuntu, though not to Linux as a whole, and as such am still learning.

---

