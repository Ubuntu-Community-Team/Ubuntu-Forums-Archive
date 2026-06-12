---
title: "I think this is an nvidia problem"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by tomislav1 on 2009-02-24
Hey when i install ubuntu it gets to this point:

[http://img49.imageshack.us/img49/4751/installinghardyplus04og3.png](http://img49.imageshack.us/img49/4751/installinghardyplus04og3.png)

Then after that comes this:

[http://img235.imageshack.us/img235/3491/1601091047ki7.jpg](http://img235.imageshack.us/img235/3491/1601091047ki7.jpg)

and when i start it in graphic safe mode it works
I got nvidia geforce fx 5200

and when i try to install it in terminal to change it from vesa to nv it goes back to that colourful screen... or it doesnt change at all.

SPECS:

Manufacturer: Compaq Presario 061 
Processor: Intel(R) Pentium(R) 4 CPU 3.20GHz (2 CPUs) 
Memory: 1024MB RAM 
Hard Drive: 160 GB 
Video Card: NVIDIA GeForce FX 5200 
Monitor: ASUS 19inch
Sound Card: Realtek AC97 Audio
Operating System: Windows XP Home Edition Service Pack 3

---

### Post by balaknair on 2009-02-24
It certainly looks like an issue with the nv nVidia drivers(or a hardware error with the graphics card?).
The nVidia GeForce FX5200 needs the 173.14.12 drivers(closed source, so I think not included on the CD due to licensing issues), and I think you'll need to enable these after installing Ubuntu(install using safe graphics mode, then boot into the install in safe mode, and when prompted, enable the proprietary drivers, restart).

---

### Post by SHANIKAMN on 2009-02-24
Is this operating system kid friendly?

---

### Post by bumanie on 2009-02-24
I know the issues you've been having as you pmed me about it. The only other thing I can think of is doing the following. With this method, the driver will not get updated. You will need the nvidia binary driver downloaded to your desktop. > sudo apt-get remove --purge nvidia-glx-newTo remove all traces of nvidia-glx-new, then ctrl-alt-F1, this will drop you into console mode - login, then > sudo /etc/init.d/gdm stop. Install the driver by > cd ~/Desktop> sudo sh name-of-driver.runthen > sudo /etc/init.d/gdm start then hit ctrl-alt-F7. I think this is the method, it's a long time since I installed a driver this way.

---

### Post by tomislav1 on 2009-02-24
my mate has same nvdia gfx card as me and had no problem.

could it be because i installed from xp desktop not rebooting?

---

### Post by bumanie on 2009-02-24
> **tomislav1 said:**
> my mate has same nvdia gfx card as me and had no problem.

could it be because i installed from xp desktop not rebooting?

Could you explain a little clearer what you mean by > i installed from xp desktop not rebooting?

---

### Post by tomislav1 on 2009-02-24
well i downloaded ubuntu and installed from DESKTOP not a cd.

My friend said he had the same gfx card as me and installed ubuntu when he restarted computer.

could this also work to?

apt-get install envyng-core envyng-gtk

then run it from the "Applications -> System tools " menu

you choose which graphics card NVIDIA or ATI and then choose the driver, then click on Apply.??

---

### Post by bumanie on 2009-02-24
Worth a try. I have never needed to use envy, so can't give any advice. I have installed a GPU the same as yours in the past and had no issues - I'm a bit lost as to why you are having these issues and why every suggested 'fix' is not working. Have you tried xfix from within safe mode? Or else > sudo xfixin terminal. That may work.

---

### Post by tomislav1 on 2009-02-24
no i havent tryed sudo xfix and i havent tryed anything in safe mode

---

### Post by bumanie on 2009-02-24
I suggest you try xfix from within safe mode, it is one of the options in the list.

---

### Post by tomislav1 on 2009-02-24
i wouldnt have a clue how to do that in safe mode..

---

### Post by stchman on 2009-02-24
> **tomislav1 said:**
> Hey when i install ubuntu it gets to this point:

[http://img49.imageshack.us/img49/4751/installinghardyplus04og3.png](http://img49.imageshack.us/img49/4751/installinghardyplus04og3.png)

Then after that comes this:

[http://img235.imageshack.us/img235/3491/1601091047ki7.jpg](http://img235.imageshack.us/img235/3491/1601091047ki7.jpg)

and when i start it in graphic safe mode it works
I got nvidia geforce fx 5200

and when i try to install it in terminal to change it from vesa to nv it goes back to that colourful screen... or it doesnt change at all.

SPECS:

Manufacturer: Compaq Presario 061 
Processor: Intel(R) Pentium(R) 4 CPU 3.20GHz (2 CPUs) 
Memory: 1024MB RAM 
Hard Drive: 160 GB 
Video Card: NVIDIA GeForce FX 5200 
Monitor: ASUS 19inch
Sound Card: Realtek AC97 Audio
Operating System: Windows XP Home Edition Service Pack 3

After Ubuntu installs enable restricted driver.

---

### Post by tomislav1 on 2009-02-24
> **stchman said:**
> After Ubuntu installs enable restricted driver.

i would have to start it in safe graphic mode??

---

### Post by stchman on 2009-02-25
> **tomislav1 said:**
> i would have to start it in safe graphic mode??

Once you install Ubuntu it asks you to reboot.  In the System--->Administration--->Hardware Drivers you can enable the Nvidia driver.

I have 3 PCs with Nvidia cards and the restricted driver works most excellent.

---

### Post by tomislav1 on 2009-02-26
still the same when i put CD in computer when i turned computer on it comes up with menu i click install ubuntu etc

the menu loads i click install etc

then after the orange bar loads that f'ed up screen happens all over again

---

