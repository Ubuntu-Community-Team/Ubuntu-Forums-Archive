---
title: "Win XP - Can't install driver for wi-fi internet device"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by Roger Allott on 2010-02-07
Does anyone fancy helping me with a Windoze problem?

I bought a second-hand PC from an acquaintence on Friday, which has Win XP installed on it.

I had always intended putting Ubuntu onto it, but as it hadn't been booted up for a fair few months, I wanted to do a Windows Update first.

But that requires getting oneself connected.

As there's no internal wireless (as far as I know), I've plugged in a D-Link DWL-G122 wireless USB adapter.

It seems that I've got much too used to plug-and-play, because upon booting, the 'Found New Hardware' dialog appears. Of course, it wants to find the driver for the D-Link on the web, but that presents a rather obvious problem!

So, I've done some Googling and found the latest Win XP driver for the device. It's not available as a self-installing .exe, but as a zip file. I've extracted it and the following files are in there:

setup.exe
[INDENT]a folder called 'Drivers' containing:
PRISMA02.cat
PRISMA02.inf
PRISMA02.sys
a folder called 'WinXP' containing:
[INDENT]PRISMA02.sys[/INDENT][/INDENT]

When I double-click the setup.exe file, I get error messages when I reboot, and the 'Found New Hardware' dialog thing springs up again.

When I try to install the driver through Device Manager, I get the error message again when I reboot.

I've attached the error message to this post.

Something that confuses me is my Network Connections screen, which suggests that there's a 1394 Net Adapter somewhere, but I've no idea what that is. On it's status, it tells me that I've been connected to something for some time, but with no data whatsoever going in or out.

Oh yes, and by the way, when I installed Ubuntu, my D-Link internet connectivity just worked out of the box without any issues whatsoever.

---

### Post by mk1w86 on 2010-02-07
Did you get the drivers from the D-Link website?  If you cannot get your wireless adapter working does the machine have an ethernet port you can temporarily use?

The 1394 network adapter is for a firewire network, I think is says connected becuase of the way firewire works it appears permanently connected to the machine even if there is no cable plugged in.

Also if you are going to continue using Windows XP you might prefer to do a clean install instead of using your acquaintance's installation. ;)

---

### Post by goldshirt9 on 2010-02-07
agree with the above totally
do a clean install of xp and then install ubuntu.

---

### Post by Roger Allott on 2010-02-07
> **mk1w86 said:**
> Did you get the drivers from the D-Link website?
No. That particular adapter is no longer supported by D-Link. I got the driver from various well-known sites such as Softpedia.


> **mk1w86 said:**
> If you cannot get your wireless adapter working does the machine have an ethernet port you can temporarily use?
It might be possible, but the PC is quite a distance from my router, so it'll be a right pain in the butt.


> **mk1w86 said:**
> The 1394 network adapter is for a firewire network, I think is says connected becuase of the way firewire works it appears permanently connected to the machine even if there is no cable plugged in.
Thanks for that info.

> **mk1w86 said:**
> Also if you are going to continue using Windows XP you might prefer to do a clean install instead of using your acquaintance's installation. ;)
Unfortunately, I don't have the XP disc. But in any event, would a fresh install of XP load the driver for the adapter without being able to connect to the net?

---

### Post by jimbean on 2010-02-07
i know with a blue tooth adapter, i have to wait for xp to boot up completely then attatch the adapter otherwise xp has trouble finding it

---

### Post by jimbean on 2010-02-07
also did you download the wireless drivers for your mobo
there probably on there site {motherboard`s} also check to see if your bios has an option to turn it off and on {wireless}

---

### Post by mk1w86 on 2010-02-07
> No. That particular adapter is no longer supported by D-Link. I got the driver from various well-known sites such as Softpedia.


Even if a product is no longer manufactured or supported you can usually still get drivers for it from the manufactures website, make sure to look under the support section not their current line up of products. ;)

I had a look at the D-Link website and found information and downloads for your adapter :D (the link is to the UK website):

[http://www.dlink.co.uk/cs/Satellite?c=Product_C&childpagename=DLinkEurope-GB/DLProductCarousel&cid=1197319528697&p=1197318962342&packedargs=ProductParentID%3D1195808623928%26locale%3D1195806691854&pagename=DLinkEurope-GB/DLWrapper](http://www.dlink.co.uk/cs/Satellite?c=Product_C&childpagename=DLinkEurope-GB/DLProductCarousel&cid=1197319528697&p=1197318962342&packedargs=ProductParentID%3D1195808623928%26locale%3D1195806691854&pagename=DLinkEurope-GB/DLWrapper)

I don't know exactly which drivers you need because I don't know what revision your adapter is.

> Unfortunately, I don't have the XP disc. But in any event, would a fresh install of XP load the driver for the adapter without being able to connect to the net?


Possibly, although unless there is a problem with the current installation it should have installed the drivers if they are built in to XP.  When I suggested ethernet in my previous post there is a chance the drivers are available from Windows Update.

---

### Post by Mark Phelps on 2010-02-07
Next time you're in Windows and running IE, google for Microsoft Update Catalog.  This will open an MS Website that will allow you to search Windows Update for drivers for your device.  You have to be running IE v6 or greater to use this (typical MS limitation).

---

### Post by Roger Allott on 2010-02-07
> **mk1w86 said:**
> 
I had a look at the D-Link website and found information and downloads for your adapter :D (the link is to the UK website):

[http://www.dlink.co.uk/cs/Satellite?c=Product_C&childpagename=DLinkEurope-GB/DLProductCarousel&cid=1197319528697&p=1197318962342&packedargs=ProductParentID%3D1195808623928%26locale%3D1195806691854&pagename=DLinkEurope-GB/DLWrapper](http://www.dlink.co.uk/cs/Satellite?c=Product_C&childpagename=DLinkEurope-GB/DLProductCarousel&cid=1197319528697&p=1197318962342&packedargs=ProductParentID%3D1195808623928%26locale%3D1195806691854&pagename=DLinkEurope-GB/DLWrapper)

I don't know exactly which drivers you need because I don't know what revision your adapter is.

You're a gentleman and a skolar, Sir! My revision is B1, so once I found that out, getting the correct driver from that site was simple.

And installing it on Windows was fairly painless.

Then I had to update Windows, which has taken quite a few hours, with numerous restarts required.

I've installed Firefox and AVG, updated Adobe's stuff, and now to install OpenOffice for compatability with my Ubuntu.

---

### Post by Sylslay on 2010-02-07
Had the same card with my Desktop, but not sure (at the momnet)  witch revison,

Plesae let me know ,
Is working fine with Ubuntu Live CD.

PS
Most drivers in XP need be install before You plug any hardwere.

Had error mesage  (when system start - from D-link softwhere), after upgrade to sp3, 
but wi-fi card still working fine.

---

