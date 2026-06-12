---
title: "How do I increase my 1024 x 768 screen resolution"
date: 2010-06-23
forum: New to Ubuntu
---

### Post by Warbandit on 2010-06-23
Im running Ubuntu 10.04 LTS on my Dell dimension 3000. I want to increase my screen resolution.If you can help me please post.

---

### Post by Perfect Storm on 2010-06-23
More info is needed;

```
lspci |grep VGA
```

---

### Post by Warbandit on 2010-06-23
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
This is what I got.

---

### Post by Possum Films on 2010-06-23
have you tried going to System -> Preferences -> Monitors ?

---

### Post by Warbandit on 2010-06-23
Yes

---

### Post by Perfect Storm on 2010-06-23
If Possum Films suggestion doesn't work;

Lets check the xorg
```
cat /etc/X11/xorg.conf
```

---

### Post by Warbandit on 2010-06-23
I typed in the command but it says it can't find directory

---

### Post by Perfect Storm on 2010-06-23
Make sure it's exactly - There's a difference between lower and upper letters in Linux.

By the way do also check if xorg intel is installed;

```
sudo apt-get install xserver-xorg-video-intel
```

---

### Post by Warbandit on 2010-06-23
Yeah its installed alright.

---

### Post by Perfect Storm on 2010-06-23
ok, but I still need to see your xorg.conf

---

### Post by bailout on 2010-06-23
ubuntu doesn't have xorg.conf by default any longer.

---

### Post by Perfect Storm on 2010-06-23
Ah, must be my nvidia restricted driver that makes one.

Then lets try with;
```
xrandr
```

Which options do you have? (and it will also tell you which resolutions the intel driver supports for your card)

---

### Post by Warbandit on 2010-06-23
[FONT=monospace]Screen 0: minimum 320 x 200, current 1024 x 768, maximum 2048 x 2048
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 304mm x 228mm
   1024x768       60.0 +   75.1*    70.1  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     60.0  
   720x400        70.1  
This is what I got.
[/FONT]

---

### Post by Perfect Storm on 2010-06-23
Okay. It seems it can't see your prefered resolution due to buggy intel driver.


```
cvt 1024 768
```
Change 1024 768 with your prefered resolution.

You 'll get 2 lines of output. You need the stuff after "Modeline"

And use it with;
```
xrandr --newmode <the stuff after "Modeline">
```

eg;
xrandr --newmode "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync

You can also read more about it here; [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
which go more in the depth of it.

---

### Post by penguinv on 2010-06-23
> **Warbandit said:**
> Im running Ubuntu 10.04 LTS on my Dell dimension 3000. I want to increase my screen resolution.If you can help me please post.

There is another thread about this same issue under my user name.

Learning to pose the question is a skill we all are working on.
Go to that thread. I got help that worked.

You can include the name of your monitor. You can look it up on the site of the manufacturer, mine was Dell, to see what the maximum possible resolution for the monitor is. Maybe you've got it already? Maybe not.

At least now you know how to get your video card info

   ```
 lspci | grep VGA
```

and how to find your present configuration file

    ```
cat /etc/X11/xorg.config
```

you can educate yourself by looking at the contents of that directory (ie the list of files in that folder) using

   ```
 ls /etc/X11
```

Best!


edit: wrapped CODE tags around text

---

