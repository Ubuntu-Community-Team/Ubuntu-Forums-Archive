---
title: "Buffalo AirStation Wireless-G High Power WLI-CB-G54HP pcmcia...several solutions"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by Funk Phenomena on 2008-05-29
Just posting to help others searching for this pcmcia card.  I'm just a noob that spent most of yesterday flailing my way through many threads and attempts and so here is some info that I hope helps more than it confuses.  
Let me preface this by stating that with the first two 'solutions' the card could see networks, but since I don't have a wireless router, I couldn't test to see if they'd connect.  That said, the noob that I am, I'd guess the first two to provide basic functionality, while the third solution is the best.  The fourth solution allows for packet sniffing and such.

[LIST=1]
[*]The card works fine using the native **b43** driver in Hardy 8.04.  If you haven't done anything yet, you should be able to see this by going System>Administration>Hardware Drivers.


[*]In Synaptic Package Manager, there are two 'drivers' you can find by searching for Broadcom: **b43-fwcutter** and **bcm43xx-fwcutter**.  Installing one or the other works and it fetches some firmware from la-la land.  I don't know what this provides over the basic b43 driver, but the card still works using either one of these.


[*]Uninstall either (or both) of those two 'drivers' from solution two and head on over to this thread for some more terminal love: [http://ubuntuforums.org/showthread.php?t=766560]("http://ubuntuforums.org/showthread.php?t=766560")  It's a bit long, but it worked for me without errors and I liked that it was super simple.  The author also shows how to undo what you just did (post 35 of that thread).  

With this I was able to get swscanner to work.  One caveat, swscanner from Add/Remove or Synaptic doesn't work in Hardy, at time of this writing.  But another user, **calraith**, put out a .deb of a working version here: [http://ubuntuforums.org/showthread.php?t=487058]("http://ubuntuforums.org/showthread.php?t=487058")  For a laugh, check out his multi-step reply on how one can spend 19 hours installing a printer...

However, with this solution I was unable to get the card in monitor mode, as ndiswrapper does not support it. No doubt the card works and is properly recognized, but if you want to use network analyzers and sniffers, you need to get the card in monitor mode.  Knowing that this worked, I did the undo then went to the next tutorial...


[*] Now this solution was a bit trickier for me as it wasn't noobified enough, though this allowed for monitor mode, capturing packets, etc... which was such a relief.  [http://forumubuntusoftware.info/viewtopic.php?f=42&t=1085&p=10175]("http://forumubuntusoftware.info/viewtopic.php?f=42&t=1085&p=10175")  

For step one, skip the b43legacy part and hit up the regular flavor.

For step two, make sure both those files are on your desktop.  I proudly used wget only to have to go find them and plop them on the desktop... doh.  Then you'll need to hit up Synaptic and install **linux-source-2.6.24** before following his instructions.  Also, check to make sure your kernel version matches his on this line: **sudo cp /usr/src/linux-headers-2.6.24-[COLOR="Red"]16[/COLOR]-generic/.config /usr/src/linux-source-2.6.24** I highlighted the 16 in red because my kernel version is 17.  This next edit was my own, because I thought this chunk was just for the  b43legacy users, so I removed it: **drivers/net/wireless/b43legacy/b43legacy.ko**  I just copied his step two code into a text editor to make the changes, then copy and paste the code to terminal. 

I still got errors when trying to monitor, so his code in 'troubleshooting' has been etched into memory (brain burn?):

[B]sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode monitor
sudo ifconfig wlan0 up[/B]

I added the sudos because I was getting errors otherwise.  You can verify your card is in monitor mode by typing **iwconfig** . I guess the default mode is Managed.  To get it off monitor mode, **sudo airmon-ng stop wlan0** .  Rinse and repeat with the three sudos for more fun.  With this I have been able to capture packets passively.  This whole network security thing has been a good read, especially on WEP and using strong passwords for WPA.


[/LIST]

---

### Post by texla on 2009-11-16
Solution #2 worked great in Karmic - installed **b43-fwcutter **and then rebooted and voila - Buffalo WLI-CB-G54S wireless card is shown in the networks available and connecting as well as it did in windows...

---

### Post by Dr.Bogo on 2011-05-10
If anyone wants/needs one of these cards I have a few available. I liked the idea of an external antenna so I collected them for awhile!

---

### Post by Dr.Bogo on 2011-05-10
I've got a few of these cards available!  [EMAIL="freedmanbilldrogo@yahoo.com"]freedmanbilldrogo@yahoo.com[/EMAIL]

---

