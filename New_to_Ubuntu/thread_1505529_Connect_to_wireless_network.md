---
title: "Connect to wireless network"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by Luke359 on 2010-06-09
Hi, i just used wubi to install the latest ubuntu alongside my windows 7. In windows 7 i can click the network thing on the taskbar and it brings up my wireless router. 

I searched on youtube for an instructional video and it shows to do pretty much the same thing on ubuntu but when i try and do it my wireless network does not show up.

Any help please?

---

### Post by SlidingHorn on 2010-06-09
> **Luke359 said:**
> Hi, i just used wubi to install the latest ubuntu alongside my windows 7. In windows 7 i can click the network thing on the taskbar and it brings up my wireless router. 

I searched on youtube for an instructional video and it shows to do pretty much the same thing on ubuntu but when i try and do it my wireless network does not show up.

Any help please?

Ubuntu (linux systems in general) can be a little tricky when it comes to wireless connections.  If you could give us some additional information, it will be helpful for us to solve the problem.  Take a look [here]("http://ubuntuforums.org/showthread.php?p=6183681") to see what kinds of info to post to make it easier to get this going for you...

---

### Post by Luke359 on 2010-06-09
My laptop is HP 6735s The router is a belkin 54g  Security type: WPA-Personal Encryption type: TKIP  Ubuntu version: ubuntu-10.04-desktop-i386  Most of those commands need to be done whilst on ubuntu but seeing as though i cant even find the network i wouldnt be able to get information for it.

---

### Post by SlidingHorn on 2010-06-09
well the commands have to be done in ubuntu, but no network is required...you can maybe save the output in a text document and email it (can you connect via a wired network?), or throw it on a flash drive and post from windows?

It's hard to diagnose the problem without knowing what your card & chipset are.

---

### Post by Luke359 on 2010-06-09
> **SlidingHorn said:**
> well the commands have to be done in ubuntu, but no network is required...you can maybe save the output in a text document and email it (can you connect via a wired network?), or throw it on a flash drive and post from windows?

It's hard to diagnose the problem without knowing what your card & chipset are.

[http://www.pastie.org/997940](http://www.pastie.org/997940) There you go. I did most of the things in that link you sent in your first post.

---

### Post by SlidingHorn on 2010-06-09
link seems to be bad... 503 error

---

### Post by Luke359 on 2010-06-09
> **SlidingHorn said:**
> link seems to be bad... 503 error

weird, it is working for me.

Here is a mirror:
[http://pastebin.com/3uR4QTtE](http://pastebin.com/3uR4QTtE)

---

### Post by anewguy on 2010-06-09
Here's why it's not working:  you have the Broadcom 4316 wireless adapter and, just like Windows, it requires a driver.  EDIT: note that in the log it fails on the BCM wireless because it can't load the firmware.  Some would say to use the firmware cutter, but the below 2 choices are easier:

There are 2 ways I know of to install the driver:

(1) Use the restricted driver

(2) Use ndiswrapper to use the Windows drivers in Linux

The preferable way is to use the restricted driver, but here's the catch:  you must be able to connect to the net - so if you can hard-wire your computer temporarily to the net let us know.

If you can't, it gets a little more involved.  Start by finding the Windows drivers for your card - should be something like bcmwla5.sys and inf - I don't remember the exact spelling but it will be something along those lines.

Let us know if you can hard-wire temporarily or if we need to use the Windows drivers.

We will provide more instructions after we know that.

Dave ;)

---

### Post by Luke359 on 2010-06-09
Ok, i think i can. give me 5 - 10 minutes. I'll have to change some of the main computers wires around

---

### Post by SlidingHorn on 2010-06-09
Have a look here: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

The readme in the zip file has pretty detailed instructions.  If you still have problems afterward, let us know :)

---

### Post by Luke359 on 2010-06-09
> **anewguy said:**
> Here's why it's not working:  you have the Broadcom 4316 wireless adapter and, just like Windows, it requires a driver.  EDIT: note that in the log it fails on the BCM wireless because it can't load the firmware.  Some would say to use the firmware cutter, but the below 2 choices are easier:

There are 2 ways I know of to install the driver:

(1) Use the restricted driver

(2) Use ndiswrapper to use the Windows drivers in Linux

The preferable way is to use the restricted driver, but here's the catch:  you must be able to connect to the net - so if you can hard-wire your computer temporarily to the net let us know.

If you can't, it gets a little more involved.  Start by finding the Windows drivers for your card - should be something like bcmwla5.sys and inf - I don't remember the exact spelling but it will be something along those lines.

Let us know if you can hard-wire temporarily or if we need to use the Windows drivers.

We will provide more instructions after we know that.

Dave ;)

> **Luke359 said:**
> Ok, i think i can. give me 5 - 10 minutes. I'll have to change some of the main computers wires around

I couldnt get it to connect to the internet via the cable. I will try the Readme thing posted just before this post. If i cant get it to work i will come back.

---

### Post by anewguy on 2010-06-09
Once you are connected to the net via a hard-wired connection, do the following:

- open a terminal window (Applications/Accessories/Terminal)

- type:

sudo apt-get update <press enter>

sudo apt-get upgrade <press enter>

exit <press enter> This will return you to the desktop.

Once back at the desktop do the following:

- go to System/Administration/Hardware Drivers

- does it show a driver there?  If not, post back here and don't go any further on this post.

- be sure to enable the driver it shows

- disconnect your hard-wire cable from your computer

- wait a couple of minutes (or just reboot)

- check in network manager to be sure "Enable Wireless" is checked

- do you see any networks now?

Dave ;)

---

### Post by Luke359 on 2010-06-09
OK, so i attempted to go through that walkthrough thing i downloaded on the previous page but i didnt really know what i was doing so i thought it best to stop before i break something.

I'll try again to get it connected through a wire and then follow your instructions.

---

### Post by anewguy on 2010-06-09
If you can't use a hard-wired connection, first get your Windows driver (the .sys file should be in windows/system32/drivers and the .inf may be in windows/system32).  Copy these 2 files to a flash drive or some other portable media.

Boot Ubuntu.

Copy the driver files to your desktop.

Put in the LiveCD you install from.  When the window opens telling you that it contains software packages just close that window.

Your LiveCD should show on the desktop now.  If it's not open to explore, click on "Places" and then on your CD.

Navigate to the pool/main/n folder.  There you should see a folder for ndiswrapper.  Click on the folder to open it.  You should see 2 files - one for ndiswrapper common, the other for ndiswrapper utilities.  Double-click on the common one first to start its installation.  When the installation finishes, double-click on the utilites on to install it.

Once the above 2 installations are complete, navigate back a level in the folder tree to pool/main/n again.

You should see a folder for ndisgtk.  Click on the folder to open it.  There you will find a single file for ndisgtk.  Double-click on it to install it.

Once ndisgtk has finished installing you can close the explore window and then eject your CD.

Start up ndisgtk via System/Administration/Windows Wireless Drivers.

If any connections are listed there remove them first.

Now just add and point it to the driver files on your desktop.

Remove the CD, and just for the heck of it reboot Ubuntu.

Now check your wireless.

Dave ;)

---

### Post by Luke359 on 2010-06-09
> **anewguy said:**
> If you can't use a hard-wired connection, first get your Windows driver (the .sys file should be in windows/system32/drivers and the .inf may be in windows/system32).  Copy these 2 files to a flash drive or some other portable media.

Boot Ubuntu.

Copy the driver files to your desktop.

Put in the LiveCD you install from.  When the window opens telling you that it contains software packages just close that window.

Your LiveCD should show on the desktop now.  If it's not open to explore, click on "Places" and then on your CD.

Navigate to the pool/main/n folder.  There you should see a folder for ndiswrapper.  Click on the folder to open it.  You should see 2 files - one for ndiswrapper common, the other for ndiswrapper utilities.  Double-click on the common one first to start its installation.  When the installation finishes, double-click on the utilites on to install it.

Once the above 2 installations are complete, navigate back a level in the folder tree to pool/main/n again.

You should see a folder for ndisgtk.  Click on the folder to open it.  There you will find a single file for ndisgtk.  Double-click on it to install it.

Once ndisgtk has finished installing you can close the explore window and then eject your CD.

Start up ndisgtk via System/Administration/Windows Wireless Drivers.

If any connections are listed there remove them first.

Now just add and point it to the driver files on your desktop.

Remove the CD, and just for the heck of it reboot Ubuntu.

Now check your wireless.

Dave ;)

I didn't use a LiveCD, i used wubi to just install it alongside windows 7. To create the liveCD would i just burn the .iso file of ubuntu to a CD?

If so then i'll have to do this next week when i return home.

Thanks for all the help :). Is there a karma button i can press some where?

I will mark the thread as solved when i have actually gotten it to work.

---

