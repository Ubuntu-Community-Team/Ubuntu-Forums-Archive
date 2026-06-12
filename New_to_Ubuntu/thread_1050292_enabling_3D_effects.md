---
title: "enabling 3D effects"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by Tmoney1309 on 2009-01-25
I'm brand new to Ubuntu, I have Ubuntu 8.04. I was wondering how to enable the 3D desktop feature(Linux Cube).

---

### Post by SunnyRabbiera on 2009-01-25
Well step 1 is to learn how to install packages, so we can help faster.
The application you need is called compizconfig-settings-manager, now there are a few ways to do this but because you are fresh may i direct you here:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

its a place to downlaod ubuntu's main packages, just type in what i said above and select the version you are using from the pulldown labeled distribution.
it should be easy from there on in, its similar to download.com

---

### Post by MikeBrown on 2009-01-25
> **overdrank said:**
> Hi and welcome, Have you looked at the FAQ's here  [The Great Desktop Effects FAQ of 2009]("http://ubuntuforums.org/showthread.php?t=809695")
Also your graphics card may need drivers. :)


Quoted from this thread: [http://ubuntuforums.org/showthread.php?t=1050197](http://ubuntuforums.org/showthread.php?t=1050197)

---

### Post by pi.boy.travis on 2009-01-25
> **SunnyRabbiera said:**
> Well step 1 is to learn how to install packages, so we can help faster.
The application you need is called compizconfig-settings-manager, now there are a few ways to do this but because you are fresh may i direct you here:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

its a place to downlaod ubuntu's main packages, just type in what i said above and select the version you are using from the pulldown labeled distribution.
it should be easy from there on in, its similar to download.com


You could also use synaptic package manager, a program that allows you to add or remove new packages.  You can find it in System>Administration>Synaptic Package Manager.

Once you have the settings manager installed, you can configure the effects by going to System>Preferences>CompizConfig Settings Manager.

Hope this helps!

---

### Post by Stalker72 on 2009-01-25
**System -> Administration -> Hardware Drivers**. **Activate** the driver, then restart your PC.

Go to **Applications -> Accessories -> Terminal** and run this command:

```
sudo apt-get install compiz compizconfig-settings-manager
```

Press **Enter** and then **y**.

**Applications -> System Tools -> Compiz Fusion Icon**. From there, you can enable and disable effects as you like. You can also customize them. To get the 3D cube, enable **Desktop Cube** and **Rotate Cube**. To access the 3D cube, hold down **Ctrl** and **Alt** (at the same time), then move around with your mouse.

Good luck and welcome to Ubuntu! ;)

Stalker72

---

### Post by SunnyRabbiera on 2009-01-25
> **pi.boy.travis said:**
> You could also use synaptic package manager, a program that allows you to add or remove new packages.  You can find it in System>Administration>Synaptic Package Manager.

Once you have the settings manager installed, you can configure the effects by going to System>Preferences>CompizConfig Settings Manager.

Hope this helps!

Both work about the same way, but I might start referring to ubuntu packages for beginners now as gdebi works like the windows exe installer in a sense

---

### Post by leonardo_neo on 2009-01-25
> 
I'm brand new to Ubuntu, I have Ubuntu 8.04. I was wondering how to enable the 3D desktop feature(Linux Cube).

Watch this tutorial. This will guide you for what exactly you are looking for.

> [http://in.youtube.com/watch?v=Dj2Ml-0B0i8](http://in.youtube.com/watch?v=Dj2Ml-0B0i8)

Best of luck. :D

---

### Post by Tmoney1309 on 2009-01-25
I went to the sight but i dont know how to download it, it says to use Synaptic which I already have, but it doesn't give me the option for download.

---

### Post by leonardo_neo on 2009-01-25
> **Tmoney1309 said:**
> I went to the sight but i dont know how to download it, it says to use Synaptic which I already have, but it doesn't give me the option for download.

Do exactly as this gentleman says........It can't be explained better than this.....

>  Re: enabling 3D effects
System -> Administration -> Hardware Drivers. Activate the driver, then restart your PC.

Go to Applications -> Accessories -> Terminal and run this command:

Code:

sudo apt-get install compiz compizconfig-settings-manager

Press Enter and then y.

Applications -> System Tools -> Compiz Fusion Icon. From there, you can enable and disable effects as you like. You can also customize them. To get the 3D cube, enable Desktop Cube and Rotate Cube. To access the 3D cube, hold down Ctrl and Alt (at the same time), then move around with your mouse.

Good luck and welcome to Ubuntu!

Stalker72
Stalker72 is online now   	Reply With Quote

This will resolve your issue......Even if having some trouble at some point, then do let us know......

---

### Post by Tmoney1309 on 2009-01-25
What driver do I install? There is only one option for a wireless internet driver, which is already installed.

---

### Post by drugon on 2009-01-25
For this effects, make sure if you have the graphics card, the driver for that card is installed. after this is done, go to Applications -> Add Remove Programs

once there, select All Available applications and in the search bar type "compiz"

select "Advanced Desktop Effects Settings" form the results and eneble it to install it. 

after installation go to System -> Preferences and you will see this option so you can configure it as your needs.

also on the lower panel, right click on the desks and select Preferences. once the rows and columns window opens, make columns = 4 for 4 sides of the cube.

Hope this helps.

I have it installed in the same way and it works fine.

---

### Post by geezerone on 2009-01-25
You need to run proprietary graphics drivers to run 3D effects hence you being asked to check hardware drivers as this is where the graphics drivers are if installed.

Do you know what graphics card you have (model and make), e.g. Nvidia 8800GT or ATI 4670?

---

### Post by leonardo_neo on 2009-01-26
> **Tmoney1309 said:**
> What driver do I install? There is only one option for a wireless internet driver, which is already installed.

Don't bother about drivers. Simply go to the next step, that is installation of the Compiz setting manager. You know what you have to do for that, but again,

Go to Applications -> Accessories -> Terminal and run this command:

Code:

> sudo apt-get install compiz compizconfig-settings-manager

Press Enter and then y.

---

### Post by n.ght1ne on 2009-02-02
Okay, here's a question for you guys...I've enabled Desktop Cube and Rotate Cube, as well as 3D Windows, and I still can't get it to work. I've tried alt+ctrl, and still nothing..Any ideas?

---

### Post by geezerone on 2009-02-02
ctrl   alt    <-  or   ->   arrow keys. Also can ctrl   alt   and move mouse. 

You need proprietary drivers for effects to work remember.

---

