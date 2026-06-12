---
title: "How do you install applications on a Palm Treo 650?"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by tahitiwibble on 2009-04-14
I must be going daft but I can't for the life of me figure out how to install my old Palm applications on my brand new old Treo 650. The last time I had to do this was on Windows and it couldn't have been easier.

I am using Evolution to synch the contacts etc. to and this is functioning correctly. I tried just putting a .prc file into the MyPDA folder in the /home folder and nothing happens.

Help would be very much appreciated.

---

### Post by tahitiwibble on 2009-04-16
Is there anybody out there today that knows?

---

### Post by fenian on 2009-04-16
You can use JPilot (its in the repos) or there is also a panel applet (right click on a panel and choose Add to Panel and select the Pilot Applet) to sync Palm Apps.

---

### Post by tahitiwibble on 2009-04-16
> **fenian said:**
> You can use JPilot (its in the repos) or there is also a panel applet (right click on a panel and choose Add to Panel and select the Pilot Applet) to sync Palm Apps.

fenian, thanks for that. I saw J-Pilot but can't work out how to set it up :(

Do you know where to put the Palm OS apps so that they'll be installed when syncing with the Pilot Applet?

---

### Post by fenian on 2009-04-21
After you install Jpilot you can start it from the Aplications>Office menu 
First you will need to set it to the correct port (USB,Serial,etc....) to connect to the palm,to do this...

Go to the File menu

Choose prefrences

Click the settings tab

In the 'Serial Port' pull down menu choose the port you connect the palm with (for my really old palm its /dev/ttyS0 )
For transfer rate I use 115200  (you may have to try a few before you get the right one.)

Next you need to Install User from  the File menu choose install user change the name to suit you and click the install button.

You then need to click the red and blue hot-synch button and the sych button on the palm.

It should set up the user on the palm.If not go back to the prefrences and try a different transfer rate.

After you set up the user you can add apps from the File menu...

Go to File>Install

Add the Apps to install

Click close

Hit the hot sych button in Jpilot,hit the synch button on the palm hit the close button in the Jpilot window.

---

### Post by tahitiwibble on 2009-04-25
Fenian, thanks a million! "Preferences" weren't nearly as bad as they looked at first, there was actually very little to configure. Everything works perfectly. Thanks again.

---

