---
title: "screen resolution"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by rjs1064 on 2009-06-15
windows are too big for screen with evolution and several other things, screen resolution appears to be 640*480. i have nvidia gefoce5200 and have tried to follow advice on other threads, but to no avail.

---

### Post by ~sHyLoCk~ on 2009-06-15
Did you install the restricted graphics driver?

---

### Post by rjs1064 on 2009-06-15
yes, it has173 14 16. I did try getting a driver from nvidia but it wouldn't run.

---

### Post by mhgsys on 2009-06-15
I have a GeForce4 Ti 4200, and had to adjust my screen resolution in ```

system > preferences > display.

```
Clicking that gave me the warning: "It appears that your graphics driver does not support the necessary extensions to use this tool. Do you want to use your graphics driver vendor's tool instead?"

When I clicked yes I was taken to the nvidia-settings, were adjusting resolution did not hold on after reboot, even when sudo nvidia-settings and saving it to xorg.conf.

So.... click NO.

And adjust the resolution with the Display preferences menu, 
That worked for me, even after reboot my display is 1280x1024 working smoothly with extra visual effects.

Hope this also works for you.

---

### Post by rjs1064 on 2009-06-15
system / preferences / display says that i have unknown monitor and only lists 640*480 or 320* 240 . it is an advance 17s crt monitor if that is any help.

---

### Post by mhgsys on 2009-06-15
hmz, 
Mine also show a unknown monitor, but has way more resolutions listed for that.
what if you try to detect monitors?

Also:
what's in your nvidia-settings X Server Display Configuration?

>system> administration> Nvidia Xserver settings.

or in a terminal 
```

sudo nvidia-settings 

```

Set reslution to Auto (don't save to X)  and try to adjust settings again in system > preferences > display

---

### Post by rjs1064 on 2009-06-15
detect monitors doesn't do anthing[IMG]file:///tmp/moz-screenshot.jpg[/IMG][IMG]file:///tmp/moz-screenshot-1.jpg[/IMG][IMG]file:///tmp/moz-screenshot-2.jpg[/IMG]
xserver display 
  crt-0( oncrt-0 on gpu-0)
separate x screen.  resolution auto .  mode name nvidia-auto-select.  panning 640*480
it was already on auto so display preferences didn't change

---

### Post by zubin71 on 2009-06-15
type out the following at the terminal...

$ xrandr -s 1280x800

assuming 1280<x>800 is the resolution.
change it as required.

---

### Post by rjs1064 on 2009-06-15
i get command not found

---

### Post by stoogiebuncho on 2009-06-15
> **rjs1064 said:**
> i get command not found

Don't type the '$'

---

### Post by rjs1064 on 2009-06-15
i tried 1280x800 and 1280x960 ( twice the present) and got  "size 1280x800 not found in available modes".

---

### Post by rjs1064 on 2009-06-15
i also tried 1024x768 and 1152x864

---

### Post by ~sHyLoCk~ on 2009-06-15
Did u try changing to a lower refresh rate?

---

### Post by mhgsys on 2009-06-15
Do you see other resolution opties when opening nvidia-settings?


Can you change from auto , to a higher resolution.?

---

### Post by rjs1064 on 2009-06-15
i think there is only 1. 50hz or 59.93 depending where you look.
there are only three options, auto, 640x480, or 320x240.

---

### Post by mhgsys on 2009-06-15
hmz, Strange, . This is not my expertize, but I think the output of xorg.conf will be usefull to see/

Could you post your /etc/X11/xorg.conf 
?

---

### Post by rjs1064 on 2009-06-15
i typed /etc/x11/xorg.conf in terminal correct? and got no such file or directory.

---

### Post by mhgsys on 2009-06-15
nah, you should open it with a reader/viewer.

type:
```

gksudo gedit /etc/X11/xorg.conf

```

f.e.. You can also use vi, vim or nano and I don't know what more.
:-)

---

### Post by rjs1064 on 2009-06-15
Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    Option    "AddARGBGLXVisuals"    "True"
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection
looked in places and found this. i am rather new to terminal stuff.

---

### Post by mhgsys on 2009-06-15
well, that all looks ok compared to mine.

I don't see why your stuck in this resolution.
You could try to edit xorg.conf
And add VertRefresh and HorizSync manually to see if that helps/


check this page for info.
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by rjs1064 on 2009-06-15
i had several goes at that, lost gui and couldn't get it back, restarted, and all as before. would it be any good to reinstall ubuntu ?  i can't find out anything about my monitor on google( acana peripherals usa corp, advance 17s, made in 1998.

---

### Post by mhgsys on 2009-06-15
made me wonder. 

Can you get a higher resolution when you disable the hardware drivers>?

---

### Post by rjs1064 on 2009-06-15
i get 800x600 which is an improvement but no nvidia, and  no effects etc

---

### Post by mhgsys on 2009-06-15
Thats a sad improvement then, 
knowing your hardware can do much more nice tricks, 

I recommend you reinstall drivers, have a look here.

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by rjs1064 on 2009-06-15
thank you so much for your help i will have a go tomorow . just too tired to work it all out tonight.

---

### Post by rjs1064 on 2009-06-18
finaly found where i went wrong with putting hysync and refresh rate into xorg.config and now i have 800x600 with nvidia card! which if not a complete fix is a lot better. Many thanks .

---

