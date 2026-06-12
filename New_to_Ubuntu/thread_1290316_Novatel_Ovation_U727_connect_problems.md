---
title: "Novatel Ovation U727 connect problems"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by macheted01 on 2009-10-13
New to Ubuntu and having all kinds of problems. Ordered new Dell mini with Ubuntu and did not realize what I was getting into. After XP, Vista and now 7, I felt ready to try something different. In any case my problem is with trying to connect my USB Aircard, the Sprint Novatel Ovation U727. I have found the how to page on Sprint for this product. At first I was completely lost since I did not know how to enter a command. I know how to do this now. When plugging the U727 in the computer seems to recognize it and a folder opens immediately. The green light is also on, on the U727 as it should be. By the way the U727 has been activated on XP and works great on other computers.
From step 1 on Sprint page
[FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][LEFT]This setup assumes that you have installed the usbserial driver distributed on your Linux CD according to the instructions in the driver installation readme file. Ubuntu has this setup by default.
I am assuming that this is already installed, as it detects USB drives.
 
So I enter the command[/LEFT]
[FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2]sudo modprobe –r usbserial
It responds with
FATAL: Module -r not found.
 
I have browsed around the forums and found some info on this with no luck to me. I have also posted on some of them with not much luck either.
 
I found one post mentioning to eject the U727 and it will rescan and find the drive as it should. No luck with that either.
When trying to open a web page. The page opens and says Offline mode
Web Browser is currently in offline mode and cant browse the web.
Also, another box opens on the screen at this time that says
Close Firefox
Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox procedd, or restart your system.
 
Please, Any help would be greatly appreciated on this matter. Thanks.
[/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT]

---

### Post by macheted01 on 2009-10-17
I'm still having issues with this. Still cant get my usb modem to work. I have searched around the forum and it seems most all usb modems act the same. So anybody else that has had issues with other modems, please let me know what you had to do. It is my understanding that when the usb modem is hooked up, it will really give you no sign of being connected to the internet. If anyone has some tips on what I could try to do, please let me know.

---

### Post by jasonditz on 2009-11-06
> **macheted01 said:**
> I'm still having issues with this. Still cant get my usb modem to work. I have searched around the forum and it seems most all usb modems act the same. So anybody else that has had issues with other modems, please let me know what you had to do. It is my understanding that when the usb modem is hooked up, it will really give you no sign of being connected to the internet. If anyone has some tips on what I could try to do, please let me know.

I've been fiddling with this too on my hardy netbook. If I eject the "CD" and right click on the network manager, it appears to detect and set it up, but when it tell it to connect it immediately says "disconnected." 

I know we can get this working with enough effort, since it works in 9.04 on my laptop, but its really frustrating how touchy the thing is and how bad Sprint's "linux documentation" is.

---

### Post by macheted01 on 2009-11-08
Yeah, I never had any luck with it, because I could not seem to get any help anywhere. I just recently installed a bigger hard drive in my mini 10 and now in the works of reinstalling Ubuntu. Thinking about jumping into 9.10. Keep me posted on your efforts. Thanks.

---

### Post by YosefKaro on 2009-11-08
I managed to get the exact same modem working so it is doable.  I managed to do so both with Sprint's instructions as well as with a PDF that I found on the web.  However, the process is a bit too involved to go into it here.  What it involves is getting a deb file along with it's dependencies (5 .deb files total) and then editing /etc/wvdial.conf  (to be cont...) :p

-Yos

---

### Post by jasonditz on 2009-11-11
Yeah its doable a lot of ways... what I finally did was as follows 

sudo -s      (so you don't have to put sudo in front of everything) 

eject /dev/sr1     (or /dev/sr0 if you're using a system with no internal CD/DVD drive)

modprobe usbserial vendor=0x1410 product=0x4100

modprobe option

After that not only does Network Manager see it, but it will connect perfectly fine. The option module appears to be critical to getting this thing to work in newer versions of Ubuntu, and was enabled by default on my Jaunty laptop but not on my Karmic desktop.

---

### Post by macheted01 on 2009-11-12
Hey Thanks guys,
I ended installing 9.10 which was kind  of a bear for me, but got it done. As long as I have my Novatel plugged in upon turning the computer on it recognizes it and works fine. I'm sure some of the info. here will help others.

---

