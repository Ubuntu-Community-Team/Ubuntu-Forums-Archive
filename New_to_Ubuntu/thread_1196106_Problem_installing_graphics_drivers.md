---
title: "Problem installing graphics drivers"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by Carolla on 2009-06-24
I am installing Ubuntu 9.04 and installed the recommended graphics drivers for my installation. When it rebooted I got a black screen, then later some blocks of color, but no functional desktop. I think the functions were there, if I moved and clicked my mouse the colors changed, but the grapics were messed up. How do I know what drivers to install? I tried two of the recommended drivers, each on a new install, and don't really want to keep reinstalling Ubuntu. On the other hand, my goal is to play Civ 4 and to use Ubuntu as my OS, so I do need drivers I'm sure! 

Also, is there some way to get information as to the hardware on my computer through Ubuntu, or will I have to open it up and try to figure it out? (This particular computer is a bit of a kludge from leftover parts and I don't remember all the components I ended up with!)

---

### Post by sideffects on 2009-06-24
What kind of graphics card do you have. Ubuntu seems to be having some problems with ATI. I think there is a workaround though.

---

### Post by Carolla on 2009-06-24
Is there some way to tell without opening the computer? I think its some sort of ATI card though, Ubuntu calls for ATI drivers.

---

### Post by decoherence on 2009-06-24
> **Carolla said:**
> Is there some way to tell without opening the computer? I think its some sort of ATI card though, Ubuntu calls for ATI drivers.

run

Applications > Accessories > Terminal

and type 
```

lshw -C video
```

"product:" and "vendor:" are the important bits.

---

### Post by Carolla on 2009-06-24
product: NV43 [GeForce 6600 GT] 
vendor: nVidia Corporation

Thanks! Now what do I do to properly install drivers? I'm afraid I'm pretty ignorant, but don't intend to stay that way!

---

### Post by Bucky Ball on 2009-06-24
Boot from the LIVE install CD, choose the option to 'Try Ubuntu'. Do you have success and screen problems? 

Whilst there, you can go to System->Administration->System Monitor and that gives some information about the machine.

You can also open a terminal (Applications->Accessories) and paste this in:

lspci 

That will tell you EVERYTHING that is in the machine. Search for your video card and post back here, please. :)

* UPDATE: Everyone else beat me to it! What they said ... ;)

---

### Post by sideffects on 2009-06-24
> **Carolla said:**
> product: NV43 [GeForce 6600 GT] 
vendor: nVidia Corporation

Thanks! Now what do I do to properly install drivers? I'm afraid I'm pretty ignorant, but don't intend to stay that way!

System > Administration > Hardware Drivers
Then click activate.

Although, I can't confirm this because I'm at work and running XP, atm.

---

### Post by Carolla on 2009-06-24
In case there is any confusion, I can run Ubuntu with the default set up without any problems, but want the specific drivers for my video card so that I can set it up to play games. (Windows games)  Thanks for your help so far!

Edit: The drivers that come up when I go to System> Administration> Hardware Drivers are the ones it automatically told me to use previously that messed everything up. I tried both of the first two choices (my bad, they are Nvidia drivers) and neither one worked properly. Any more ideas?

---

### Post by sideffects on 2009-06-24
That's weird. I'm not sure what the issue is because I think I have that exact same graphics card and have had no problems.

---

### Post by sideffects on 2009-06-24
Actually, I think my friend was having a similar problem. Maybe not though. In any case, here is the thread [http://ubuntuforums.org/showthread.php?t=1161726](http://ubuntuforums.org/showthread.php?t=1161726). I don't know if he ever solved it or not.

---

### Post by Carolla on 2009-06-24
> **sideffects said:**
> That's weird. I'm not sure what the issue is because I think I have that exact same graphics card and have had no problems.

Which driver are you using?

---

### Post by Carolla on 2009-06-25
I have a question - is there some way to access your settings and install or uninstall the drivers when you boot to a black screen with a mouse cursor without having to reinstall Ubuntu? Can I boot with the live CD and change what's on the hard drive? Or? I don't want to play around with the graphics drivers if I have to reinstall Ubuntu every time it gets messed up, but as it is, I don't know how I can access the OS to change anything. 

Also, when I boot, I am unable to access the GRUB menu, it doesn't seem to respond to my keyboard when I get the message to press ESC to access the GRUB menu. :(

---

