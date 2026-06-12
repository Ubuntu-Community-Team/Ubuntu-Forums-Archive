---
title: "Broadcom 802.11b/g WLAN issues on Maverick"
date: 2010-11-27
forum: New to Ubuntu
---

### Post by JoeLeeto on 2010-11-27
Howdy all :D

I'm really new to all of this, so, if you guys have any suggestions on what other info I should give you, I would (and I think yo would too) appreciate it. :)
I've installed Ubuntu 10.10 a week ago in my Acer Aspire 3680, and I immediately fell in love with it. The only really big/unsolvable problem I've come up with was the gorram wireless card, that wouldn't work at all. I've roamed the web a bit and found two possible solutions to my problem: NDIS Wrapped and MADWiFi. 
At first I tried MADWiFi, mainly because a friend recommended it, but I couldn't find a way of making it work on Maverick (50% of tutorials found were about Ubuntu 8 and 9, that wouldn't work, and the other 50% had broken links when I got to the "wget" part ;)). 
I proceeded to try NDIS Wrapped, but almost immediately I faced yet another problem: I had absolute no idea what .inf file I should have (and as I completely erased Windows from my HDD, I had no access to my old drivers), yet reaching another dead-end.
So, I ask you, o mighty forumers, help this poor noob access wireless internet!


For your information, I have an Acer Aspire 3680-2992 notebook, with an Intel Celeron M processor 440, and the Mobile Intel 940 GML Express chipset. I've got a 512MB RAM, but it's a DDR2, so I plan changing it soon. Any other information you need, just give a shout (and if possible, inform me where I can find that information, because I'm a total zero at this) and I will reply as soon as possible.

Thank you! (Long thread, wasn't it?)

---

### Post by sandyd on 2010-11-27
> **JoeLeeto said:**
> Howdy all :D

I'm really new to all of this, so, if you guys have any suggestions on what other info I should give you, I would (and I think yo would too) appreciate it. :)
I've installed Ubuntu 10.10 a week ago in my Acer Aspire 3680, and I immediately fell in love with it. The only really big/unsolvable problem I've come up with was the gorram wireless card, that wouldn't work at all. I've roamed the web a bit and found two possible solutions to my problem: NDIS Wrapped and MADWiFi. 
At first I tried MADWiFi, mainly because a friend recommended it, but I couldn't find a way of making it work on Maverick (50% of tutorials found were about Ubuntu 8 and 9, that wouldn't work, and the other 50% had broken links when I got to the "wget" part ;)). 
I proceeded to try NDIS Wrapped, but almost immediately I faced yet another problem: I had absolute no idea what .inf file I should have (and as I completely erased Windows from my HDD, I had no access to my old drivers), yet reaching another dead-end.
So, I ask you, o mighty forumers, help this poor noob access wireless internet!


For your information, I have an Acer Aspire 3680-2992 notebook, with an Intel Celeron M processor 440, and the Mobile Intel 940 GML Express chipset. I've got a 512MB RAM, but it's a DDR2, so I plan changing it soon. Any other information you need, just give a shout (and if possible, inform me where I can find that information, because I'm a total zero at this) and I will reply as soon as possible.

Thank you! (Long thread, wasn't it?)

```

sudo apt-get install bcm43xx-fwcutter
```
and if that doesn't work, heres the inf files

[http://drivers.softpedia.com/get/NETWORK-CARD/Broadcom/Broadcom-BCM943XX-Driver-4-102-15-56-whql.shtml](http://drivers.softpedia.com/get/NETWORK-CARD/Broadcom/Broadcom-BCM943XX-Driver-4-102-15-56-whql.shtml)

---

### Post by PRC09 on 2010-11-27
The first step would be to see which wireless card is in your laptop and then check for which drivers apply.According to your laptop specs it should be an Atheros  wireless which wont work with a Broadcom(bcm43xx) driver.




[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by anewguy on 2010-11-27
> **sandyd said:**
> ```

sudo apt-get install bcm43xx-fwcutter
```
and if that doesn't work, heres the inf files

[http://drivers.softpedia.com/get/NETWORK-CARD/Broadcom/Broadcom-BCM943XX-Driver-4-102-15-56-whql.shtml](http://drivers.softpedia.com/get/NETWORK-CARD/Broadcom/Broadcom-BCM943XX-Driver-4-102-15-56-whql.shtml)

But.....you need to be connected to the net.  So, if you can't hardwire a connection to your router, then do the following:

- after ubuntu is booted, load up the LiveCD (or USB flash drive if you went that route to install)

- using "Places", navigate to the /pool/main/b folder and you'll see the folder for the firmware cutter.  Navigate to that folder and double-click on the file to begin installation.  It will ask for a password - use your normal password, it just won't show on the screen.


We all need to remember that there are a lot of people who do not have access to a hardwire connection, so without wireless working they can't do things like sudo apt-get.  For these types of instances, the firmware cutter, ndiswrapper and ndisgtk (the GUI'd front-end to ndiswrapper -> use it, you'll be glad you did!) are all included on the LiveCD.

- firmware cutter in /pool/main/b

- ndiswrapper and ndisgtk in /pool/main/n (remember to install ndiswrapper common, then ndiswrapper utilities and then ndisgtk).  Ndisgtk is accessed via System/Administration/Windows Wireless Drivers and takes the place of trying to enter tons of stuff into the command line.

Also keep in mind - there are a lot of posts out there that are outdated now.  There is no need to download the ndiswrapper source and compile it as some old post recommend.  Use ndisgtk instead of typing in a bunch of ndiswrapper commands, modprobe's, etc. in the command line, and remember that the old blacklist file, /etc/modprobe.d/blacklist, was renamed to /etc/modprobe.d/blacklist.conf quite a while ago.  Old posts still make reference to either editing or echoing lines in the old blacklist file, and this will no longer work.

Dave ;)

---

### Post by JoeLeeto on 2010-11-27
Thank you everyone that answered! 

The terminal thingie didn't work, but the inf file did the trick, thankyall :D

---

### Post by JoeLeeto on 2010-11-28
The inf file did the trick, but only until I turned my notebook off, when I tuned it on again it wouldn't locate the wireless connection again. Any clues on what to do?

---

### Post by anewguy on 2010-11-28
I'm going to assume you used ndiswrapper manually, that being typing things in at the command line.  What you probably didn't do was add it to the modules file so it is loaded at boot:

sudo gedit /etc/modules

add a line to the end that simply says:

ndiswrapper

save the file and exit

reboot

Please, for future reference, and for others who might be following this thread looking for help, install ndisgtk when you install ndiswrapper (both can be installed from the LiveCD in /pool/main/n/ndiswrapper and /pool/main/n/ndisgtk).  Ndisgtk is a GUI'd front end to ndiswrapper and takes away all of the command line typing and things like editing the modules file.  You simply start up ndisgtk via System/Administration/Windows Wireless Drivers, click on "new" and point it to the .inf file for your driver files.  That's it - it does the rest.

Dave ;)

---

### Post by JoeLeeto on 2010-11-30
Okay, now you got me worried: I didn't type anything in the command line, I went to the "Windows Wireless Drivers" tab that appeared after I downloaded NDIS Wrapper through the Ubuntu Software thingo.

---

### Post by anewguy on 2010-11-30
Hummmmmm.....that would have done it all for you.  Please log in to a terminal session and check the /var/log/Xorg-0.log (I *think* that's what it's called).  See if there are error message in there, and if so, post them back here.

Also, while in the terminal session, type:

cat /etc/modules <press enter>

see if ndiswrapper is in that list - if not:

sudo echo ndiswrapper/n >> /etc/modules

then reboot.

EDIT:  Also try sudo modprobe ndiswrapper then wait a couple of minutes and see if wireless is working.

Would also like to see the output of  cat /etc/modprobe.d/blacklist.conf


Dave ;)

---

### Post by JoeLeeto on 2010-12-01
Ok, cat /etc/modprobe.d/blacklist.conf brought this:
```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

```

Couldn't find the /var/log/Xorg-0.log thing though.

When I typed sudo modprobe ndiswrapper, this message showed up:

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

Is it important?

---

### Post by anewguy on 2010-12-01
Don't worry about the message from when you modprobe'd ndiswrapper.  After you did that, did your wireless come up?

Dave ;)

---

### Post by JoeLeeto on 2010-12-01
Eeer, no? Well, anyways, should something different come up on the Drivers page? Or anything? Do I have to activate the Broadcom STA wireless driver? Or it must be off to work?

---

### Post by anewguy on 2010-12-01
You would be fighting a losing battle trying to use ndiswrapper/ndisgtk and using the restricted driver as well.  If the STA driver shows in System/Administration/Additional Drivers, then I would strongly suggest using it.  To do, some things have to be backed out:

- open a terminal window (Applications/Accessories/Terminal)

- type:

sudo ndiswrapper -l <press enter> Where that's a lower case "L" for "list".

For each device returned above:

sudo ndiswrapper -e xxxxxx <press enter> Where xxxxxx is the device returned above

Repeat this until nothing is returned in a list.

- try activating the STA driver.  I noticed some of the Broadcom stuff is in your blacklist.conf file, so I don't know if any of those would affect the STA driver or not.

It would also probably be wise to remove ndiswrapper and ndisgtk for now - remove them via Synaptic Package Manager.

You also want to check the /etc/modules file.  If ndiswrapper shows in that file, delete the line containing it.

Just for fun, reboot, then try the wireless again. (The reboot will sort of clear everything out so you are starting on the latest updates to the modules file and using the STA driver).

Post back if you have any problems or questions, and also let us know if this works for you or not.

Dave ;)

---

### Post by JoeLeeto on 2010-12-13
Sorry for taking so much time to answer, but I did what you told me and HOLY PLASTICVILLE it is working! Eternal kudos to you, sir Dave, knight of the new guys.

---

