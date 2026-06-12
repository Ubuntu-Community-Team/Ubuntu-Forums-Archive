---
title: "How do I edit graphic properties in xorg.conf"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by alohatim on 2009-02-05
I finally got Ubuntu 8.1 installed on my second machine.  It took many tries and would not install until I used Safe Graphics mode.  Now, I would like to set a higher resolution than 640x480.  

The machine is a Dell 2350 desktop and has an Intel 82845G onboard graphics card.  I have upgraded the BIOS to A02 and set the graphics to "onboard" in BIOS.  

System/Preferences/Screen Resolution only gives me the 640x480 option.  I read in another forum that I should edit the xorg.conf file to say that "intel" is the driver and that I could also change the amount of memory the graphics uses.  I tried the command: sudo dpkg-reconfigure xserver-xorg. My results differed from the poster in the other forum.  All I got were settings for the keyboard.  

Other than the screen resolution, Ubuntu is running great.  I installed as dual boot with windows XP and XP continues to work. 

Mahalo nui loa for your help.

alohatim

---

### Post by abyssius on 2009-02-06
> **alohatim said:**
> I finally got Ubuntu 8.1 installed on my second machine.  It took many tries and would not install until I used Safe Graphics mode.  Now, I would like to set a higher resolution than 640x480.  

The machine is a Dell 2350 desktop and has an Intel 82845G onboard graphics card.  I have upgraded the BIOS to A02 and set the graphics to "onboard" in BIOS.  

System/Preferences/Screen Resolution only gives me the 640x480 option.  I read in another forum that I should edit the xorg.conf file to say that "intel" is the driver and that I could also change the amount of memory the graphics uses.  I tried the command: sudo dpkg-reconfigure xserver-xorg. My results differed from the poster in the other forum.  All I got were settings for the keyboard.  

Other than the screen resolution, Ubuntu is running great.  I installed as dual boot with windows XP and XP continues to work. 

Mahalo nui loa for your help.

alohatim

Try:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by alohatim on 2009-02-06
I think I found the answer: sudo nano /etc/X11/xorg.conf

I sort of figured out how to use that editor.  For the "Device" called "Configured Video Device", I change the driver from "vesa" to "intel".  

Then I pressed ctrl+X to exit.  It asked me to write the file: /etc/X11/xorg.conf.  After staring at this line for a few minutes, I pressed the enter key--and then it went away.  I think I did ctrl+X one more time and I was back at the terminal.  

When I restarted, the new screen appeared at an acceptable resolution.

---

### Post by alohatim on 2009-02-06
Thanks, Abyssius.  I think I had tried it with the -phigh switch also.  Just for the heck of it, I did sudo dpkg-reconfigure -phigh xserver-xorg again after I had the screen in good resolution.  After rebooting, it reverted back to the 640x480.  

So, back to the nano editor and all is fixed again. 

Thanks for replying.  BTW, how do I put code in a box like you did?

---

### Post by abyssius on 2009-02-06
> **alohatim said:**
> Thanks, Abyssius.  I think I had tried it with the -phigh switch also.  Just for the heck of it, I did sudo dpkg-reconfigure -phigh xserver-xorg again after I had the screen in good resolution.  After rebooting, it reverted back to the 640x480.  

So, back to the nano editor and all is fixed again. 

Thanks for replying.  BTW, how do I put code in a box like you did?

You place the code text between keywords CODE and /CODE. However you need to use square brackets around the keywords [...]. Sorry, I don't know how to show you this without actually triggering a code box. I hope you understand this convoluted explanation.

---

### Post by alohatim on 2009-02-06
Yes.  I think I've got it.  Thanks, again!

---

### Post by Malalo on 2009-02-06
> **abyssius said:**
> You place the code text between keywords CODE and /CODE. 

You can also just use the # icon when you tpe in your post, it will automatically create the CODE tags and you write what you in between.

---

### Post by majabl on 2009-02-06
> **alohatim said:**
> I think I found the answer: sudo nano /etc/X11/xorg.conf

I sort of figured out how to use that editor.  For the "Device" called "Configured Video Device", I change the driver from "vesa" to "intel".  

Then I pressed ctrl+X to exit.  It asked me to write the file: /etc/X11/xorg.conf.  After staring at this line for a few minutes, I pressed the enter key--and then it went away.  I think I did ctrl+X one more time and I was back at the terminal.  

When I restarted, the new screen appeared at an acceptable resolution.

Thanks - this worked for me and my old computer when I just did an install!

---

