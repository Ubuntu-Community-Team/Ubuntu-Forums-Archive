---
title: "Installing software ( driver ) via cd  or usb"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by bcash977 on 2010-06-13
hey guys, im like newb of newb in ubuntu , i installed it via my win 7 and hats off, its so slick and smooth . Cant describe with words. 

The reason i choose to run ubuntu at my machine because there is some nice beat making software and i wanted to try that out. 

my first problem, i have a Wireless - G USB Adapter Wusb54gc not to be confused with Wusb54g 

[http://homesupport.cisco.com/en-us/wireless/lbc/WUSB54GC/download](http://homesupport.cisco.com/en-us/wireless/lbc/WUSB54GC/download)

this is the one 

how do i install driver for it in ubuntu ? i found some old thread and i couldn't figure out, any latest medium 
?

i have the cd but seems like i cannt install from there 

After i get internet there i can figure out easily i guess, looking it up in win 7 and then going to ubuntu has been a hassle lol

---

### Post by crowderd on 2010-06-13
bcash,
      Ubuntu is usually made to work with all the hardware for you computer. Typically you do not have to install drivers. I assume you had the connection with Windows working great. What you need to do is hard wire the ethernet cord into your computer and it should connect to eth0 once it says connected you need to go to SYSTEM -> ADMINISTRATION -> HARDWARE DRIVERS. A window should come up with a wireless driver and all you have to do is enable or install it. Remove the ethernet cord and restart your computer you should be able to see your connections once this is done.

---

### Post by anewguy on 2010-06-13
> **crowderd said:**
> bcash,
      Ubuntu is usually made to work with all the hardware for you computer. Typically you do not have to install drivers. I assume you had the connection with Windows working great. What you need to do is hard wire the ethernet cord into your computer and it should connect to eth0 once it says connected you need to go to SYSTEM -> ADMINISTRATION -> HARDWARE DRIVERS. A window should come up with a wireless driver and all you have to do is enable or install it. Remove the ethernet cord and restart your computer you should be able to see your connections once this is done.

It seems we usually have them do an update first, so, *if* the original poster can hook their computer to the router via a hardwire temporarily, the syntax would be:

- open a terminal window (Applications/Accessories/Terminal)

- type:

sudo apt-get update <press enter>

- close the terminal window

Check under System/Administration/Hardware Drivers and see it there is a restricted driver showing.  If so, and if it is not enabled, enabled it and reboot and disconnect the hard-wire cable.

If, however, you are not able to hard-wire a connection, or if a restricted driver doesn't show, post back and we'll go from there.

Dave ;)

---

### Post by anewguy on 2010-06-13
I also found this thread on getting this working, and it includes updates that appear to apply to 10.04:

[http://ubuntuforums.org/showthread.php?t=1353044]("http://ubuntuforums.org/showthread.php?t=1353044")

Please let us know if you have any questions.

Good luck!
Dave ;)

---

### Post by bcash977 on 2010-06-13
well i installed the latest version of ubuntu yesterday , i cannot bring internet cable to my room, my other pc is in another oom

---

### Post by Mark Phelps on 2010-06-13
Just so you know, the SW and drivers on the CD that came with the device are for MS Windows -- not for Ubuntu.  So, basically, you can't use them.

There is another option known as NDISWrapper -- which I'm sure folks will get into in some detail.

---

### Post by bcash977 on 2010-06-13
yea i figured that , well i really want to try out Ubuntu , ill try some stuff and try n see if i can figure out some way , i read that thread  , tried it  and got lost within 10 mins , pretty hard for a newb to follow all the stuff

---

### Post by anewguy on 2010-06-13
If you want to try ndiswrapper, let me know.  We can have you trying it in just a few minutes with step-by-step instructions.

Dave ;)

---

### Post by bcash977 on 2010-06-15
yea i will like to try that , please instruct me

---

### Post by anewguy on 2010-06-15
Okay, the first thing you need are the Windows XP driver files - the .sys and .inf files.  Copy those to your Ubuntu desktop.

The next step is dependent on whether or not you can get a wired internet connection:

**

If you can get a wired internet connection:

- open Synaptic Packabe Manager (System/Administration/Synpatic Package Manager)

- use "ndis" as a search string

- be sure the packages for ndisgtk, ndiswrapper common and ndiswrapper utilities are marked for installation

- click apply

**

If you cannot get a wired internet connection:

- insert the LiveCD you installed from

- if a message comes up about a CD with packages has been found just cancel it

- using "Places", open the CD

- navigate to the pool/main/n folder.  You should see to folders there - one for ndisgtk and the other for ndiswrapper.

- navigate to the ndiswrapper folder

- click on the ndiswrapper common file to start installing it

- when that finishes, click on the ndiswrapper utilities file to start installing it

- when that finishes, navigate back to the pool/main/n folder

- navigate to the ndisgtk folder

- click on the file there to install ndisgtk


**


Now to continue with common tasks:

- start up ndisgtk via System/Administration/Windows Wireless Drivers

- if anything shows - delete it

- click the add

- point it to the driver .inf file on your desktop

- right click on the network manager icon and be sure "Enable Wireless" is clicked

- now check to see if you can see wireless networks

Dave ;)

---

