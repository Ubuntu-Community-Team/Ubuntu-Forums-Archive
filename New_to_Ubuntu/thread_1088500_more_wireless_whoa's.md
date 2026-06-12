---
title: "more wireless whoa's"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by Scooter1962 on 2009-03-06
OK, I;m done.

I've tried to do this myself using the help files on ubuntu 8.10, which are excellent, but despite many hours of work, I CANNOT CONNECT MY WIRELESS.

To keep it brief - 
new toshiba laptop, 3 weeks old, Vista works fine, fully connected to the new Belkin Wireless router. 

One strange thing, before the router went in, Ubuntu worked fine (plug n' play) on my Motorola Surfboard cable modem - now it will not.

Cannot connect wireless or wired - so cannot download ndiswrapper
Cannot read E: drive from terminal - so cannot load tarballs or any other program updates to allow tools for wireless help

Cannot read CD from Software Sources or synaptic manager

My last attempt before this thread was using terminal to load ndiswrapper from a CD, it all looked good until:
Media change: please insert disk labelled
'ubuntu 8.10 _Intrepid Ibex_ etc.....

did this, and the CD won't load - yet another brick wall in the wireless loop.

I love the ubuntu philosophy and want to take part in this great idea, but with out an internet connection, its good bye from me.

---

### Post by redseventyseven on 2009-03-06
What's the make and model number of your Wireless router?

---

### Post by Scooter1962 on 2009-03-06
router is a Belkin Wireless G router - 2.4 Ghz 802.11g

---

### Post by st33med on 2009-03-06
You can remove the CD dependency.  System -> Administration -> Software Sources. Input your password, and uncheck the Cdrom on the Ubuntu Software tab. Then hit close.

---

### Post by Scooter1962 on 2009-03-06
This action takes away the packages for networking in the synaptic package manager. 
What I need to be able to do is 'download' or unpack ndiswrapper from a disk or usb stick. 
The system just won't read the via the package manager, the cd is readable in other states.

---

### Post by sneeks on 2009-03-06
can u not connect via cable for the time being and d/l updates and stuff and see if that helps?

---

### Post by Scooter1962 on 2009-03-06
Believe me, I've tried it all.

Wired does at least recognise the Modem, but won't connect. I'm not experience enough to work out the detail of how to modify the settings - though I have tried every combination in the Network manager.

Now here is something really interesting - I have put the live cd on my desktop computer, (running as the live cd, not installed) and I can connect with no problems.

When I first put Hardy Heron on the laptop, pre wireless router, it also connected with no problems.

Have also tried to add the Belkin CD installation as a third party repository, won't read the CD.  Seems to be some other program blocking it?

---

