---
title: "Wifi won't maintain connection.  Needs SIS drivers?"
date: 2011-03-11
forum: New to Ubuntu
---

### Post by Footling on 2011-03-11
I'm a Linux/Ubuntu newbie so apologise if I need walking through this in  baby steps!

A while ago I bought a laptop without an OS,  installed Ubuntu without any problems and loved it.  Unfortunately,  since day one it hasn't maintained its wifi connection for long.

Assuming  this was part of an issue that's supposed to have plagued Ubuntu 10.04  onwards, I changed OS.  So far I've tried Peppermint, Easy Peasy, Leenux  and am now on Jolicloud - but the problem hasn't been solved.   (Jolicloud may seem an odd choice, but a system designed for internet  use seemed a reasonable place to expect an internet fix. Yes, that's how  naive I am.)

After more research, it seems that the problem may  be with the netork adapter, a **Realtek TRL8187B wireless 802.11b /g  54Mbps USB2.0** as it doesn't have the right drivers.  (The source of  this info is [here]("http://forums.ebuyer.com/showthread.php?58638-Foehn-Hirsch-Laptop-Intel-Celeron-Dual-Core-T3000-4GB-RAM-320GB-HDD-15.6-TFT-DVDRW-Webcam-No-Operating-System-%28Quickfind-185894%29/page3&highlight=Foehn+Hirsch+laptop")  - page 2, post #59 and page 3, post #70, particularly.)   Incidentally,  I found that every Linux OS I've tried has worked perfectly, apart from  this glitch.

Ubuntu forums suggest not installing drivers direct  from Realtek (not that I'd know how to do it anyway) so I'm not sure  what the fix is. I seem to be going in circles through the forums and am  even more confused as Jolicloud doesn't use quite the same format as  Ubuntu so any instructions about going into Admin/Hardware Drivers etc.,  don't 'fit'.

Sorry if I've gone on too much.  I hope you can  help - I really DON'T want to install Windows just to get online but  must admit I'm feeling out of my depth!

---

### Post by Hippytaff on 2011-03-11
Can you post the output of```
lspci
``` or ```
lsusb
``` if it is a usb device.
 
You might need to install the windows driver using ndisgtk. the above commands will tell us which driver that is.
 
Ndisgtk will need the .inf and .sys files from the windows XP driver (it has to be XP). You need to extract these to a folder then opint ndisgtk at the .inf file.

---

### Post by Footling on 2011-03-11
Thanks, Hippytaff :)  lspci shows this:

[IMG]https://lh6.googleusercontent.com/_LMbD-xrqLhc/TXpxqehSN7I/AAAAAAAAE3M/AffUnhJ8aZU/s512/Screenshot.jpg[/IMG]

---

### Post by Hippytaff on 2011-03-11
I can't see a wireless device there - is it a usb dongle?

And are you sure its not a hardware problem - as you say it doesn't seem to work with any OS

---

### Post by Footling on 2011-03-11
Definitely not a USB dongle.  The spec of the laptop is very good for what I use it for (i.e. no gaming or 3D requirements, just surfing the net and general office doodads) and it came with a CD of drivers - but it seems that they're tailored to Windows. 

Post #59 in the ebuyer forum suggests that when Windows is loaded, Device Manager shows that the chipset is a **Realtek TRL8187B wireless 802.11b /g 54Mbps USB2.0 Network adapter.  **As I couldn't find that on the[ list of wireless cards supported by Ubuntu]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion"), it did seem likely to be the culprit.  

I found some [driver downloads on the Realtek site]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#352"), but have no idea whether they'll help or how to install them.

Sorry to sound so useless.

ETA: I'm pretty sure it's not a hardware problem as I ran Windows Vista very briefly, just to check, and all the kit including wifi worked without any problems, so I should have said, "Since day one *of using a non-Windows OS..*."    Wigwam (a member on the ebuyer forum) seems confident that it's a lack of SiS drivers that's the culprit with any non-Microsoft OS, hence my digging around at realtek.com.

---

### Post by Hippytaff on 2011-03-11
What I would do is download the XP driver. 

install [ndisgtk]("http://linuxappfinder.com/package/ndisgtk") and install the windows drivers thus - 

Extract the .inf and .sys files and put them in a folder (I always make a folder on my desktop - Bad windows user habit) The open Ndisgtk and point to the .inf file. Reboot.

Let me know how it goes

---

### Post by Footling on 2011-03-12
Sorry about this, Hippytaff.  I know that what I'm trying to do should be really simple - except that I don't know to do it, so it's not :rolleyes: 

I've found that I can't download **ndisgtk** because - surprise - Joli OS has Chrome as its browser, not Firefox.

Downloading Firefox was the obvious solution but once I'd got the file in Downloads, I stalled.  Embarrassingly, it seems I'm dependent on being spoon-fed.

So I've spent the morning looking through various tutorials.  They're interesting, but not telling me what I need as an ABSOLUTE beginner.

I feel like I'm walking miles just to reach the house next door and I know I'm wasting your time, but can you point me in the right direction, please? :oops:

---

### Post by Hippytaff on 2011-03-12
Thats understandable...it's all new
open a terminal CTL+ALT+T and do```
 sudo apt-get install ndisgtk
```Then extract the windows XP drivers to a folder (the .inf and .sys files). Then open ndisgtk and point it to the .inf file. That should install the drivers.

BTW - your not wasting my time - I can do that all by myself ;-)

---

### Post by Footling on 2011-03-13
[SIZE="1"]I think we've done it - I'm actually typing this using the laptop's wifi[/SIZE]

I'm whispering that because you never know ;)

There were a couple of scares along the way - I followed your instructions and downloaded **ndisgtk** without any problems, but it was getting late and like an eejit I closed down the system.   Then I couldn't remember how to get into it again! 

Also after a day of frustration trying to find and download the Windows XP drivers, I realised last night that they were probably on the CD that came with the machine :brickwall:  Never try this stuff when you're tired...

Then I remembered to use sudo ndisgtk and things went swimmingly; I simply followed the instructions until...
[IMG]https://lh3.googleusercontent.com/_LMbD-xrqLhc/TXy5G9n_M3I/AAAAAAAAE3s/XdLufTD_1Io/s512/Cropped%20Screenshot-3.png[/IMG]
 
To cut a very long story into a long one, I ignored it,closed all the terminals, apps etc and deleted the old wireless connection then set it up again.

It logged on without missing a beat and is still working.  So far, so good.  Thanks for your help, Hippytaff  \\:D/

---

### Post by Hippytaff on 2011-03-13
Your welcome! glad you got it sorted :-D

Remember to mark you thread as solved in the thread tools at the top of the page :-)

---

