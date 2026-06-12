---
title: "Help for those using the dreaded Atheros AR5BXB63 Card"
date: 2008-11-28
forum: Networking &amp; Wireless
---

### Post by ArcDarkWolf on 2008-11-28
Hey there,
If you're reading this, you're probably in the same position as me. You own a laptop, that has the Atheros AR5BXB63 Wireless Networking Driver Card. Ubuntu (and other) 8.04+ just doesn't like it. Obviously, there have been many ways to fix this problem, and I'm going to share one that works for me. You've probably heard it before, but there are a few extra things that no one was kind enough to mention.

Right, so first you're going to need Madwifi, even though our wireless card isn't actually compatible with it. Be sure to have a hard line connection (ethernet) until said otherwise.

Thankfully, Madwifi have a wiki with the instructions on bow to install the application, and to save me lots of copy and pasting, and overall post take up, I'll just give you this link: [http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo]("http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo")

As soon as you're sure Madwifi is installed, you're going to need ndiswrapper, which can be found in Add/Remove programs. And since that's easy to install, there's no point saying anything else.

Now even though you've got Madwifi working, and ndiswrapper installed, you're still going to need the drivers. You need the XP drivers, not Vista ones. One small problem however, these are now as rare as rocking horse poop. But after nearly 12 hours of painful searching, I managed to find them, and have uploaded them to my e-snips account. This link [http://www.esnips.com/web/UbuntuHelp]("http://www.esnips.com/web/UbuntuHelp") will take you to the folder in which I store them, just scroll down and look for the ar5007 file. Download that and extract it to somewhere that you intend not to touch for a long time. I made a folder in my documents called "Wireless Drivers" and stuck 'em in there. Just make sure you don't delete those drivers.

Then use ndiswrapper (System > Administration > Windows Wireless Drivers) and install the necessary drivers. It should say that the hardware is present if you installed it correctly. A reboot should probably be a good idea right about here. Take note: After the reboot and your wifi is working, great! You can use that, but you need to read on. And if it's not working... read on!

After your reboot, you're going to want to save this to a text document and keep it safe, since some system updates mess up some of the install.

First off, CD into your Madwifi directory with a Terminal, and then input the following:
```
sudo make clean

sudo make

sudo make install

sudo modprobe ath_pci
```

Use this every time an update seems to disable your drivers. Oh, and one more thing. If you're STILL not getting any connections via wifi (Just not even saying there's a wireless option) don't panic! Just go into your Driver Manager, disable and re-enable your Support for Atheros driver. No reboot required.

So the condensed version is:
Install Madwifi
Install ndiswrapped
Download Drivers
Install Drivers via ndiswrapper
Reboot
Disable and Re-enable drivers in Driver Manager if there's still a problem
And after updating and using the last step doesn't work, use the code above!

Hope this helps, oh, and if you want to tidy these steps up and repost them, go for it. Feel free to share my e-snips link to people who need it too!

---

### Post by Paperfolder on 2010-09-26
Does this work for 10.04LTS?

WiFi worked perfectly with Xandros.

I installed 10.04 netbook version on a new 64 gb RunCore SSD

Thanks

---

### Post by Paperfolder on 2010-09-26
OK.

Just for kicks, I jumped into the Bios.

Wireless disabled.  Why, I have no idea.  It was enabled with Xandros.  This is a new SSD, clean install of Netbook LL 10.04.

So just check it before you get into MadWifi, ndis wrappers, etc.

Freaky.

---

