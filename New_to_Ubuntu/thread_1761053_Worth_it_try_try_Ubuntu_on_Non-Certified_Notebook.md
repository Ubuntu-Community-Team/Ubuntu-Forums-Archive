---
title: "Worth it try try Ubuntu on Non-Certified Notebook?"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by Griegfan on 2011-05-17
Greetings:
I have an older notebook I use for business purposes (HP Pavilion zv6000 or zv6100). It came with Windows XP Home Edition (OEM).  The hard drive crashed and I installed a new one.  

I re-installed the OS, but have been thinking of replacing it with Ubuntu.  

I looked at [http://www.ubuntu.com/certification/make/HP](http://www.ubuntu.com/certification/make/HP) and saw that my notebook is not "certified."  

Off the top of my head, I think I only need drivers for the following:
(1) WiFi (Internet)
(2) Audio
(3) Internal DVD Player
(4) Hi-Speed USB 4-Port CardBus (this was a plug and play device I bought and installed seamlessly)

To make the above 4 items work, am I on a fool's errand and better off just sticking with what has worked in the past?

I would really like to use Ubuntu, but I am not a technician and am afraid of getting entangled in hours of researching and experimenting and tinkering.  

Thank you for reading.

---

### Post by sanguinoso on 2011-05-17
If you are concerned with it not working immediately after a fresh install I wouldn't try it. Its possible that you would have to manually install drivers for the ones you listed and on a business machine that might not be a great idea. I'd recommend trying Ubuntu out in a VM or on a personal machine first.

---

### Post by IWantFroyo on 2011-05-17
> **sanguinoso said:**
> I'd recommend trying Ubuntu out in a VM or on a personal machine first.

I second the good old Virtual Machine.
If it works, it will almost certainly work on a full install.

As for the compatibility list, I'm not certain whether it means there are open source drivers available or it just doesn't work. It's worth a try anyways.

---

### Post by Griegfan on 2011-05-17
Thank you both for your replies.  Installing on a personal machine is a good idea, but I want to know if it will work on this particular notebook.  Even though the notebook is for business purposes, I am essentially starting from scratch with this new hard drive, so if things don't work out I could just re-install XP.  

My needs are EXTREMELY basic.  For example, if I install Ubuntu, can I get a reliable wifi connection to the Internet?  Can I get audio? etc.

---

### Post by kaldor on 2011-05-17
Just try it on a Live USB or CD. If it works out of the box, it will work if you install it. If not, you might need to tweak a little but it shouldn't be hard on these forums to get assistance.

My laptop isn't on the certified list but everything worked without a hitch.

---

### Post by beew on 2011-05-17
Or you may install in an external hard drive, it is always the best iMO since it is a "real" install.

A live usb with persistence would be the next option, though it is kind of slow and restricted in size and doesn't support things like system or kernel updates (this is important for testing hardware because sometimes things only work after that kind of updates)

VM is probably a bad idea as you say it is an older machine and may not have enough power to run it and it may be very slow even if you can run it.

I agree that you shouldn't worry about certification since you are not buying a new computer. I have Ubuntu running beautifully on all the machines I have tested on  and none of them are certified. My main laptop is a Samsung and the bozos in their tech support  actually told me Linux would not run on it but here it is running flawlessly on Ubuntu 10.10, much faster than Windows 7 which came preinstalled (and I have since gotten rid of)

---

### Post by snowpine on 2011-05-17
Give it a try on Live CD/Live USB and you will know for sure.

Trying it in a Virtual Machine or on another computer will tell you nothing. :)

---

### Post by NormanFLinux on 2011-05-17
Live CD will let you know if you can connect to your Internet, if the video card is configured properly and so forth.

If it tests OK in live environment, it will probably work OK installed to the hard disk. In my case, I needed to update a broken kernel and now Natty runs smooth as silk!

---

### Post by wep940 on 2011-05-17
But.....if it doesn't seem right - perhaps video abnormalities or wireless not working, don't just write off ubuntu.  Some video requires drivers not included on the LiveCD, and some wireless drivers are restricted (i.e., not open source) so they can't be included on the LiveCD either.
 
Here's what I think your best bet is for now, before you try anything else:
 
- with Windows, check the device manager and see what type of video, sound and wireless adapters are installed.  Based on that, we can check to see if you will need additional drivers and instructions that we can provide before you try installing.
 
I say this only for 1 reason - a lot of people jump in, try the LiveCD or even an install, and haven't done their basic homework on what their hardware is.  The result is a system that maybe:
 
- boots only to the command line
- has low resolutions or unreadable screens in X windows
- has no sound
- wireless doesn't work
 
These things turn people off right away, and they remove ubuntu/linux.
 
So, while I dual-boot so I'm not an ubuntu purist, I'd like to see you have success with your laptop and not have any "bad taste left in your mouth" because of it.
 
Let us know, and we'll do our best to help!

---

### Post by beew on 2011-05-17
> **wep940 said:**
> But.....if it doesn't seem right - perhaps video  abnormalities or wireless not working, don't just write off ubuntu.   Some video requires drivers not included on the LiveCD, and some  wireless drivers are restricted (i.e., not open source) so they can't be  included on the LiveCD either.
 


That's why I recommend a full installation in an external hard drive and boot off it on the computer you intend to test. You can then install any driver and do all the tweaking and testing you want and it has the same performance as an install into the internal hard drive.

---

### Post by wep940 on 2011-05-17
And if you don't have an external drive, or the space to spare on an existing one.......
 
Is that better?  ;)

---

### Post by Griegfan on 2011-05-23
Thank you all for responding!  I installed Ubuntu.  It was fairly painless.  However, I don't have WiFi as well as another item or so.  However, my first priority is to get WiFi working.

I ran this in terminal: sudo lspci

Here is a line that might provide important information:
03:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless Lan Controller (rev 03)

I googled that information and got results.  I may not have a choice but to go through those results until I find a solution.  However, I am humbly hoping that by posting here someone will know exactly what I must do so it will be reasonably painless.

If that's possible, I would love to hear from you!

Thank you for reading.

---

### Post by dFlyer on 2011-05-23
> **Griegfan said:**
> Thank you all for responding!  I installed Ubuntu.  It was fairly painless.  However, I don't have WiFi as well as another item or so.  However, my first priority is to get WiFi working.

I ran this in terminal: sudo lspci

Here is a line that might provide important information:
03:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless Lan Controller (rev 03)

I googled that information and got results.  I may not have a choice but to go through those results until I find a solution.  However, I am humbly hoping that by posting here someone will know exactly what I must do so it will be reasonably painless.

If that's possible, I would love to hear from you!

Thank you for reading.

Not sure if this will work on your system or not. I have the BCM4312. What I end up doing is starting synaptic and marking bcmwl-kernel-source for reinstallation, rebooting the computer and wifi works.

---

### Post by wildmanne39 on 2011-05-23
> **Griegfan said:**
> Greetings:
I have an older notebook I use for business purposes (HP Pavilion zv6000 or zv6100). It came with Windows XP Home Edition (OEM).  The hard drive crashed and I installed a new one.  

I re-installed the OS, but have been thinking of replacing it with Ubuntu.  

I looked at [http://www.ubuntu.com/certification/make/HP](http://www.ubuntu.com/certification/make/HP) and saw that my notebook is not "certified."  

Off the top of my head, I think I only need drivers for the following:
(1) WiFi (Internet)
(2) Audio
(3) Internal DVD Player
(4) Hi-Speed USB 4-Port CardBus (this was a plug and play device I bought and installed seamlessly)

To make the above 4 items work, am I on a fool's errand and better off just sticking with what has worked in the past?

I would really like to use Ubuntu, but I am not a technician and am afraid of getting entangled in hours of researching and experimenting and tinkering.  

Thank you for reading.
Hi, I have the same laptop and it works fine.:P

---

### Post by 3rdalbum on 2011-05-23
You might need to plug your computer into your modem/router with an Ethernet cable so you have an internet connection, then use the Synaptic Package Manager program to "reload" the package list, and then go into the Additional Drivers program and you should find something installable in there that allows you to enable your Broadcom wifi.

After doing this, after a reboot, you will be able to get a connection over wifi.

---

### Post by Griegfan on 2011-05-31
> **Griegfan said:**
> Thank you all for responding!  I installed Ubuntu.  It was fairly painless.  However, I don't have WiFi as well as another item or so.  However, my first priority is to get WiFi working.

I ran this in terminal: sudo lspci

Here is a line that might provide important information:
03:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless Lan Controller (rev 03)

I googled that information and got results.  I may not have a choice but to go through those results until I find a solution.  However, I am humbly hoping that by posting here someone will know exactly what I must do so it will be reasonably painless.

If that's possible, I would love to hear from you!

Thank you for reading.

Once again, thank you for the responses.

I got Internet access on the notebook via a cable connection.  I went into Synaptic Package Manager.  I don't recall for certain what I did, but I think I clicked the “Reload” button. 

From the “Quick filter”field I typed in “bcm4306” and got these two items:

firmware-b43-installer
firmware-b43legacy-installer

Questions:

I haven't gone any further than this.  Will installing one (or both) of these items do the trick?  

Since I'm using the notebook for business purposes, are there any licensing issues I need to consider if I install one or both of those items?

By clicking the “Reload” button in Synaptic Package Manager, what exactly did I do?

Thank you.
Griegfan

---

### Post by wildmanne39 on 2011-05-31
> **Griegfan said:**
> Once again, thank you for the responses.

I got Internet access on the notebook via a cable connection.  I went into Synaptic Package Manager.  I don't recall for certain what I did, but I think I clicked the “Reload” button. 

From the “Quick filter”field I typed in “bcm4306” and got these two items:

firmware-b43-installer
firmware-b43legacy-installer

Questions:

I haven't gone any further than this.  Will installing one (or both) of these items do the trick?  

Since I'm using the notebook for business purposes, are there any licensing issues I need to consider if I install one or both of those items?

By clicking the “Reload” button in Synaptic Package Manager, what exactly did I do?

Thank you.
Griegfan

Hi, go into if you are using natty go into the apps by clicking on it in the launcher then in the search type additional drivers, click on it and there should be the driver you need then click on it when it is done installing restart then enter your password to connect to your network. If you are using an older version of ubuntu go to admin click on restricted drivers follow the same instructions as above.

---

### Post by Griegfan on 2011-05-31
Hello Wildmanne39:
Thank you for replying.  I did this:
Applications > Additional Drivers

A dialog titled, "Additional Drivers" came up with the message, "Searching for Available Drivers..."  

The next dialog had as its title, "No proprietary drives are in use on this system."  

There appeared to be an option to install a "software modem, " but this doesn't seem to be what I'm looking for.  Have I missed anything?

Griegfan

---

