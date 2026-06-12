---
title: "Monitor display"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by johnos on 2009-11-18
Hi,
 I'm new to Ubuntu and like it so far. I have been having an odd problem with my monitor. At first it wouldn't auto detect the monitor. I went to System, Administration, Hardware Drivers and loaded the suggested driver and restarted the computer. It seemed to fix things. While the monitor was listed as unknown it now listed several configurations. I selected the best fit and was happy. ...but  three times now it seems to loose this setting and changes back to 640 X 480. The only other setting listed is 320 X 240, even worse. I then load the other diver listed and after restarting the computer it comes back with the options and I can get back a usable setting. I just can't understand why it keeps reverting to the 640 X 480 setting. Is there another setting I need to change?
Thanks,
John

---

### Post by wojox on 2009-11-18
What graphics card are you using? What does this return:

```
lspci | grep VGA
```

---

### Post by johnos on 2009-11-19
desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV31 [GeForce FX 5600 Ultra] (rev a1)

---

### Post by NoaHall on 2009-11-19
Try using from the terminal (Applications -> Accessories -> terminal) "gksudo nvidia-settings" and then changing from there, then clicking on "Save to x-file" then restart.

---

### Post by johnos on 2009-11-20
Thanks for helping... I did as directed and the NVIDIA X server settings dialog box came up with settings that seem to be working. Hit button SAve to X configuration file and got a message:
Failed to parse existing X config file
'/ect/x11/xorg.config'!

---

### Post by Sir Jasper on 2009-11-20
Hi,

Can you please type or copy and paste the code below into your terminal

xrandr

click Return, then let us know if you see various screen resolutions as output.

My regards

---

### Post by johnos on 2009-11-20
Yes. A whole list of screen resolutions.

---

### Post by realzippy on 2009-11-20
Open terminal:

**sudo nvidia-xconfig**

---

### Post by cjohnston on 2009-11-20
When I first install the drivers on a system I have always had to run

sudo nvidia-xconfig

and then i just run

sudo nvidia-settings

to get to the config app.

---

### Post by johnos on 2009-11-20
_***Thanks***_ again for the help ***!****!! *** Things are working and looking Good.
John

---

### Post by cjohnston on 2009-11-20
Glad to hear it!

---

### Post by Sir Jasper on 2009-11-20
Hi,

OK, if you count down from the top on which no row is the display you want.

Also, can you please type the details of that row or copy and paste in your reply.

My regards

Addendum:

You seem to have it fixed which is all that matters, but if not please post the details requested.

---

### Post by running_rabbit07 on 2009-11-20
> **Sir Jasper said:**
> Hi,

OK, if you count down from the top on which no row is the display you want.

Also,cCan you please type the details of that row or copy and paste in your reply.

My regards

[http://ubuntuforums.org/showpost.php?p=8357781&postcount=10](http://ubuntuforums.org/showpost.php?p=8357781&postcount=10)

---

