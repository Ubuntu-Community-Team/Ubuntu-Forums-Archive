---
title: "netgear USB wireless adapter not working in 9.04"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by MrCode on 2009-07-08
Hi, all.  I'm not all that familiar with Linux in general, but I had been using a virtual machine with Ubuntu on it for a while, and I've grown a somewhat good sense of how to get around and do certain things from the command line.  I have been using a USB wireless-n adapter for getting online with Windows and the virtual machine, but the VM just sees the adapter as a wired network port (auto eth0 or something like that).  Now I've done a dual-boot install of Ubuntu without partitioning (using the "install inside Windows" option on the livecd), and it won't recognize my wireless adapter!  If I pull down the menu under the network status icon, it says "No network devices available", or something along those lines, in a greyed-out button option.  It's a Netgear RangeMax NEXT Wireless-N USB adapter...  is there any place I could maybe get Linux drivers for this particular type of adapter?  If not, is there anything else I can do?  This really is my only way of getting online, as I'm on the second floor of my house and the router is in the basement, and running ethernet cable through the house would just be too much of a hassle...

---

### Post by Ian dewhurst on 2009-07-08
Have you NDISwrapper installed?
If not then install this through synaptic and then under windows copy the drivers over to the ubuntu partiton (I think its the .inf extension you'll need)
Then under system-administration-windows wireless devices (I think) install the driver from there.

---

### Post by alexlafreniere on 2009-07-08
To clarify the last poster, ndiswrapper lets you use the Windows drivers for your wireless device in Linux. So first you should install ndiswrapper:

```
sudo apt-get install ndiswrapper
```

Then go to the manufacturer's website and grab the latest drivers. Here's a great tutorial on using ndiswrapper: [http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/](http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/)

---

### Post by MrCode on 2009-07-08
Well...  I looked at the wikipedia article on ndiswrapper and the wrapper's wiki on SourceForge, and it appears that 1) the adapter I'm trying to get working isn't on any of their lists (working, not working, or maybe working), and 2) ndiswrapper is for IA-32 and x86-64 systems only...  I'm on a 32-bit system!  Am I totally screwed?  Or will it work with just standard x86?  Also, I tried searching for the package in synaptic pkg manager and it couldn't find it...  also tried ```
sudo apt-get install ndiswrapper
``` only to get an error message back saying it couldn't find the package.  Now I'm really stumped...

---

### Post by alexlafreniere on 2009-07-08
x86-64 is just an abbreviation meaning it works on both x86 and x64 systems (or 32-bit and 64-bit, if you prefer that nomenclature). And don't worry if your device isn't listed, I have a system at home with one of those "unlisted" cards, and it works just fine. Since it isn't in the repos, get the binary from SourceForge. And this thread is stickied for a reason: [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

---

### Post by MrCode on 2009-07-08
Ok, I've downloaded the ndiswrapper packages from [here](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper), and put them on a thumb drive and installed them in the Ubuntu "partition" (if you really want to call it that) from that.  When I open the Windows Wireless Devices dialog and go to add a system driver, though, it's asking for an **inf** file, and according to Windows Device Manager, the adapter uses a driver by the name of "MRVW245**.sys**".  Will .sys drivers work?

---

### Post by MrCode on 2009-07-08
Well this just plain sucks...  I tried using the .sys driver and it flat out rejected it, saying it's invalid...  does that mean I'm screwed?  I ***really*** don't know what to look for here.  If that's not what it wants, then what *does* it want!?

---

### Post by kerry_s on 2009-07-08
there should be an inf file in the same place that sys file is. 

i just realized you did a dualboot right, go into the windows to C:\WINDOWS\inf\WN111(i think) and grab a copy of the sys & inf files.

---

### Post by MrCode on 2009-07-08
Thanks kerry!  I got the (correct) drivers working, and I'm posting this from Ubuntu.  Thanks to everyone for the help!

---

### Post by MrCode on 2009-07-08
Err, while I may have already said thanks above, I think I need help again.  It seems that while the drivers seem to work, it seems to have a hard time connecting; most of the time it will refuse to connect.  I'll choose the appropriate network, enter it's name and pass, and hit Connect.  It'll hover there for a minute or two, and *sometimes*, it will manage to connect.  However, it seems more often than not that it'll just time out with the message &quot;[router name here] Disconnected.  You are now offline.&quot;  Is there more to configure?  Or is it because the router is (for some odd reason) Windows specific?  It's a netgear, too.  will I have to do a similar driver thing like I did for the adapter?  EDIT: The adapter works correctly 99% of the time in Windows.

---

