---
title: "Don't WORK! Dell Latitude D600 With Broadcom wireless card..."
date: 2008-06-10
forum: Networking &amp; Wireless
---

### Post by saggitheman on 2008-06-10
I have a Dell Latitude D600 with Broadcom Wireless network... But i can't get it to work! I cant even see what networks who's around me! Anyone know what to do? Pleas answer in a easy way! I'm a new Linux (Ubuntu 8.04) user...

---

### Post by Ayuthia on 2008-06-10
> **saggitheman said:**
> I have a Dell Latitude D600 with Broadcom Wireless network... But i can't get it to work! I cant even see what networks who's around me! Anyone know what to do? Pleas answer in a easy way! I'm a new Linux (Ubuntu 8.04) user...

Can you post the results of lspci -nn.  You will need to open the Terminal and enter this command.  It will help us figure out your wireless card.

---

### Post by saggitheman on 2008-06-11
What is that? lspci -nn.?? Were do i find it?

---

### Post by Milardo on 2008-06-11
I would try this-using hardy,open synaptic manager and make sure you check the cd option so it can install stuff from cd, search for ndis and install all those ndis that come up in the search. After installing them in adminstration go to windows wireless drivers. Have your 3 or 2 files from the linksys cd or the one from linksys website. The .cat, .sys, and .inf files. Install new driver the .inf file and next go to the top right icon that looks like a computer monitor. Right click the iconand make sure network and wireless are checked. Next left click it and click the option that is search or find new wireless network not the create or manual option. Now you can enter your wireless security settings and you can easily choose wpa/wpa 2 as well. It should connect pretty fast. I got high speeds as well. To disconnect and unplug adapter (if that is what you have) just uncheck wireless from the icon and then pull out the adapter. To connect to the same wireless network you just have to plug it back in and check wireless if not already checked. You should be connected in about 50 seconds or so. This worked for my linksys wusb54gc.

---

### Post by Ayuthia on 2008-06-11
> **saggitheman said:**
> What is that? lspci -nn.?? Were do i find it?The Terminal is an application that you run that will get you to something that looks like the DOS command line.  You will need to type lspci -nn and press enter.  This command will list out your PCI cards so that we can identify your wireless card.

You can also try installing the application attached in the first post of this thread:
[http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)
When you run the application, it will display your wireless card at the bottom of the window.

---

### Post by saggitheman on 2008-06-12
I tryed to type Ispci -nn in the terminal, but it didn't find something. Pleas Relay

---

### Post by Ayuthia on 2008-06-12
Let's go ahead and see if we can activate the card by using the Hardware Drivers application.  If you have a working internet connection, run System->Administration->Hardware Drivers.  If you see an option for Broadcom, enable it.  It should install the firmware for you.

---

