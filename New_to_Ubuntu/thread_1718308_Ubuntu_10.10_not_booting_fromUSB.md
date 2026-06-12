---
title: "Ubuntu 10.10 not booting fromUSB"
date: 2011-03-31
forum: New to Ubuntu
---

### Post by mbogo.kariuki on 2011-03-31
Hi all,
I downloaded Ubuntu 10.10 yesterday a created a boot USB. Every time I try to boot I get an error,

unkown keyword in the configuration file

what could be the problem and how is it solved? :confused:

---

### Post by IWantFroyo on 2011-03-31
Redownload the iso and try again. That means there's something wrong with your image. I got that error after moving a file onto my boot USB and trying to use it.

---

### Post by oklokl on 2011-03-31
In my case
Twice after installation
The file was corrupted
-_-;;;
USB does not  recommend
Please use the ODD

New Downloads
Reinstall
But the same symptoms
No problem USB

---

### Post by mastablasta on 2011-03-31
> **IWantFroyo said:**
>  I got that error after moving a file onto my boot USB and trying to use it.
 
why would that make a difference? i thought you can freely add files once you put the image on boot disk. as long as you don't modify the system files.
 
was i wrong?

---

### Post by IWantFroyo on 2011-03-31
I don't know if the media was faulty, but I moved a folder of my files into a live usb, and it gave me the error.
I remade the live usb and it worked. At this point I can't remember if it was the same iso file or not.

---

### Post by Baniita on 2011-03-31
Duuude. I have no idea really. All I can say is what I did, since I'm also running Ubuntu from a USB drive.

In my case, I got Ubuntu 10.10 from a CD. From System > Startup Disk Creator. Selected drive, created startup disk... Tada.

So all I can suggest it re-download Ubuntu, and if you have a bunch of blank CD's, just burn it onto one. Use the CD or move it onto a USB. /Shrug. Your choice.

I don't know how to download it directly onto a USB, though. I don't think that even works. Heck, it took me forever to figure out how to set it up on my USB.

---

### Post by Baniita on 2011-03-31
xxxNevermind. I thought the issue was solved but it was Froyo, not the original requester for help. Hurr. ...Actually, how do I delete this post? TROLOLOL--/Shot.

---

### Post by karibik on 2011-03-31
I have ubuntu downloaded and cd gebrant with image recorder but if he is up is because only the background to know what to do?
Ps I downloaded onto it more than once.

---

### Post by mbogo.kariuki on 2011-04-01
Ok guys. Finally it worked. I did not download the iso again but burned the usb from Windows were I had downloaded it and it just worked. The earlier usb i had burned from Ubuntu 9.04. Maybe a compatibility problem. 
But am having new problems! I have a ZTE AC 2726 modem that i wish to use but cant get it working. I have read alot about it from the net but just cant fix it. The problem is the OS sees the modem as storage device (or so i think!). When i '*lsusb*' the modem appears as:

[I]Bus 005 Device 002: ID 19d2:fff5

[/I]instead of[I]

Bus 005 Device 002: ID 19d2:fff1.

[/I]I tried to download and install the *usb-modeswitch_1.0.2-1_i386.**deb *but the OS says there is a later version already installed. 

Just how do i solve this? I really need to know more about Ubuntu!!!

And thanks for your helps guys.

---

