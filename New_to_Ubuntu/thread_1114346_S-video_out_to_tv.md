---
title: "S-video out to tv"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by Mtrboat on 2009-04-02
I have a hp pavilion dv5000 with a VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1) . I would like to see the video go out the s-video to the tv . this worked before on xp and i would like to get it to work on ubuntu now that i don't use xp anymore can anyone help ?

Anyone have any ideas on what to do to fix this ? This is my second post this forum responds fast and is very helpful . I thank you in advance.

---

### Post by Elfy on 2009-04-03
Have you tried using nvidia-settings?

```
gksudo nvidia-settings
```

Have the tv plugged in before you run it - it should recognise the tv.

I have my monitor and tv set as seperate X screensbut there are other options.

---

### Post by card_ace on 2009-04-03
i can't tell you what video card i have as i'm really not sure :lolflag: but i have a S-Video out port too and how i got it to work was by turning off the computer and taking my monitor plug out and then putting the s-video cable in.  worked like a charm

---

### Post by Mtrboat on 2009-04-04
thank you for your time. i opened a terminal and put this in gksudo nvidia-settings it paused for a min then displayed:
dominic@dominic-laptop:~$ gksudo nvidia-settings
dominic@dominic-laptop:~$ 
the three row monitor plug on the side of the laptop is not being used .the s-video out is what i am trying to get up and running. i have pluged in the s-video cable and held the [FN] & pressed the f4 video out key and i get a flicker then nothing is there a driver i need or somthing to configure this?

---

### Post by Elfy on 2009-04-05
Do you have the driver installed?

Go to System > Admin > Hardware Drivers - does it say that the driver is activated?

---

