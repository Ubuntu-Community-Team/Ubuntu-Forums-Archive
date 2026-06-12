---
title: "Ubuntu won't detect my camera"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by st4 on 2009-04-23
What should I do:confused:

---

### Post by Godly on 2009-04-23
I would suggest posting some spces. What kind of camera, what distro you're using, and vefify your camera is compatible with linux.

---

### Post by CRIMPS on 2009-04-23
Can you give us more information?  What kind of camera?  What version of Ubuntu are you running?  The more you provide, the more we have to work with to help you.

---

### Post by st4 on 2009-04-23
Thanks for the replies, it's one of [these.]("http://www.ecamerafilms.com/Waterproof_Digital_Camera_p/dc1131.htm")

It doesn't say anywhere in the instructions that it's compatible with linux, tho. Just windows and Mac.:(

---

### Post by st4 on 2009-04-23
Oh and I'm running Ubuntu 8.10.

---

### Post by st4 on 2009-04-23
I've installed gtkam but still no luck.

---

### Post by st4 on 2009-04-23
[Will this work,]("http://www.linux.com/feature/34681") if i buy a card reader? And what do you do, just plug your camera into the card reader?

---

### Post by CRIMPS on 2009-04-23
yeah, a solid card reader is the way to go.  Nice find!

---

### Post by anewguy on 2009-04-23
With your camera plugged in to a USB port, do the following and then copy the results back to a post here:

lsusb <press enter>

sudo lsusb <press enter>

There were some changes starting back at 8.04 on how some of the permissions are handled, and in particular who "owns" a USB file system from a device such as a camera.  These are not the permissions you see on files, but rather are set via the udev rules files.  While I don't know if it will be the case with your camera or not, some have been getting mounted as owned by root - hence why I'd like both outputs above.  It's been a while since I worked around that, so I really don't remember if it gives a permissions error or just doesn't think the device exists unless you are root.

We'll see after you post the results.

Dave :)

---

### Post by Godly on 2009-04-23
Once you've verifed the card reader works, let us know. Thanks!

---

### Post by st4 on 2009-04-24
> **anewguy said:**
> With your camera plugged in to a USB port, do the following and then copy the results back to a post here:

lsusb <press enter>

sudo lsusb <press enter>

There were some changes starting back at 8.04 on how some of the permissions are handled, and in particular who "owns" a USB file system from a device such as a camera.  These are not the permissions you see on files, but rather are set via the udev rules files.  While I don't know if it will be the case with your camera or not, some have been getting mounted as owned by root - hence why I'd like both outputs above.  It's been a while since I worked around that, so I really don't remember if it gives a permissions error or just doesn't think the device exists unless you are root.

We'll see after you post the results.

Dave :)These are the rsults I got with those commands,

bill@bill-desktop:~$ 
bill@bill-desktop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 05e1:0b02 Syntek Semiconductor Co., Ltd 
Bus 001 Device 003: ID 041e:3f07 Creative Technology, Ltd 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
bill@bill-desktop:~$ sudo 
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
bill@bill-desktop:~$ lsusb

---

### Post by st4 on 2009-04-24
> **Godly said:**
> Once you've verifed the card reader works, let us know. Thanks!I will, [will this work?]("http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=380116746721#ebayphotohosting")

---

### Post by st4 on 2009-04-24
To answer my own ?, I don't think the reader I posted above will work. that's a UDMA card reader, and I need an SD reader. So I got [this one]("http://www.amazon.com/Memory-Card-Reader-USB-2-0/dp/B000R4J1G8/ref=sr_1_1?ie=UTF8&s=electronics&qid=1240579652&sr=1-1") from amazon. I hope it works with linux suystems. It doesn't say tho, just Windows and Macs.

---

