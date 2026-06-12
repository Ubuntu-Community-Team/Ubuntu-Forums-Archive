---
title: "WUSB54G Trouble"
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by agentorannnge on 2007-08-21
Hello, I am having trouble with the Linksys WUSB54G USB network adapter. I am running Ubuntu 7.04 Feisty by the way. I tried looking at some other tutorials and I downloaded some drivers. I really need some specific instructions considering im not all that great with the terminal. I am posting this on my Laptop which has Ubuntu and im having trouble with my Desktop. When I go to System>Administration>Network I only see "Wired Connection" and "Modem Connection" but no Wireless. 

Can some give me a link to a tutorial or help me on a personal level. I can't seem to find a help topic concerning my problem exactly.

Thank you for bearing with my inability to use Ubuntu too good :)

{AgentOrannnge}

EDIT: I refreshed to see if anyone replied and noticed the stickies posted. I feel really dumb but will the WUSB54G setup guide for Dapper work with Feisty? If so is there any modification I will have to make note of because of the version difference?

---

### Post by wickstopher on 2007-08-21
I've had no trouble getting this device to work out of the box with Feisty with the native drivers.  Here's what I would recommend to try.  Let me know if it works for you.

- get rid of ndiswrapper and the drivers you had attempted to install for the device.

- plug in the device and restart your system (preferably turn your computer off, plug in the device, and then boot.  NEVER unplug and/or replug this device while the system is running...for some reason this causes all sorts of problems).

- go to System > Administration > Network and go to the properties of your Wireless connection.  Turn off "Roaming Mode" and manually enter the information for your wireless network.  This should get you going.

- I also have disabled the Network Manager "applet" from system > preferences > sessions, as it seems to inexplicably conflict with the base network manager and cause frequent disconnects, forcing me to deselect and reselect my wireless connection from System > Administration > Network with annoying frequency.  I don't know why, but it seems to work for me.  I'm getting 90% or better fewer disconnects since disabling this applet.  Anybody care to comment on this?

Let me know how this works out for you.

---

### Post by agentorannnge on 2007-08-21
I rebooted and went the System>Administration>Network and I didn't have a "Wireless Connection" option. Is there something I have to enable?

---

### Post by wickstopher on 2007-08-21
Did you remove ndiswrapper?  

if you installed ndiswrapper via Add/Remove Programs menu, you can uninstall it there.

If you installed it another way, and are having trouble removing it, repost here.

When configuring ndiswrapper, did you add any items to /etc/modprobe.d/blacklist (i.e. bcm43xx)?  If so, make sure you remove that item from your blacklist.  

```
gksudo gedit /etc/modprobe.d/blacklist
```

and remove the line
```
blacklist bcm43xx
```

Also, are you sure the device is functional?

---

### Post by agentorannnge on 2007-08-21
I have not configured ndiswrapper at all. I am fairly new to the linux scene. I installed Ubuntu and it did not recognize the USB device. This adapter was used with Windows for a long time and never posed a problem. If somehow this ndiswrapper file got removed or if it was configured incorrectly is there a way to get it back to normal?

---

### Post by wickstopher on 2007-08-22
Okay, I assumed that you had installed ndiswrapper, since you made mention of downloading drivers for the device.  What did you do with said drivers if you didn't have ndiswrapper installed?  Honestly, I'm not sure what is going on for you.  Like I said, the device worked fine for me as per the procedure I outlined (hopefully clearly enough).  Not sure why it wouldn't work for you (although Ubuntu, both 6.04 and 7.10, is the ONLY distribution I've ever been able to get it fully working in...not even Linux Mint Cassandra, which is supposedly based on Feisty).

---

### Post by wieman01 on 2007-08-22
The Sticky should work for you as well. If not, compile the latest version of "ndiswrapper" from source. That should definitely do. Then follow the guide.

If you happen to have a WUSB54G V4(!), then the chipset is a Ralink one. Get rid of the native Linux driver, it is only trouble. "ndiswrapper" is the way to go.

---

### Post by Roswellgrey on 2007-08-22
What version of WUSB54G do you have ?  

Have a look at the label on the bottom - if it is just says WUSB54G, then its a V1 - otherwise it will show WUSB54G V2, V3 etc .....

If its a V1, you definately need ndiswrapper  - there is no native support for a V1.  If this is the case, maybe Post #8 on this thread might help ...


[http://ubuntuforums.org/showthread.php?t=524826]("http://ubuntuforums.org/showthread.php?t=524826?p=#8")

If its not a V1, it probably won't  help at all :)

---

### Post by wieman01 on 2007-08-22
V4 means "ndiswrapper" as well...

---

### Post by Roswellgrey on 2007-08-22
You are right of course - sorry - what I put might be confusing :(

---

### Post by wieman01 on 2007-08-22
> **Roswellgrey said:**
> You are right of course - sorry - what I put might be confusing :(
No prob... it's a confusing topic, mate. All those version numbers and different chipset. :-)

---

