---
title: "WUSB54Gv4 driver issues"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by enc4free on 2008-06-12
Hi all, I'm new arround here.
Here is my question:
I recently installed the latest version of ubuntu (8.04LTS), and I have a wireless network (linksys), using WUSB54Gv4 as my adapter (which was supplied with the whole kit), I dont know much about using linux so please take it easy on me.
I want to install a driver for the adapter so I can surf the net ofcourse and have no idea how am I going to do that.
I contacted live chat with someone from the linksys support team who told me that they dont support such operating system and there is no compatable driver for me! I asked for a driver compatable with the hardware itself (for the chip), no such luck.
Is there anything I can still do?
thank you all (hoping to solve this issue).

---

### Post by DirtDawg on 2008-06-12
When I first installed Hardy, my linksys wusbd5gv4 (same as yours) did not work. However, when I connected my computer to a wired internet connection and *updated*, the wireless card worked just by plugging it in. However, I found the performance to be poor and the signal dropped often and caused the computer to freeze. But maybe your experience will be better.

If not, the very first post on Page 13 by Pavlick of [this thread]("http://ubuntuforums.org/showthread.php?t=588045&page=13") is just the thing to aid your woes. 

Follow it carefully and it will explain how to install the Windows drivers for your device onto your Ubuntu machine. I just did this several days ago and it works *perfectly*. That said, there are a couple problems. 

For one, the driver in question comes in an .exe file, so you will need to unzip it using either a Windows machine or Wine(available in Synaptic). That is, if you run the .exe file, it just unzips the thing. Don't ask me why it's not just a zip file  :confused:

Also, you will need to add the "sudo" command for some commands. Notably the "sudo make install" and "sudo ndiswrapper -i etc/etc/etc/" commands.

If you are new to Linux, you may find all this a little intimidating, but if you follow the instructions precisely, you should avoid most snags.

Good luck! Let us know if(when?) you need help.

---

### Post by enc4free on 2008-06-13
wow down 4 pages in 11 hours!
well, seems to have another problem.
suddently ubuntu doesnt startup claiming something about many many usb devices doesnt work properly (i have mouse&keyboard usb but worked just fine 2 nights ago on ubuntu)
how can I solve this so I can get to work on the wireless adapter?
thanx

---

### Post by enc4free on 2008-06-13
sorry had to reply for this again cause it got down by 1 page
does anyone has a solution for me?
I cant start ubuntu during to USB problems as I have written 1 post before this
thank you all

---

### Post by snowpine on 2008-06-13
Hi there, I have the exact same wireless adapter, and it was a real pain until I followed the instructions in the link that DirtDawg mentioned above. Reading through that thread helped me get it working.

One tip if you still can't get it working is to install 'rutilt'. It is a wireless utility that may or may not be easier for you than ubuntu's network manager. Good luck!

---

### Post by DirtDawg on 2008-06-13
> **enc4free said:**
> wow down 4 pages in 11 hours!
well, seems to have another problem.
suddently ubuntu doesnt startup claiming something about many many usb devices doesnt work properly (i have mouse&keyboard usb but worked just fine 2 nights ago on ubuntu)
how can I solve this so I can get to work on the wireless adapter?
thanx

Er, I really have no idea what your problem is here. Ubuntu won't start and there's an error about having too many usb devices not working? I have never heard of any problem like that and have no idea how to fix it. 

If this is still an issue, I would recommend starting another thread addressing this new problem. Hopefully someone can help you out.

Good luck

---

### Post by DirtDawg on 2008-06-13
> **snowpine said:**
> Hi there, I have the exact same wireless adapter, and it was a real pain until I followed the instructions in the link that DirtDawg mentioned above. Reading through that thread helped me get it working.

One tip if you still can't get it working is to install 'rutilt'. It is a wireless utility that may or may not be easier for you than ubuntu's network manager. Good luck!

Glad you got it working :KS It's actually a great little wireless card once it's running properly.

---

### Post by snowpine on 2008-06-13
> **DirtDawg said:**
> Glad you got it working :KS It's actually a great little wireless card once it's running properly.

On page 1 of the megathread you linked to above, there's another method that involves an open source rt2x00 driver instead of ndiswrapper. I've used that successfully on Gutsy, not sure if it works in Hardy. Just mentioning it so you know there is more than one way to skin a cat. (not literally)

---

### Post by DirtDawg on 2008-06-13
> **snowpine said:**
> On page 1 of the megathread you linked to above, there's another method that involves an open source rt2x00 driver instead of ndiswrapper. I've used that successfully on Gutsy, not sure if it works in Hardy. Just mentioning it so you know there is more than one way to skin a cat. (not literally)

I believe it does work in Hardy. But isn't the disadvantage of that method is it disables the roaming capabilities of the card? That's why I suggested the ndiswrapper method. 

Please correct me if I'm wrong.

---

### Post by snowpine on 2008-06-13
> **DirtDawg said:**
> I believe it does work in Hardy. But isn't the disadvantage of that method is it disables the roaming capabilities of the card? That's why I suggested the ndiswrapper method. 

Please correct me if I'm wrong.

You are exactly correct, and that's why I switched to rutilt :)

---

