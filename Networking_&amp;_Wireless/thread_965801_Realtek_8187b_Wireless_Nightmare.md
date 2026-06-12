---
title: "Realtek 8187b Wireless Nightmare"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by Midnightsun on 2008-10-31
Hi guys,

Been using Ubuntu for about 6 months now and thought it was time to revisit a problem I never solved when I first installed. I'm currently using Hardy.

My laptop has a Realtek 8187b wireless adapter which is well documented as being a pain in the backside for linux.  I've never been able to get it working.

The way my laptop is set up, the adapter appears to actually be connected internally via USB.  In Windows I need to press "Fn+F10" to enable it (plays the little USB plugged in sound) and go from there.  

In Ubuntu I've tried various drivers, tried ndiswrapper with the win98 drivers nothing seems to work.  When following the instructions [**here**]("http://ph.ubuntuforums.com/showpost.php?p=5803229&postcount=3") the gui just says "Hardware Present: No"

Now I seem to remember it used to at least be listed in lsusb so I was worried that the adapter itself was faulty.  Created a new partition, installed XP and it still works fine, so no idea why it's no longer showing in lsusb.  

I would really appreciate any help people can give in getting this nagging problem working.  Currently I'm getting by mostly with ethernet in the house and borrowing an external usb dongle when taking it out on my travels which is far from ideal.  I'll include some terminal outputs that may or may not be of help.

[B][COLOR="Blue"][lsusb output]("http://pastebin.com/f2f28e414")
[lspci output]("http://pastebin.com/f2c4f530d")
[ifconfig output]("http://pastebin.com/f444ca12")
[iwconfig output]("http://pastebin.com/f617b9f15")
[/COLOR][/B]
Thanks!

Also - should note this is an almost fresh install of Hardy following a rather painful upgrade attempt to intrepid (my graphics adapter sucks even harder than wireless).  As you can probably tell, this laptop was not built with Linux in mind.

---

### Post by ctglahn on 2008-11-08
I had Hardy working with NDISWrapper and the Windows XP driver.
Worked FLAWLESS until upgrading to IBEX - a whole other story.

---

