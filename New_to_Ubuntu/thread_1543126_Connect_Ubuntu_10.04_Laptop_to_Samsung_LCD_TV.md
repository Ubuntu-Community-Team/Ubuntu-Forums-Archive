---
title: "Connect Ubuntu 10.04 Laptop to Samsung LCD TV"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by sudip@houston on 2010-07-31
I'm trying to connect my ubuntu laptop to my Samsung TV. I went to NVidia X Server Settings and to X Server Display Config. From the display I selected samsung and configured it to Seperate View and hit clone with Auto detect resolution. But the display on my laptop got extended and the TV was not showing the entire desktop. I changed the resolution to a number of setting but none proved correct. How do I make the entire desktop on my laptop screen to appear on the LCD TV.
Thanks in advance.
-- Sudip

---

### Post by sudip@houston on 2010-07-31
*** BUMP *** Please help

---

### Post by JustinR on 2010-07-31
Just mess around with the settings. You'll get it to work - the nVidia graphics control panel is sort of confusing.

---

### Post by cariboo on 2010-07-31
Please don't bump your thread until 24 hours has elapsed, excessive bumping makes it look like you are getting help, and the person that can answer your question may just pass it by.

---

### Post by dream_coder on 2010-08-01
a little hint look for "overscan compensation" in the nvidia-settings it allows u to resize your desktop :)

ps also make sure u run "sudo nvidia-settings" from terminal or probably bettter command would be "gksudo nvidia-settings" 
so it can save the changes

can you mark as solved please if this solved your problem thanks

---

### Post by sudip@houston on 2010-08-03
I ran the nvidia settings as sudo. But I don't seem to get a bar or something like that to compensate for the overscan. Do I have to install any drivers for my Samsung LCD?

---

### Post by ieee488 on 2010-08-03
I have a LG HDTV. There is a setting for video for **Just Scan**. According to the owner's manual, this is the setting I would use if connected to a PC. You might want to see if there is something similar for your Samsung.

---

### Post by sudip@houston on 2010-08-03
Where exactly does the "**Just Scan**" feature appear? Is it in the Nvidia settings - if so I don't have it.

EDIT: *[COLOR="Red"]On a side note I'm wondering if I have the right NVidia drivers. How do I check and what should be results I would look for. TIA[/COLOR]*

---

### Post by smokie75 on 2010-08-03
> **dream_coder said:**
> a little hint look for "overscan compensation" in the nvidia-settings it allows u to resize your desktop :)

ps also make sure u run "sudo nvidia-settings" from terminal or probably bettter command would be "gksudo nvidia-settings" 
so it can save the changes

can you mark as solved please if this solved your problem thanks
Maybe we are a little thick here but, it seems we are all having trouble finding the overscan adjustment in the NVIDIA X Server Settings.  I've been through EVERY menu (even opening advanced settings) and still no joy.  Can you give anymore direction?

---

### Post by dream_coder on 2010-08-04
here guys a pic i found on google for you, this is the nvidia-settings with the position of overscan [http://www.desai.fr/images/blogimages/overscan/overscan.jpg]("http://www.desai.fr/images/blogimages/overscan/overscan.jpg")

the middle one of the 3 scroll bars hope this helps

Just choose the monitor/screen you want to adjust and scroll to get desired size so desktop fits onto the monior/screen/lcd etc :)

Regards

P.S you must have the proprietary drivers installed or surely you would not have nvidia-settings and no you should not need any drivers for the tv, Ubuntu should recognise the correct model or near enough it did for my no make Baird 37" lcd and baird is not even a manufacturer its just a rebadge lol

---

### Post by sudip@houston on 2010-08-04
Thanks!! Will look for the setting today.

---

### Post by Bills Shadow on 2010-08-23
I'm so happy I came across this because it fixed my problem and with allot less work then I thought was needed! I couldn't find the overscan option too!:lolflag:
Thanx alot):P

---

### Post by dream_coder on 2010-08-30
no worries glad I could help happy ubuntu'ing :)

---

