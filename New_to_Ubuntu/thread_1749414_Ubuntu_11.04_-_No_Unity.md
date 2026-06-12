---
title: "Ubuntu 11.04 - No Unity?"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by ctyonahl on 2011-05-04
Hi,

When I upgraded to 11.04 and logged in for the first time, something popped up that said my graphics card wasn't good enough to run Unity, so it was disabled. I recently got my graphics card working (some bugs in v10 stopped it from working properly). But when I go to CompizConfig Settings Manager it indicates that Unity is enabled. But when I click the Ubuntu Applications menu, everything looks the same as it did in v10. No cool looking menus like I've seen in screenshots. Please help, the Unity UI looks sooo cool and I want to try it out.

Thanks,
Josh

---

### Post by underdog512 on 2011-05-04
You will have to switch Desktop environments.  Log out and as you are logging back in you will notice a drop down  menu at the bottom of the login page. It probably says something like "Ubuntu Classic" Change it to "Ubuntu" and continue logging in.

---

### Post by ctyonahl on 2011-05-04
> **underdog512 said:**
> You will have to switch Desktop environments.  Log out and as you are logging back in you will notice a drop down  menu at the bottom of the login page. It probably says something like "Ubuntu Classic" Change it to "Ubuntu" and continue logging in.

That's just the thing! I AM logged in with "Ubuntu", not "Ubuntu Classic"!!

---

### Post by Blasphemist on 2011-05-04
Try running this to see if the system see's your system as unity capable.

```
/usr/lib/nux/unity_support_test -p
```

It comes from this.

[https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements](https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements)

---

### Post by ctyonahl on 2011-05-04
Here is the code:

```
OpenGL vendor string:   Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R100 (RV200 4C57) 20090101 x86/MMX/SSE2 TCL DRI2
OpenGL version string:  1.3 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          no
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        no
GL fragment program:      no
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       no

Unity supported:          no

```

So, there is no hope? :(

---

### Post by tkelito on 2011-05-04
What graphics card and specs are you running?  I ran Unity with no issue on an integrated Intel GMA4500 Chipset... which is like a bicycle compared to most any graphics processing out there.  

Secondly Unity has a lot more hoops to get through before it will be ready, I have since defaulted back to KDE as my GUI.

---

### Post by ctyonahl on 2011-05-04
> **tkelito said:**
> What graphics card and specs are you running?  I ran Unity with no issue on an integrated Intel GMA4500 Chipset... which is like a bicycle compared to most any graphics processing out there.  

Secondly Unity has a lot more hoops to get through before it will be ready, I have since defaulted back to KDE as my GUI.

Here is the code from sudo lshw -C display:

```
*-display               
       description: VGA compatible controller
       product: Radeon Mobility M7 LW [Radeon Mobility 7500]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=66 mingnt=8
       resources: irq:11 memory:e8000000-efffffff ioport:3000(size=256) memory:d0100000-d010ffff memory:d0120000-d013ffff
```

---

### Post by Thopkins123 on 2011-05-04
Go to install drivers and install one, it's that easy:D

---

### Post by Blasphemist on 2011-05-04
Not with the current driver it seems. How did you fix the recent issues? Did you install another driver that got replaced by the upgrade? Can you re-implement the solution you used before? Please post the result of this code.

```
sudo lshw -C video
```

---

### Post by ctyonahl on 2011-05-04
> **Thopkins123 said:**
> Go to install drivers and install one, it's that easy:D

System-->Administration-->Additional Drivers

"No drivers in use on your system"

---

### Post by ctyonahl on 2011-05-04
> **Blasphemist said:**
> Not with the current driver it seems. How did you fix the recent issues? Did you install another driver that got replaced by the upgrade? Can you re-implement the solution you used before? Please post the result of this code.

```
sudo lshw -C video
```
```
*-display               
       description: VGA compatible controller
       product: Radeon Mobility M7 LW [Radeon Mobility 7500]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=66 mingnt=8
       resources: irq:11 memory:e8000000-efffffff ioport:3000(size=256) memory:d0100000-d010ffff memory:d0120000-d013ffff
```

The problem that I had with my video card in Ubuntu v10 was that I wanted to install a game and it said my video card was unsoupported. But when I upgraded to 11.04, these two bugs were fixed, and I could play the game without any trouble.

Bug 1: [https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/656100](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/656100)
Bug 2: [https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/602267](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/602267)

---

### Post by Blasphemist on 2011-05-04
Do you have updates turned on? There was an update 4-27 that I think may have an affect on this and it doesn't look like it got into the release but rather daily updates since.

---

### Post by ctyonahl on 2011-05-04
> **Blasphemist said:**
> Do you have updates turned on? There was an update 4-27 that I think may have an affect on this and it doesn't look like it got into the release but rather daily updates since.

Yes, I have updates turned on. When I go to the Update Manager, it says I'm up-to-date.

---

### Post by Blasphemist on 2011-05-04
I've been looking at other threads and sticky's and have an idea from them. Try this please from a sticky.

If I select "older Linux Kernels" (I think that's what it says) from the grub menu and boot to 2.6.37 everything seems to work fine.

---

### Post by Blasphemist on 2011-05-04
The ATI mobility Radeon 7500 only has 64MB of video memory and unity requires 128MB. So it seems you are out of luck. Let's be sure that is what you have and not just what is being reported by the system. What make and model of system do you have?

---

### Post by ctyonahl on 2011-05-04
I have an IBM A31 laptop. Practically a fossil! :P

---

### Post by corncob on 2011-05-04
Try System > Administration > Login Screen and make sure Ubuntu (not Ubuntu Classic) is selected.

---

### Post by ctyonahl on 2011-05-04
I'm OK without having the Unity UI, but I heard somewhere that computers not using it will be unsupported for new updates in the future? Is that true?:confused:

---

### Post by ctyonahl on 2011-05-04
> **bkerensa said:**
> You need to find the appropriate driver.

Could you post a link to one?

---

### Post by Blasphemist on 2011-05-04
With only 64MB video memory, you'll never run natty. You'll need to use DE's with lower needs for video memory such as natty modes without 3D or even DE's with lesser needs, LXDE for instance.

---

### Post by ctyonahl on 2011-05-04
OK, looks like I'm out of luck with Unity. Time for a new laptop!:D Thanks for the help, guys.

---

### Post by corncob on 2011-05-05
> **ctyonahl said:**
> I'm OK without having the Unity UI, but I heard somewhere that computers not using it will be unsupported for new updates in the future? Is that true?:confused:

Yea, but I think we're okay for now -- hopefully till the next release in 11.10 when Unity is more polished.

---

### Post by dwhite on 2011-05-05
i had a similar problem with a different computer (would boot directly into ubuntu classic even though i had ubuntu selected and i expected unity) it turns out the video card in that computer would not support unity 3D 

however if you go to synaptic package manager and search on "unity" you will see a package "unity-2D" download it and it will install.  there will be a new option prior to login for unity-2D (i think it was set to default anyway once downloaded but check anyway)

after that i had a nice unity desktop, give it a try

hope this helps  :)

---

### Post by ctyonahl on 2011-05-05
> **dwhite said:**
> i had a similar problem with a different computer (would boot directly into ubuntu classic even though i had ubuntu selected and i expected unity) it turns out the video card in that computer would not support unity 3D 

however if you go to synaptic package manager and search on "unity" you will see a package "unity-2D" download it and it will install.  there will be a new option prior to login for unity-2D (i think it was set to default anyway once downloaded but check anyway)

after that i had a nice unity desktop, give it a try

hope this helps  :)

WOW!! Thanks! I have Unity now!!! :guitar:

Now this thread is REALLY solved! :P

---

