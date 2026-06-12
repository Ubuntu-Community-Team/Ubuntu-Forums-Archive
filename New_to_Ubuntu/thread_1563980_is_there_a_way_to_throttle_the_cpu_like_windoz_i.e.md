---
title: "is there a way to throttle the cpu like windoz? i.e. performance &amp; power saver?"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by bradmayne04 on 2010-08-29
I was just wondering if I can turn my cpu's performance down when i'm running on battery power?  (i'm on a laptop) it would be great if there was.  I'm on a cheap-0 e-machine and the battery life is terrible. also, is there a way to select which programs come on at boot? I think i read something about a program it might have been called BUM? but then when i did an apt-get it wanted to remove my samba.  I can't have that I need it to print on my home network.

---

### Post by Finalfantasykid on 2010-08-29
I'm pretty sure that the default setting is on demand.  There is an panel applet which allows you to see this and change the mode that it is in.

---

### Post by migs73 on 2010-08-30
Right click on the top panel, select add to panel, click on CPU Frequency scaling Monitor and click add.
Now you have a little display on your panel telling you the current frequency your CPU is running at. Click on it and you should have a list of options, what frequency you wish it to run at, or a named power scheme. NB this is not held after a reboot and it reverts back to OnDemand. :D

Enjoy!!

---

### Post by bradmayne04 on 2010-08-31
> **migs73 said:**
> Right click on the top panel, select add to panel, click on CPU Frequency scaling Monitor and click add.
Now you have a little display on your panel telling you the current frequency your CPU is running at. Click on it and you should have a list of options, what frequency you wish it to run at, or a named power scheme. NB this is not held after a reboot and it reverts back to OnDemand. :D

Enjoy!!

I've been using the CPU frequency scaling monitor for awhile. I never knew much about it.  I took a look at it in depth.  How do you change the cpu settings from it?  I don't see any way at all!

---

### Post by Windows Nerd on 2010-08-31
> **bradmayne04 said:**
> I've been using the CPU frequency scaling monitor for awhile. I never knew much about it.  I took a look at it in depth.  How do you change the cpu settings from it?  I don't see any way at all!

Click on it.

---

### Post by jerome1232 on 2010-08-31
Like this.

---

### Post by Peter09 on 2010-08-31
Try installing "laptop-mode-tools", I gained about an hour by doing that. It sets the kernel up for better power saving.

---

### Post by migs73 on 2010-08-31
Once you have clicked on it select either the frequency you want your CPU to run at (lower uses less power but you get slower performance) or select a power scheme.(I would think powersave if you are trying to extend battery life).

---

### Post by bradmayne04 on 2010-08-31
> **jerome1232 said:**
> Like this.

D'0h!  Now I got it!  Thanks for pointing that out.  Why do the simplest things elude me sometimes? I was clicking on the moving graph that shows stuff like network, cpu, and memory. I clicked on the other icon and boom there it was right in front of me. thanks man.

---

### Post by Matt__ on 2010-08-31
You could always try [Undervolting your CPU ]("http://openmindedbrain.info/09/05/2010/undervolting-in-ubuntu-10-04-lucid-lts/")




[COLOR=White].[/COLOR]

---

### Post by KdotJ on 2010-08-31
powertop

powertop is a program made by Intel that collects data from your CPU that's causing it to wake up, be interrupted and using cycles.  Install it with the old 

 ```
sudo apt-get install powertop
``` 

and then run it as sudo in the terminal...  

sudo powertop

It will then collect data, then tell you the results. Now they may be hard to understand, but the pogram will tell you some keys to press to disable redundant processes or turn them off. 
I managed to get my battery to last 4 hours instead of 1.5 on my netbook. 

Note. After reboot/log out, all will be back to normal and you will have to runs powertop again if you wish to save power again

---

