---
title: "3rd Plea for help with no replies"
date: 2006-10-02
forum: Networking &amp; Wireless
---

### Post by spacecowboy706 on 2006-10-02
Somebody has to know how to fix this or I may have to go back to windows since this cat 5 cable ran from one end of the house to the other isn't gonna work as a permanent thing. This will be the third time i have posted in this forum asking for help on this subject.

I cannot figure out how to make my wireless pci card connect to the internet. I am using a wmp54g from linksys. I have already installed the ndisgtk, ndiswrapper-utils and just in case the ndiswrapper-source as I wasn't sure what all I needed and i have even found the correct driver that I need "I THINK"... BUT... when i go to SYSTEM - ADMINISTRATION - WINDOWS WIRELESS DRIVERS - and then Click on the "INSTALL NEW DRIVER" button i go to where i downloaded it to and i am given the following file:

rt2500-1.1.0-b4.tar.gz

so i then extracted it to the same directory and i am given this new file:

rt2500-1.1.0-b4

So i then go back to the Wireless Network Drivers window and click the "INSTALL NEW DRIVER" button again and locate the newly extracted file "rt2500-1.1.0-b4", but here is where my problem begins...

I cannot find any ".inf" file anywhere in the file...

Please tell me what i am doing wrong or if i even have the right driver downloaded, or if i am even going about this the right way? or if there is an easier way. 

I have posted about this twice before and in the first thread the guy who helped me just told me to use airsnort then never replied to any more of my posts... and in the second thread no one at all answered for 2 days...

---

### Post by mckemie on 2006-10-02
Well, since you are having a hard time getting real help, I offer this:
I just bought a pair of "homeplug" type "over AC wiring" adapters/bridges off of eBay for about $60.  Worked out of the box.  I was not able to get reliable wireless 50' and through a wall.  I had run a temporary 50' network cable through the doorway.  I plugged one homeplug adapter into an AC outlet near my "upstream" wireless router and connected to the router with a 7' cable.  Same on the other end: AC -> wireless router.

With troublesome PCMCIA wireless cards, I have found it most cost effective to just go out and find a Linux compatible model.  Maybe you don't have that option with a desktop.

---

### Post by tturrisi on 2006-10-02
If use ndiswrappern then you are using the wrong driver.  Ndiswrapper is supposed to use the WINDOWS driver, not a linux driver.  The windows driver for your card exists on your windows installation.  Copy it to a floppy, cd or other partition & then load it in linux.

---

### Post by harts12 on 2006-10-02
Also, I left a reply to Linksys WMP54G thread that will direct you to a site that might help...

---

### Post by spacecowboy706 on 2006-10-02
mckemie - thanks for the suggestion.. but thats not an option for me.

tturrisi - did as you suggested... but copied the drivers directly form the wireless cards disk... and the ndiswrapper program said the card was detected and then i clicked the configure network button and encountered the same "No Connectivity" when i tried to enable the wireless.

harts12 - no luck with your suggestionas well

---

### Post by haiku99 on 2006-10-03
the following writeup helped me get ndiswrapper working...
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
in my case using the current version was essential

---

