---
title: "Random freezing after wireless install"
date: 2007-11-26
forum: Networking &amp; Wireless
---

### Post by volfro on 2007-11-26
I recently moved, and there's no ethernet in my new place, so I got a wifi card for my desktop, which is running UbuntuStudio 7.10.

I bought the [D-Link WDA-1320 from Newegg]("http://www.newegg.com/product/product.asp?item=N82E16833127080"). The reviews on Newegg (and here in the forums) said that in most cases, the card works flawlessly with Ubuntu.

I got the card, installed it, and all I had to do after turning the computer on was allow the Restricted Drivers Manager to enable the Atheros HAL, then give the applet the WEP key. All was fine and dandy, until I was working and the computer just froze. It's a hard lock--nothing responds, including keyboard shortcuts to X (CTRL+ALT+Backspace/F1/etc.). My only option is the power button. 

It seemed like it was only freezing when the Wifi applet was working to re-connect (as it would lose the connection at random), so I assumed it was a driver issue and switched to Ndiswrapper. Ndiswrapper works fine--in fact, I think the Windows drivers are a little bit better--but the hard lock still happens seemingly at random. 

Is this a problem with the applet? Or is there something wrong with my hardware? This computer has been rock-solid for a long time; nothing was wrong until I installed the D-Link.

---

### Post by volfro on 2007-11-26
I just turned the computer off after another hard freeze. 

The applet looked like it was resetting the connection when the computer froze, so I'm beginning to think it's the applet. 

Is there a way to use my network without using the applet that's in the panel? Can I turn the applet off entirely?

---

### Post by growingtedium on 2007-11-26
I've got a Trendnet Atheros card and I use a script to log in to my network.  Perhaps you can modify this to match what you need.  The first two lines may not be necessary - not sure.  Only one of the last two lines are needed - I happen to use dhclient.

sudo wlanconfig ath0 destroy
sudo wlanconfig ath0 create wlandev wifi0 wlanmode managed

sudo ifconfig ath0 up
sudo iwconfig ath0 essid NETWORKNAME key NETWORKKEY

sudo dhcpcd ath0
sudo dhclient ath0

Hope it helps.

---

### Post by volfro on 2007-11-26
I'm pretty sure it's an Atheros card that D-Link distributes, so this should work...how would I disable the applet (or any other Gnome utilities) from accessing the card?

Thanks for the script, I'll definitely try it out as soon as I've figured out how to turn off the applet.

---

### Post by volfro on 2007-12-03
For now, the script is working. I just run a sudo killall nm-applet at the top of it, because that's what seems to be freezing.

Hopefully this'll be stable now. It hasn't frozen yet, but it's only been a few minutes...I'll post again here when I find out it's stable or unstable. 

Thanks for your input! Seems to be connecting just fine via script.

---

### Post by volfro on 2007-12-04
Nope. The computer froze again today. 

Gonna do a memory test tomorrow and see what turns up...hopefully my RAM is okay.

---

### Post by volfro on 2007-12-04
Memtest86 says my RAM is fine, after an hour of testing. 

Has anybody else experienced this weirdness? I'm going to do a format/reinstall to see if that helps, as that's the only thing left I can think to do. (Been using Linux for awhile, but I'm by no means a guru. I've never really had to be...it's always worked pretty well for me without much tweaking.)

---

### Post by SyberKowboy on 2007-12-04
I get solid freeze up running on certain networks when I am running certain apps, particularly any torrent clients. Pretty sure it's from outside sources, but have never logged all my traffic to find out for sure. Not likely the same issue you are going through unless the network has others using torrent apps on it. Might be worth looking into.

---

### Post by volfro on 2007-12-04
My landlord doesn't use torrents at the moment, and when my machine freezes, the most it's usually doing is Firefox or Amarok. (Or, like yesterday, Rhythmbox.) I haven't been doing anything to bandwidth- or CPU-intensive (like work) because I know it's going to freeze.

---

### Post by volfro on 2007-12-05
I just booted up a fresh Ubuntu installation (including a fresh home directory, which I hadn't been formatting for awhile), and the exact same thing happened.

It connected to the network just fine, then I was unable to access the Internet to download updates, then as the connection restarted, the computer froze solid.

That's really frustrating.

...come to think of it, would this have anything to do with the fact that I'm on AMD64? I'm running Ubuntu x86, but it's 64-bit processor...I'll try installing Ubuntu x64 tonight, if I can stay awake. (I really need this computer to work! It's my production machine!)

---

### Post by volfro on 2007-12-05
I installed Ubuntu 7.10 x64. It ran pretty solid for about three hours--including a few times where the wireless connection became unstable. But, about a minute ago, it froze. 

I'm at my wits' end with this. Does anybody have any idea why this wireless card would be causing hard locks like this on a fresh install? Has anybody else experienced this?

---

### Post by volfro on 2007-12-06
Alright, I can't figure it out. Called NewEgg today to get an RMA number, and I'm sending the D-link back. 

Instead of using an internal or USB card, I went ahead and ordered an ethernet bridge. It's a Buffalo Technologies one that got really good reviews, and once it's set up, it's done, no additional drivers needed.

Shame, too; when the D-Link card worked, it worked well. Ubuntu recognized it and installed it without a hitch. I'm guessing there's something funky with my hardware that causes it to crash.

---

### Post by mocha on 2007-12-10
I have that same card, it never froze on me for about 6 months, until....  The other day I executed " sudo wlanconfig ath create wlandev wifi0 wlanmode monitor" in order to get an "ath1" adapter in monitor mode.  This is what causes the freezing if the machine is left on like this for a number of hours.  At least that is all I can see that is going on.  I guess I should do "sudo wlanconfig destroy ath1" when I'm done with it.

---

### Post by volfro on 2007-12-11
Update: I'm pretty sure my motherboard is on its way out. Got the ethernet bridge, and the on-board ethernet refuses to work (which has literally never happened before). Installed a PCI ethernet card and I get the same issue: it'll work for a bit, then just stop. 

It must've been hit by a power surge, or maybe my move knocked something loose; up until now, this computer (and Ubuntu) has been rock-solid.

This sucks, because my motherboard is not quite a year old, and this is my work machine. Looks like I'll be buying another board, though...

---

