---
title: "No Wireless Option"
date: 2007-09-03
forum: Networking &amp; Wireless
---

### Post by Wired2k7 on 2007-09-03
I've had a look at a few threads, but none of them seem to help my particular problem.

I installed Ubuntu this morning, and I haven't been getting any wireless options in the networking bit, and when I tried to install ndiswrapper, Ubuntu told me that it couldn't download it...

I (think) I have an inbuilt wireless card by 'VIA Technologies'. I did *lspci -v | less* to get that information, but I cannot post exactly what I got because of the no internet on Ubuntu. I checked on the hardware bit under System, and it mentions the type of VIA card it is, but it doesn't seem to recognize it as a wireless card... if that makes any sense. Sorry if it doesn't, i'm new to Linux and I've never had any wireless problems with Windows XP.

---

### Post by Trash_Gordon on 2007-09-03
Well, to install ndiswrapper you need some kind of internet connection. Maybe you can connect your PC with wired network?

EDIT: Do you know what model number your card has? Because [here]("http://www.treiberupdate.de/treiber-download/download-32342-treiber-VIA-VIAVT8231/VT8233/VT8235/VT8237.html") are drivers for VIA VT8231 / VT8233 / VT8235 / VT8237

---

### Post by Wired2k7 on 2007-09-03
Thanks for the help :)

I might be able to connect downstairs, i'll check.

But I don't think the card is any of the VT ones, I think it began with C.

I found a download of ndwrapper on sourceforge [http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)

is there any way I can download that on windows then put it on a ram stick then somehow add it to my installed programs on Ubuntu?

---

### Post by Trash_Gordon on 2007-09-03
Yes, that's possible. You have to check the dependencies though. You should download .deb packages and then install them with dpkg -i <filename>.deb

Install ndiswrapper-utils-1.9 first, then ndiswrapper-common.
I also recommend you to install ndisgtk, then you can easily manage the windows drivers with a GUI.

---

### Post by Wired2k7 on 2007-09-03
I've got it connected to the internet with wires, and i've installed ndiswrapper, and i'm just gonna try and find the inf file for my driver. :D Thanks for the help.

---

