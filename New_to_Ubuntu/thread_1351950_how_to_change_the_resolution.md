---
title: "how to change the resolution"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by irfan7706 on 2009-12-11
Hi i am using ubuntu 9.04 version and the problem is i'm not able to change the screen resolution......there are only two resolution options available (800*... and 600 *..),i'm new to ubuntu and i have gone thru the begginers guide however it did not solve the problem....thanks in advance

---

### Post by jbrown96 on 2009-12-11
You probably need to install a video driver to set the resolution. Go to System-->Admin-->Hardware drivers and see if anything is available. You will need to restart if you install one. 

You will also need to use your graphics card's utitility to manage the resolution. 

For ATI: 
There should be an entry in your Applications folder.

For Nvidia:
It's somewhere in Applications, but I always launch it with Alt+F2 then type gksu nvidia-settings. Once you set your resolution be sure to click "Save to X config file" to make the changes permanent.

Usually once you get the driver installed, it will automatically fix the resolution.

---

### Post by madnessjack on 2009-12-11
I have never got past this problem. If you Google around for EDID (to do with your monitor, it tells your PC what resolutions it can handle, but sometimes it's wrong) you should be able to trick Ubuntu by using a fake/different one.

I've only ever got around this by using a different monitor.

---

### Post by wojox on 2009-12-11
Run in your terminal:

```
lspci | grep VGA
```

and tell us what you get.

---

### Post by irfan7706 on 2009-12-12
when i run the command 
  lspci | grep VGA
i get this message
VGA compatible controller: nVidia Corporation GeForce 6100 nForce 405 (rev a2)


and when i try to install the hardware drivers  it searches for available drivers gives me three options when i select any one and click activate is does not respond

---

### Post by Bartender on 2009-12-12
"Activate" is a mis-leading term.  It's actually "download and install".  Are you connected to the internet when you click on Activate?  In my limited experience, the Hardware Drivers utility is pretty handy.  But I've got a few older (as in AGP) Nvidia, ATI, and Matrox cards that would probably benefit from better drivers if they existed but the utility pulls a blank.

---

### Post by ST3ALTHPSYCH0 on 2009-12-12
You could try the link in my sig if the driver by itself doesn't sort your problem.

---

