---
title: "Will my Wireless Device Work?"
date: 2007-08-30
forum: Networking &amp; Wireless
---

### Post by Orangepenguin on 2007-08-30
So, I am using Mandriva 2007 right now and my wireless WUSB54G Ver. 4 (Linksys, USB) adapter is working great and set itself up almost automatically.  I am thinking about making the switch to Ubuntu and I am wondering if theres a good chance my wireless adapter will work.  I checked out the list of compatible devices you guys so conveniently have stickied, and this is what it said: 

Works fine with WEP on 6.06/Breezy when installed, but hung at activating using LiveCD; works on 7.04/Feisty w/ WEP with manual config and roaming other connections.

I am planning on using the 7.04/Feisty version and I am wondering what the "w/ WEP with manual config and roaming other connections" exactly means and if I should hold off on switching to Ubuntu for now.  

Thanks for any and all replies.

-orange

---

### Post by wickstopher on 2007-08-30
I've had the same USB adapter working great in Ubuntu since Edgy (which is when I hopped on board).   What it means is that you'll have to manually configure your network settings (you might even have to manually configure the network name), but once you do, it should work right out of the box, without installing any extra software.  You'll probably have to turn off "roaming mode" and then manually enter the network name and security key.  I've had great luck.  Once you get it working, you might want to consider installing wicd to replace the Network Manager software included with Ubuntu, as it seems to work a bit better with this device (i.e., fewer disconnects).  I've only just recently started using wicd, but since installing it, I haven't had any problems or any of the annoying disconnects that I was getting before (hopefully i'm not jinxing myself!).  See thread: [http://ubuntuforums.org/showthread.php?t=530741]("http://ubuntuforums.org/showthread.php?t=530741") for my progress report with wicd.

---

### Post by kevdog on 2007-08-30
Wick

Change that avitar -- its nasty!

---

### Post by Orangepenguin on 2007-08-30
Thanks for the replies.  Well, Ill admit that I am not exactly sure how to manually configure my network settings.  Is this like my IP and stuff?

---

### Post by wickstopher on 2007-08-30
> Wick

Change that avitar -- its nasty!


awwww...I thought it was kinda cute!  No other Burroughs or Cronenberg fans on here?  I don't believe it!  Yours isn't too bad as far as suggestively disgusting goes, either, my friend. ;)

And, as far as manually configuring, it's not that hard, actually.  It's all done through the GUI.  Just go to System > Administration > Network, and if you're using the WUSB54Gv4, you should already have a wireless connection in there (if not, try rebooting with the device plugged in).  Click on "properties" for your Wireless Connection, turn off roaming mode, and manually enter your network name and security key info.

---

### Post by Orangepenguin on 2007-08-30
EDIT: NEVERMIND. Fixed it, thanks for the input wick.

---

