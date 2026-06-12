---
title: "Dual monitor configuration"
date: 2011-08-30
forum: New to Ubuntu
---

### Post by peterson43 on 2011-08-30
I'm having trouble getting a dual monitor configuration to work correctly with Ubuntu 11.04. 

At first I had issues getting the two monitors to display side-by-side. Configuring the monitors using 'Monitors' in System Settings didn't work, but then I figured out that since I have a 512MB AMD RADEON HD 6350 graphics card I needed to use the proprietary Catalyst Control Center to configure my monitors instead. 

Using the Catalyst Control Center eventually worked (sort of). The only problem that I'm having now is that the Launcher is displayed on the wrong monitor. I have two monitors, one small and one big. I have the large monitor on the left and the small one on the right but the launcher is displayed on the small monitor. 

At first I thought that the problem was that the Catalyst Control Center was recognizing my large monitor as #2 and my small monitor as #1. However, I was eventually able to fix that but the launcher still shows up on the small monitor. Does anyone know how to fix this?

I've attached a screenshot of the Catalyst Control Center that shows my monitor configuration.

---

### Post by fugaki on 2011-08-30
I have the same problem, but I am using Nvidia.

I found a solution for my problem, hopefully it will work for you; set the monitors and primary screen up how you want them. You will still end up with the launcher on the wrong screen. Then, run the configuration utility with root privileges.

I believe the program is amdcccle, so try

```
sudo amdcccle
```


Once I do that, the launcher pops to the other screen as soon as it opens.

---

### Post by peterson43 on 2011-08-30
> **fugaki said:**
> 
I found a solution for my problem, hopefully it will work for you; set the monitors and primary screen up how you want them. You will still end up with the launcher on the wrong screen. Then, run the configuration utility with root privileges.

I believe the program is amdcccle, so try

```
sudo amdcccle
```

Once I do that, the launcher pops to the other screen as soon as it opens.

That didn't work. That simply opens the Catalyst Control Center (CCC) with root priveleges (which I was already able to do from System Settings). 

I looked at my configuration a little more inside the CCC and noticed that the order in which the monitors is listed is #2 and then #1 (see the attached picture). Could this be the problem? If so, I can't figure out how to re-arrange the order.

Also, to give people a picture of what my monitors look like with the launcher in the wrong spot, I've also attached a screenshot of that.

---

### Post by peterson43 on 2011-08-30
I'm noticing something else strange going on now. There is a narrow slice of on the left side of my larger monitor that seems to act like its own monitor. When I maximize something on my larger monitor, it gets confined to this narrow slice on the left side. See the attached picture where you can see an extremely narrow window of what is my Firefox browser.

---

### Post by krytorii on 2011-08-30
Hey, just a heads up, if you want to have different windows on each monitor, you'll be best off selecting ubuntu classic at the bottom when you log in. I had a bunch of problems in unity which disappeared when I used the old gnome panel

---

### Post by peterson43 on 2011-08-30
> **krytorii said:**
> Hey, just a heads up, if you want to have different windows on each monitor, you'll be best off selecting ubuntu classic at the bottom when you log in. I had a bunch of problems in unity which disappeared when I used the old gnome panel

That didn't seem to fix it either. In the gnome panel the wrong monitor is still the primary one. (It did seem to fix that narrow little window on the left that had been happening though)

I've seen several older posts of people trying to switch what monitor was recognized as the primary monitor, and none of those forums had a solution so it's not looking so hopeful for me.

---

### Post by Rhizoid on 2011-08-30
Have you tried swapping the signal cables over?  Just a thought...

---

### Post by peterson43 on 2011-08-31
> **Rhizoid said:**
> Have you tried swapping the signal cables over?  Just a thought...

Yeah, swapping the cables over seemed to finally do the trick. It's kind of silly, and I don't know why there isn't an option (in either the System Settings > Monitors or in the Catalyst Control Center) to choose the primary monitor. 

The other issue that I had with the narrow little window on the left screen seemed to be an issue with the Catalyst driver. I uninstalled the proprietary driver and went with the open source driver for my graphics card instead. Now everything seems to be running smoothly.

---

