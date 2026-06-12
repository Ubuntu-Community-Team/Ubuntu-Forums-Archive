---
title: "Not reading grafphics card?"
date: 2010-03-06
forum: New to Ubuntu
---

### Post by Coh3n on 2010-03-06
Hey,

I have a NVIDIA GeForce 8500 GT graphics card, and it says that it doesn't have to necessary support when I try to go into the Display under System > Preferences.

When I download the drivers from the NVIDIA website and run it, I get this error:
[IMG]http://img651.imageshack.us/img651/9199/screenshotpqa.png[/IMG]

Also notice in the screenshot, NVIDIA X Server Settings says I have the right graphics card.  

Any ideas?

Thanks,
Coh3n

---

### Post by cogier on 2010-03-06
In the "Ubuntu Software Centre" type "NVIDIA" in the search box. You will find various drivers - May sure you pick the correct one.

---

### Post by cgroza on 2010-03-06
You are opening that package with a text editor... thats not the right way.Google "how to install nvidia drivers in ubuntu " and you will find a tutorial.

---

### Post by dnairb on 2010-03-06
I am running the same NVidia GPU chip.
Go to System > Administration > Hardware Drivers and choose the "Version 180"
This will download and install the drivers. After rebooting, all should be good.

---

### Post by Coh3n on 2010-03-06
> **cgroza said:**
> You are opening that package with a text editor... thats not the right way.Google "how to install nvidia drivers in ubuntu " and you will find a tutorial.
Lol, I guess that is a problem. XD

> **dnairb said:**
> I am running the same NVidia GPU chip.
Go to System > Administration > Hardware Drivers and choose the "Version 180"
This will download and install the drivers. After rebooting, all should be good.
I don't have a version 180.  I have 173, and 185 ~ 173 was activated, when it said 185 was recommended.  So I'm downloading and installing 185, and we'll see how it goes.

EDIT: It didn't work, I still have the same error.  Also, when that error message box comes up, I click no, and another window pops up called "Display Preferences".  In this window, it says my monitor is unknown.  Any more ideas?

[IMG]http://img715.imageshack.us/img715/4085/screenshot1is.png[/IMG]

EDIT: Oh, if it matters, I have visual effects on extra, so I don't see why my driver's wouldn't support the "Display" feature.

---

### Post by sandyd on 2010-03-06
Just becasue it says "unknown monitor" in the displays, it doesnt mean that there is a problem with the video card. It simply means that ubuntu does know know what type of monitor it is.

Care to tell us what monitor it is?

and I know that the graphcs drivers are working, becasue you have manged to open the nvidia settings. If the graphics drivers were not working, that settings window would not open in the first place.

---

### Post by Coh3n on 2010-03-06
> **carlee said:**
> Just becasue it says "unknown monitor" in the displays, it doesnt mean that there is a problem with the video card. It simply means that ubuntu does know know what type of monitor it is.

Care to tell us what monitor it is?

and I know that the graphcs drivers are working, becasue you have manged to open the nvidia settings. If the graphics drivers were not working, that settings window would not open in the first place.
That's what I thought also.  I just can't open System > Preferences > Display as it says the graphics driver does not support the necessary extensions to use this tool.  I've used Ubuntu 9.04 way back when it came out, and this feature worked fine.

My monitor is a Dell SE198WFP.  I don't think anything's wrong with the monitor, I just found it odd that it was unknown.

---

### Post by sandyd on 2010-03-06
> **Coh3n said:**
> That's what I thought also.  I just can't open System > Preferences > Display as it says the graphics driver does not support the necessary extensions to use this tool.  I've used Ubuntu 9.04 way back when it came out, and this feature worked fine.

My monitor is a Dell SE198WFP.  I don't think anything's wrong with the monitor, I just found it odd that it was unknown.
in this case, its a bug.
filing it for you right now...

---

### Post by Coh3n on 2010-03-06
> **carlee said:**
> in this case, its a bug.
filing one right now......
Lol oh.  Well at least I know I didn't do anything wrong then. :)

This is off topic, but do you have any idea why when using Skype, my mic wouldn't work.  It's built into my LifeCam VX-5000 webcam.  The video works perfect, just people can't hear me.  EDIT: Nevermind, I got it working. :)

---

