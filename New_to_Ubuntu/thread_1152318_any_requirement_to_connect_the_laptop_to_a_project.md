---
title: "any requirement to connect the laptop to a projectory for showing slides?"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by legolas_w on 2009-05-07
Hi
Thank you for reading my post.
It is my first time that I am going to use my laptop in a conference to show slides during my speech.
I am wondering whether some sort of driver is required to be installed in my laptop to connect it to the projector?

I am using Ubuntu 9.04 and Any advice is welcome about required software and drivers....

---

### Post by Alterax on 2009-05-07
FWIW, my guess is that you may have to set up xorg.conf to handle the external monitor port as if it were another display.  Try connecting an external monitor to the computer, then rebooting as a test.  If it's autodetecting like X11 does now, then you may just have to deal with your monitor settings under System to make sure your display is being cloned.

If not, we may be able to hack a custom xorg.conf file.  It's not too tough though.

---

### Post by chellrose on 2009-05-07
> **legolas_w said:**
> Hi
Thank you for reading my post.
It is my first time that I am going to use my laptop in a conference to show slides during my speech.
I am wondering whether some sort of driver is required to be installed in my laptop to connect it to the projector?

I am using Ubuntu 9.04 and Any advice is welcome about required software and drivers....

What kind of laptop do you have?  On my Toshiba, I just connected the projector before boot and it was connected upon boot.  I didn't have to do anything.

Do you have access to a projector now?  If so, you should try it and make sure it works before getting to the conference. :)

---

### Post by djbushido on 2009-05-07
Ubuntu is VERY good with autodetecting displays on start up. Make sure the cable is plugged in on boot-up and you should be good to go.

---

### Post by Rany . on 2009-05-31
Helo, my LCD screen shows the ubuntu loading screen at boot up, but turns off as soon as my notebooks screen reaches the login screen.
Please help, I need to do a presentation tomorrow.

Thanks in advance.


Acer Aspire 4520, nVidia 7000M

---

### Post by legolas_w on 2009-05-31
Hi 
In my case, I launched the ATI setting manager and ensured that it mirror the first display onto the second display. using this way I had both my laptop screen and the projector slide showing.

I think you need to:

- launch nvidia-settings in a terminal
- goto "X Server Display Configuration"

now you should be able to configure the screen mirroring.


hope it helps.

---

### Post by Rany . on 2009-05-31
Hey, I got it on the LCD, but the res is only 640x480 on nvidia-glx-new-envy.
I changed to nvidia-glx-new, the res can go 800x600, but no display on Notebook screen..:(

---

### Post by clarkritz on 2009-06-05
This is not a practical solution.  At scientific conferences you have to jump up and start giving your talk immediateley.  If you only have ten minutes for a presentation you don't have time to do a cold boot.  

Generic Gnome with Arch Linux can detect a projector plugged in after boot up and can be running immediately.  Why can't Ubuntu?  

Plus, mirroring a laptop monitor on a projector with a different aspect ratio will give you a weird distorted picture.  I like extending my desktop onto the second monitor and choosing the approriate resolution (1024 x 768 usually) and launching the presentation viewer from the other screen.

---

