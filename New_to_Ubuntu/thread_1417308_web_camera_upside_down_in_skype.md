---
title: "web camera upside down in skype"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by isssava on 2010-02-27
When i test web camera in Skype, on my ASUS X59SR-ap022, it is show upside down but in Cheese Webcam Booth it is working fine. Is there a way to correct that problem?

---

### Post by DeadSuperHero on 2010-02-27
Could be a driver issue. 

-What model camera do you have on your Acer?
-Can you find the latest driver in a Google search?
-Does the manufacturer provide just a .deb package, or is it in something like a .tar.gz?


Let's see if you have to build it from source.

If worse comes to worst, you may have to try upgrading Skype as well.

---

### Post by EssexEagle on 2010-02-27
> **isssava said:**
> When i test web camera in Skype, on my ASUS X59SR-ap022, it is show upside down but in Cheese Webcam Booth it is working fine. Is there a way to correct that problem?

Turn your webcam upside down?

---

### Post by isssava on 2010-02-27
I couldn't find drivers for Linux OS  from manufacturer's site. How can i check web camera model in Ubuntu 9.10?

---

### Post by theozzlives on 2010-02-27
```
lsusb
```I agree with essexeagle, turn the cam around.

---

### Post by isssava on 2010-02-27
This is what i get when i type "lsusb" in terminal:
Bus 001 Device 005: ID 0bda:0116 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 004: ID 064e:a111 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 046d:c049 Logitech, Inc. G5 Laser Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0603:00f2 Novatek Microelectronics Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

So how to fix upside down image in Skype (Only program that shows me upside image)?

---

### Post by isssava on 2010-02-27
I can't rotate it mechanically because it is integrated into my notebook.

---

### Post by EssexEagle on 2010-02-27
> **isssava said:**
> I can't rotate it mechanically because it is integrated into my notebook.

Fair enough.

A quick Google for "skype camera upside down" finds 86,000 hits, including 425 on forum.skype.com alone; if you haven't already, I suggest looking through some of these search results to see whether anyone has already solved this problem.

---

### Post by isssava on 2010-02-28
I searched around and i found one that could do the job ([http://ubuntuforums.org/showthread.php?t=838210](http://ubuntuforums.org/showthread.php?t=838210)), but i can't understand part that starts with red letters. Where should i create that folder?

---

### Post by mikewhatever on 2010-02-28
Try looking through a few last pages of the thread. It seems that simply starting skype as follows fixes the problem for many people.

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

---

### Post by shihkster1015 on 2010-02-28
There's a problem with asuses (is that a word??)
It's the same with some machines running windows. 
I think if you wait for a linux update, there might be one

---

### Post by kflarsen on 2010-02-28
I had the same problem on my ASUS laptop.
Follow these easy steps and your problem should be solved

[http://techspalace.blogspot.com/2010/02/upside-down-web-cam-simple-fix.html](http://techspalace.blogspot.com/2010/02/upside-down-web-cam-simple-fix.html)

---

### Post by isssava on 2010-02-28
Thanks for directing me to the right way. This helped me to finally run it with fully working web camera (not upside down). But is there a way to make it run from application menu like normal without terminal ( i tried to type command "LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype" in the main menu properties for that application but when i launched it from menu it said that it couldn't ["Failed to execute child process "LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so" (No such file or directory)]?

---

### Post by isssava on 2010-02-28
Thanks for the address that led me.

---

### Post by mikewhatever on 2010-02-28
> **isssava said:**
> Thanks for directing me to the right way. This helped me to finally run it with fully working web camera (not upside down). But is there a way to make it run from application menu like normal without terminal ( i tried to type command "LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype" in the main menu properties for that application but when i launched it from menu it said that it couldn't ["Failed to execute child process "LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so" (No such file or directory)]?

You can create a launcher for Skype with that command inside.

Create a text file named 'skype-launcher' and past in the following:

```

#!/bin/bash
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
```

save and exit.

Copy it to /usr/bin,
sudo cp skype-launcher /usr/bin

Then edit the command for Skype in the menu from skype to skype-launcher.

---

### Post by isssava on 2010-03-01
I created document on my desktop that i named "skype-launcher" and wrote "
#!/bin/bash
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype", but when i wanted to copy that file to the "/usr/bin" access was denied with or without using terminal. Any idea what i did wrong or if it really works?

---

### Post by mikewhatever on 2010-03-01
You need to use sudo as so:

sudo cp ~/Desktop/skype-launcher /usr/bin

If you want GUI, run **gksudo nautilus** instead, which opens the file browser with adim privileges.

---

### Post by buckyaustin on 2011-05-22
Well this is something i came up with since the new skype can share ur desktop, Open cheese and share that part of ur desktop to the recipient.... this will act like ur webcam and if u have a mic you can still use it

---

### Post by fritz269 on 2011-05-22
and I will throw some comic relief:

Turn the computer upside down or stand on your head :lolflag:

---

### Post by rocky7 on 2011-08-12
> Then edit the command for Skype in the menu from skype to skype-launcher.     Hi all,

mikewhatever what do you mean here? I could not find the menu you mentioned.

---

### Post by crysman on 2012-07-12
On my ASUS U36SD running fresh install Xubuntu 12.04 I fixed the problem this way:
[LIST=1]
[*]```
sudo apt-get install libv4l-0:i386
``` (because skype is 32 bit, so you need a 32 bit library)
[*]run skype from terminal like this: ```
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype
```
[/LIST]

---

