---
title: "[SOLVED] Reinstall Original Display Settings"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by wheelerrver on 2008-12-15
I have been using Ubuntu without any problems until today.  I apparently accidentally installed a video driver that does not work with my computer.  What can I do, other than a complete reinstall if possible, to restore my computer to the original video driver.

I do not know how to check out what is going on.  When I start from my original installation CD the display works.  When I start from my hard drive it looks OK at first, then goes black.

---

### Post by fenian on 2008-12-15
Does it go completely black or is there some text?

---

### Post by Tatty on 2008-12-15
Not sure if this still works in intrepid, but I imagine it will:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

That should reset x to its default values on your machine.

I have also heard of 
```
xfix
```

Im not sure what that does, It might just be an alias to the above command

---

### Post by tuxxy on 2008-12-15
> **Tatty said:**
> Not sure if this still works in intrepid, but I imagine it will:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

That should reset x to its default values on your machine.

I have also heard of 
```
xfix
```

Im not sure what that does, It might just be an alias to the above command

xfix is the option to select when you boot into emergency mode to reconfigure the xserver-xorg, so either do that or run the command Tatty listed and you will have just have to activate your old driver

---

### Post by wheelerrver on 2008-12-15
How do I know what the original driver was when I installed.  I do not know what I accidentally installed!  Just didn't look carefully at what I was doing, so I don't know what to go back to.

---

### Post by tuxxy on 2008-12-15
Once you have reconfigured the xserver, navigate to system >> admin >> hardware drivers and there should be one recommended for you to activate here.

---

### Post by wheelerrver on 2008-12-15
When I go to the hardware drivers it tells me I have none on the computer.  What now?

---

### Post by Tatty on 2008-12-15
What is your graphics card?  
You will only need to install drivers for it if it is a more recent ATI or NVIDIA card and you want to utilise their advanced features, as these drivers are proprietry and so they cant be installed be default in ubuntu.

If you are using an older ati or nvidia or another sort of gfx card then you will already be running the open source drivers for them.

---

### Post by wheelerrver on 2008-12-15
This is an older card, and I just want to make sure all the correct drivers that came with Intrepid are installed and any other drivers are uninstalled.  How can I do that.

---

### Post by Tatty on 2008-12-15
First we need to know what your card is so we can figure out what drivers it should have, can you post the output of:
```
sudo lshw -C display
```

---

### Post by wheelerrver on 2008-12-15
This is what I get:

 *-display UNCLAIMED     
       description: VGA compatible controller
       product: NV17 [GeForce4 420 Go]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a3
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 bus_master cap_list
       configuration: latency=64 maxlatency=1 mingnt=5

---

### Post by Tatty on 2008-12-15
How did you install the driver that made things go bad?

---

### Post by wheelerrver on 2008-12-15
I was checking system - administration - drivers, and it showed an NVIDEO driver, I think, so I had it do the install...  really don't know what I was thinking.  Now nothing shows as being installed, so I really don't know what happened there.  Just know that when I start the computer normally the Ubuntu logo shows up and it looks like it is loading.  The screen then goes black, but I can hear the sounds as if the load is going normally.  Screen never comes back.

---

### Post by Tatty on 2008-12-15
> **wheelerrver said:**
> I was checking system - administration - drivers, and it showed an NVIDEO driver, I think, so I had it do the install...  

You did the right thing.  It will only display drivers which are appropriate for your system, so that should have worked.

Sorry, i thought you had got past the blank screen problem.  Boot into recovery mode (available in the grub menu).
Then when you are at the command prompt run:

```
dpkg-reconfigure --phigh xserver-xorg
```

---

### Post by wheelerrver on 2008-12-16
Alas, in trying to use the dpkg-reconfigure command I managed to type it in wrong, make additional typing errors while trying to fix the first mistake, and then somehow run my erroneous entry.  

After that I could not get the Ubuntu on the hard drive to boot at all.  I just went ahead and reinstalled from the start. Now I am back in business.  Just having to reload the programs, bookmarks, contact info, etc.  I noticed however, that when I go to system > administration > hardware drivers it recommends installing NVIDIA Accelerated Graphics Driver (version 96).  I suspect this is what was showing on my previous effort that destroyed my graphics altogether.  I am certainly not going to try it again now.  Maybe someday when I know more.  I'll just work with the more primitive graphics that I have today.

---

