---
title: "[SOLVED] Linksys WPSM54G Print Server?"
date: 2007-11-27
forum: Networking &amp; Wireless
---

### Post by wieman01 on 2007-11-27
Quick question... I am contemplating buying a Linksys WPSM54G Print Server and common sense tells me it will work with any OS, even Linux. Could anybody confirm that? Since it communicates via a standard protocol any print server should do, right?

The Linksys WPSM54G is nice because it has wireless connectivity and supports WPA2.

_**EDIT:**_
I don't think I need to install any sort of driver, do I?

---

### Post by wieman01 on 2007-11-28
I found something interesting here which makes me believe that this device should work even using Ubuntu. I will give it a shot & post back.

[http://ubuntuforums.org/showthread.php?t=516747]("http://ubuntuforums.org/showthread.php?t=516747")

---

### Post by tbedolla on 2007-11-30
Wieman,

I am currently trying to get my linksys WPSM54G working on my recently installed Ubuntu run laptop...it was previously running XP and the print server was working fine. I've been following the seemingly related post:

Linksys WPS54G Wireless Print Server with HP LaserJet 1320 on Ubuntu

...but I haven't had any luck as of yet. I can print directly from the laptop to the printer, HP Photosmart C4810, but I haven't had any luck yet with the wireless. Have you found another path than the one described in the above post?

Appreciation Flows,

TBedolla

---

### Post by wieman01 on 2007-11-30
> **tbedolla said:**
> Wieman,

I am currently trying to get my linksys WPSM54G working on my recently installed Ubuntu run laptop...it was previously running XP and the print server was working fine. I've been following the seemingly related post:

Linksys WPS54G Wireless Print Server with HP LaserJet 1320 on Ubuntu

...but I haven't had any luck as of yet. I can print directly from the laptop to the printer, HP Photosmart C4810, but I haven't had any luck yet with the wireless. Have you found another path than the one described in the above post?

Appreciation Flows,

TBedolla
Actually I have seen posts in other forums that confirm that this device works with Linux as well, however, since it is not yet on sale in Europe, I will have to go for the WPS54G instead. It reportedly supposed WPA2 (although the documentation states otherwise) as of late.

What are the problems you encounter? Do you have a direct connection to the device through Ethernet?

---

### Post by wieman01 on 2007-12-01
I tried to install & configure the WPS54G yesterday and I gave up after long 2 hours. What a piece of junk... I knew that I would not support WPA2 (AES), so no issue at all. But getting the wireless function to work and making the device associate with my router turned out to be a nightmare. 

After messing around with it for 2 hours I eventually gave up and I will return the device and get myself another brand. It's really silly, I thought Linksys had learned their lesson. This is the 3rd frustrating experience with a Linksys device and that's it, I am over it, I'll no more buy anything from Linksys. Their hardware is such a waste of time. Not because the hardware is bad per se, but their firmware (in general) really sucks.

Sorry for ranting. But hardware you are unable to set up in less than 1 hours as an experienced user is simply not worth it. Shame on Linksys... once again.

_**EDIT:**_
One thing that annoyed me most was that the thing refuses to cooperate with FIrefox or Konqueror. The router crashed after the first welcome screen unless you access it with Internet Explorer. How ridiculous is that?!

I even used Windows and their installation CD to configure it just in case you want to know.

---

### Post by wieman01 on 2007-12-01
I have decided I won't buy a wireless print server at all. I'll connect a Linux compatible printer to my Desktop PC and run print job from other wireless clients through there. It's simply not worth the hassle... Most wireless print server do not support WPA2 (which is a must) and their compatibility with 3d party printers will the next stumbling block. Why bother? 

Even if it works today, there is no guarantee the manufacturer will continue to support new printer models in future, so at some point you might even have to buy a new piece of hardware. I simply don't see a reason why I should go through it. That's my two penny worth.

---

### Post by froy02 on 2007-12-01
Port servers are pieces of junk. I tried 3 different types and they work only once in a while in all flavors of windows.  I would not even try them in ubuntu. The money you spend on a server, you could buy a  new MFC printer with wired/wireless networking. 

The 2 brands that i know to have linux support are brother and hp.  Very hard to find linux drivers for canon.

---

### Post by wieman01 on 2007-12-02
> **froy02 said:**
> Port servers are pieces of junk. I tried 3 different types and they work only once in a while in all flavors of windows.  I would not even try them in ubuntu. The money you spend on a server, you could buy a  new MFC printer with wired/wireless networking. 

The 2 brands that i know to have linux support are brother and hp.  Very hard to find linux drivers for canon.
I'll stay away from them. :-)

Do you have any recommendation though?

---

### Post by froy02 on 2007-12-02
I am using a Brother MFC665cw, networked(wired) and we can print and scan  from 2 vista laptops (wireless), 1 desktop XP and 2 UBuntu machines. I chose it  only because I can get generic ink cartridges (not refilled) for less than half the price of the name brand.
Most hp's  are now networked also and just like brother they have a linux driver site.

Visit the hp or brother websites for linux and they have a list of their supported printers and mfc's.

---

### Post by tbedolla on 2007-12-03
Wieman,

I have the WPSM54G print server working wirelessly...finally!

This URI may or may not work for you, but here it is:

[http://192.168.0.11/P1](http://192.168.0.11/P1)

...where obviously the ip address is the address of the print server. After beating my head against the wall trying every possible permeatation of the URI given in other threads (referring to the WPS54G):

ipp://192.168.0.11:631/ipp/P1

The discovery happened when I found an old thread that described how to infer the correct URI from the device...run an nmap operation on the device

nmap 192.168.0.11

which took 76 sec to complete, but returned a list of open ports and expected protocols on each. Instead of ipp, the WPSM54G offered http on port 80 (automatically forwarded port). I had noticed that on the CUPS pages there was a listing of possible URIs and this one seemed to make the most sense with this new info.

http://<ip-address or hostname>/resource

I'm not sure if this was the same issue that you were running into, but hopefully this can help some others out there looking for wireless printing on the Linksys WPSM54G print server from an Ubuntu 7.10 (Gutsy Gibbon) install.

Cheers,

Toma

---

### Post by wieman01 on 2007-12-03
Toma,

That is great news indeed. Does the WPSM54G support WPA2 (AES) as well? Could you check that for us? And what printer do you use?

Thanks, dude.

---

