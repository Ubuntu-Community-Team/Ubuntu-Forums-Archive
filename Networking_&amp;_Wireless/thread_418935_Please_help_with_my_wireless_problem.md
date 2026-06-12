---
title: "Please help with my wireless problem"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by jc0811 on 2007-04-22
I have a 2wire usb adapter 802.11g and I just installed  the final release of feisty fawn. But it does not recognize my usb adapter. Here is more information on my usb adapter

[http://www.2wire.com/?p=117](http://www.2wire.com/?p=117)

It works fine in crappy Windows XP. But nothing in Feisty Fawn. :confused: 
I tried installing ndiswrapper then it tells me I need ndiswrapper common. Hopefully somebody can help and put me in the right path. 

JC

---

### Post by Floppyjoe on 2007-04-22
You can probably use the Ubuntu install disk as a repository to install ndiswrapper-common.

---

### Post by jc0811 on 2007-04-22
> **Floppyjoe said:**
> You can probably use the Ubuntu install disk as a repository to install ndiswrapper-common.

I tried doing that but could not figure out how you can add the cd-rom permanently. Without asking it for it every time.

---

### Post by undertakingyou on 2007-04-23
When you put in the CD it should ask whether you would like to install packages from it or not.  And then you just use synaptic to install them.  Otherwise, you can put in the CD and then run the synaptic package manager **System=>Administration=>Synaptic** and then while in synaptic go to **Settings=>Repositories**  There is a box in the bottom of that dialog box that says install from a CD-ROM.  See if you can install it from there.  

Otherwise, is there anyway to temporarily set up a wired connection, install what you need, and then go from there?

---

### Post by undertakingyou on 2007-05-01
So, I got together w/ jc0811 and looked at his machine.  That silly 2wire USB adaptor was causing his machine to lockup.   I was able to follow the guide located at [http://www.linuxquestions.org/questions/showthread.php?t=367770](http://www.linuxquestions.org/questions/showthread.php?t=367770)
The guy says that he got the card working w/ ndiswrapper.  I followed his guide to the 'T' and now jc0811's computer doesn't lockup, and lsusb sees the device as there, and ndiswrapper says that the device is present.  All that being said, the light on the card will not illuminate, and iwconfig shows no wireless devices.  

Any thoughts or workarounds?

---

