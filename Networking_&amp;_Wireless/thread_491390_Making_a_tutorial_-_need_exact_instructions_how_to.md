---
title: "Making a tutorial - need exact instructions how to get rtl8187 working"
date: 2007-07-03
forum: Networking &amp; Wireless
---

### Post by kevdog on 2007-07-03
High Im making a tutorial for others, so I'm asking around in the forum for people that have cards with chipsets that are not available to be.

So far I have the broadcom, ndiswrapper, serialmonkey drivers pretty much explained.  My problem now is trying to figure out how to write a tutorial for the rtl8187 drivers.  

I know this much already
1. I know they are blacklisted by default so the blacklist file needs to altered to unblacklist the drivers
2. I am aware of the bug with these drivers, however thought this was pretty much solved by adding an extra character such as an x to the essid.

Beyond these two things however, I thought these drivers would work without any more modification.  Am I wrong in assuming this?

Do any further modifications need to be made to the /etc/network/interfaces file to get these working (such as those needed for ra drivers)?

Any known conflict with these drivers and network manager?

Thanks, if I had a wireless card with this chipset I would just try it myself.

One more -- is there any need or reason to download a more recent version of the driver? If yes, where would I get this or is this pretty much card specific??

---

### Post by panurge77 on 2007-07-05
1- the driver is not blacklisted by default. they were blacklisted in alpha releases but are now enabled by default

2- realtek drivers and ubuntu dont like each other. i have had problems with this couple since rtl8180. the native drivers would work for browsing but freeze the kernel on high traffic. 8187 drivers wont freeze the kernel, but they still drop the connection on high traffic like p2p.  shame on them.

3- best way to go is disable native driver and network manager and go back to ndiswrapper and /etc/network/interfaces

> 
2. I am aware of the bug with these drivers, however thought this was pretty much solved by adding an extra character such as an x to the essid.

What bug is that? Would it fix the connection dropping problem?

A trick I learned from rtl8180 is you had to set key before essid in the interfaces file when using ndiswrapper. maybe this is still needed in 8187, i set it like that from the start and did not check the other way

---

### Post by kevdog on 2007-07-05
The bug was specifically that it wouldnt take the essid name without adding a "bogus" character onto the end of the real name.  Because I havent had the chance to use the newest driver, I dont know if this has been solved.

From what you are telling me, it sounds like you recommend scrap the builtin drivers and go the route of ndiswrapper.  I dont have any problem with this.  Where do you recommend however getting for example the rt8187 driver??  Is it best with the XP driver or Win98 or some other driver?

Again Im trying to be as thorough as possible so the more specifics and examples you give me, would really help me out!

---

### Post by panurge77 on 2007-07-05
I've read from many post that old 98 drivers are the only ones that work. Now when I was testing different drivers none of them would work with network manager. When I disabled network manager and installed the 98 driver from the mobo cd (p5w dh), it worked. Maybe other versions of the drivers would work.. I guess network manager was the major problem, but I had not really checked them after disabling NetM

Anyway, I can post the driver somewhere for you...
Check your PM box

---

### Post by panurge77 on 2007-07-05
> Stop network manager

sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop

Create two files with only the word 'exit' in them. These files are:

/etc/default/NetworkManager
/etc/default/NetworkManagerDispatcher

From here: [https://help.ubuntu.com/community/Wi...NetworkManager](https://help.ubuntu.com/community/Wi...NetworkManager)

Then just edit /etc/network/interfaces as it was on previous ubuntu releases. I use the passkey before the essid on the interfaces file because it was needed on RTL8180. I dont know if it's needed for the 8187 too.

---

### Post by alex77 on 2007-07-16
Heya Kevdog, 

You have no idea how happy I am to hear that you are making a tutorial  on how to get rtl8187 working!

I have been stuck for months trying to get WPA to work with no success :(

Where will I be able to find your tutorial when you're done?

Thanks :)

---

