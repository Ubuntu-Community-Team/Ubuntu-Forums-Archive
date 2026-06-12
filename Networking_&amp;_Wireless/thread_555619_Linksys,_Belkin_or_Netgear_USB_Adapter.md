---
title: "Linksys, Belkin or Netgear USB Adapter?"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by uputer on 2007-09-20
I am considering getting a wireless USB adapter for my computer but I want to get one that is not too difficult to configure.   I went to the Wiki here but apparently, some of the info is outdated.

Out of Linksys, Belkin and Netgear, which one do you think is easiest to configure for a newbie?:

Linksys WUSB54G

Belkin F5D7050

Netgear WG111

I understand it also depends on the chipset and version of the adapter (since some versions have been built with a different chipset?).   But, if anyone has any that is working, please list your adapter and the version.   I'm limited to which ones I can choose since the choices are limited (because of location and dealers).   In addition, a lot of the ones available are the most recent and new versions and they probably don't have very good compatibility with Ubuntu (yet?).   

Thanks to all responders and if there are links here that help (not the wiki, as I have that), that would be great, too.   Much appreciated.

---

### Post by calraith on 2007-09-20
I know the Netgear WG111 requires ndiswrapper, which is pretty easy to install but can be a pain if you don't have at least a temporary wired connection to download the software.  I don't know about the other two adapters.

---

### Post by Guitar John on 2007-09-20
> **uputer said:**
> I am considering getting a wireless USB adapter for my computer but I want to get one that is not too difficult to configure.   I went to the Wiki here but apparently, some of the info is outdated.

Out of Linksys, Belkin and Netgear, which one do you think is easiest to configure for a newbie?:

Linksys WUSB54G

Belkin F5D7050

Netgear WG111

I understand it also depends on the chipset and version of the adapter (since some versions have been built with a different chipset?).   But, if anyone has any that is working, please list your adapter and the version.   I'm limited to which ones I can choose since the choices are limited (because of location and dealers).   In addition, a lot of the ones available are the most recent and new versions and they probably don't have very good compatibility with Ubuntu (yet?).   

Thanks to all responders and if there are links here that help (not the wiki, as I have that), that would be great, too.   Much appreciated.

I had no luck with wireless (even with the various tutorials) using Linksys.  I threw up my hands and sprung for the Belkin F5D7050.  Make sure you get version 4.  Version 1 uses a different chipset.  Version 4 worked "out of the box" for me.   

I got mine from [New Egg]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833314011").  I would have been happier with a card, but right now I'm just happy to be wireless and working.

YMMV,

---

### Post by uputer on 2007-09-22
I got the Belkin one and it's version 4.   What do you mean it works, 'out of the box?'   You must have to do something.  I wanted to get it working in Windoze first but even that is turning out to be a chore.

Anyone know how with a Linksys router?

---

### Post by Guitar John on 2007-09-30
What I meant by *works out of the box* is that the chipset is supprted without having to mess with *ndiswrapper*.  Most of these guys can explain this way better than I can.

What I did is use Network Manager.
Enable Roaming.
Create a New Connection.
Call the connection whatever you named your network.
Type in the password.

Surf!

---

### Post by mightyteegar on 2007-09-30
I just bought the latest WG111 (v3) and it was easy to get the device running using ndiswrapper -- once I finally found the drivers!  The problem with this USB device is that the installation CD doesn't contain just the drivers anywhere on it; you have to run the setup program to get to them.  And strangely, the .sys and .inf driver files don't have the same filename (one is wg111v3.sys and the other is oem9.inf -- ???).  What I ended up doing was booting into Windows and copying the drivers over to my Linux partition.  

All told, I'd recommend researching other products.  I wish I'd done a little more homework before I bought the WG111v3; however, the machine I use it on currently runs Windows and it works fine in that environment.

---

### Post by uputer on 2007-09-30
> **Guitar John said:**
> What I meant by *works out of the box* is that the chipset is supprted without having to mess with *ndiswrapper*.  Most of these guys can explain this way better than I can.

What I did is use Network Manager.
Enable Roaming.
Create a New Connection.
Call the connection whatever you named your network.
Type in the password.

Surf!
Show me where the chipset is supported?   I have bookmarked several references of people having problems with the zydas zd1211b chipset and zd1211rw driver.   I tried a Gutsy 7.10-beta LiveCD to no avail.   Same thing.  'Doesn't work and behaves the same.   Are you even using Feisty?  

I suggest there isn't anything that works out of the box in USB wireless Linux unless it's old hardware (say USB 802.11b or something).   Unless there are droves of people claiming it works and explaining what is done, I think it's not available yet.

---

### Post by bennyz on 2007-10-06
I have the Netgear WG111v3.  I use it on my Sony Laptop running WindowsXP.  I want to use it for my desktop in the other room running Ubuntu Feisty 7.04.  I copied the files wg111v3.sys and oem9.inf to a folder in my home dir.  However, I am new to linux and don't know how to install that using ndiswrapper.   Can someone provide a step by step?

Thanks

---

### Post by uputer on 2007-10-06
I don't know of that adapter with v.3 but a search gave me this:
[http://ubuntuforums.org/showthread.php?t=212365&highlight=Netgear+WG111v3](http://ubuntuforums.org/showthread.php?t=212365&highlight=Netgear+WG111v3)
[http://ubuntuforums.org/showthread.php?t=51993&highlight=Netgear+WG111v3](http://ubuntuforums.org/showthread.php?t=51993&highlight=Netgear+WG111v3)
[http://ubuntuforums.org/showthread.php?t=414207&highlight=Netgear+WG111v3](http://ubuntuforums.org/showthread.php?t=414207&highlight=Netgear+WG111v3)
[http://ubuntuforums.org/showthread.php?t=56346&highlight=Netgear+WG111v3](http://ubuntuforums.org/showthread.php?t=56346&highlight=Netgear+WG111v3)

Try one of those links and see if one of the instructions listed in there is something that looks interesting to try. ;-)

---

### Post by delmore on 2007-10-19
Although it has worked out of the box since at least Edgy, the WUSB54G is currently broken in the Gutsy release

[http://ubuntuforums.org/showthread.php?t=580448&highlight=wusb54g](http://ubuntuforums.org/showthread.php?t=580448&highlight=wusb54g)

---

### Post by AvengerMoJo on 2007-10-24
[http://en.opensuse.org/SDB:WG111v3](http://en.opensuse.org/SDB:WG111v3)

download the inf file and use ndiswrapper should work.

---

### Post by Guitar John on 2007-10-24
> Show me where the chipset is supported? I have bookmarked several references of people having problems with the zydas zd1211b chipset and zd1211rw driver. I tried a Gutsy 7.10-beta LiveCD to no avail. Same thing. 'Doesn't work and behaves the same. Are you even using Feisty?

First, apologies for taking so long to answer you.

I bought 2 of these.  One for my Dell 4700 Desktop and one for my wife's Dell 2100 Laptop.  In both cases, I plugged it into the USB port, and  did what I said previously:

> 
What I did is use Network Manager.
Enable Roaming.
Create a New Connection.
Call the connection whatever you named your network.
Type in the password.

Surf!

One addition:  Choose the same level of security as on your router.

I did not have to install any drivers.   

 FWIW, I am far from being any kind of power user.  I had a long and frustrating process and no luck with a previous device that worked fine under XP.  Also, this past weekend, I did a clean install of Gutsy on both computers.  I had wireless working when running from the live cd.  I did the install, and everything worked like it should.  All I had to do was re-enter the above info into Network Manager.

---

### Post by mdurham on 2007-11-16
Guitar John wrote: > What I did is use Network Manager.
Enable Roaming.
Create a New Connection.
Call the connection whatever you named your network.
Type in the password.

"**What I did is use Network Manage**r" is that "network-admin"?
How do I "**Create a New Connection**"? I don't see that anywhere using network-admin.
Does all this assume that the WG111v3 shows up in network-admin?
Cheers, Mike

---

