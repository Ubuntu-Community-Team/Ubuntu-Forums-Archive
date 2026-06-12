---
title: "How to install video driver"
date: 2011-08-08
forum: New to Ubuntu
---

### Post by JoeBob9 on 2011-08-08
I want to install Ubuntu on a spare HDD and was gathering drivers, etc.  Since I am new to Ubuntu, I am not sure how to install the driver.  The driver is an nVidia driver that is from their website and is made for Linux 32 bit.  It is in the form of a RUN file.  That is, DRIVERNAME.RUN
Any suggestions?

---

### Post by wojox on 2011-08-08
Why don't you install the one from the repo's?

---

### Post by pqwoerituytrueiwoq on 2011-08-08
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates;sudo apt-get update;sudo apt-get install nvidia-current
```
latest stable driver quick and easy

---

### Post by JoeBob9 on 2011-08-08
Sorry, I currently only speak Windows (but want to change that).  Are you saying I need to type the code listed in a terminal window?

---

### Post by scheibenlosen on 2011-08-08
The short answer is yes. :) You could always open a terminal window and then copy and paste the line in the code box.

---

### Post by beew on 2011-08-08
> **JoeBob9 said:**
> Sorry, I currently only speak Windows (but want to change that).  Are you saying I need to type the code listed in a terminal window?

No. You just need to click "Additional Drivers" and let it detect and install the driver for you (you need to connect to the internet of course) I think it is actually advisable to let Additional Driver detects the version of Nvida driver instead of doing it  from Synaptic or  from the command line (which is the same thing) if you are not sure which version you should use (it may not be Nvidia-current)

 If you are using Unity you can find Additional Drivers by clicking Applications on the Unity bar  and search for it (assuming the default nouveau is good enough for your hardware that unity does load), if you are in the fall back "Classic Desktop" (or Ubuntu 10.10 or 10.04), "Additional Drivers" is under System > Administration from the panel.

 If you want up to date driver you can add the x-swat ppa into your sources list and update. To do this open synaptic package manager and go to Settings > repositories > other software and add the line (click the add dialogue box)>  *[I]ppa*:[/I]ubuntu-*x*-*swat*/x-updates Then reload and check for upgradable softwares (Alternatively you can add X-swat and reload Synaptic first before you use Additional Software then the driver it installs would be automatically up to date)

After installing the driver you need to reboot.

---

### Post by amjjawad on 2011-08-08
[http://www.ehow.com/how_5104522_install-video-drivers-ubuntu.html](http://www.ehow.com/how_5104522_install-video-drivers-ubuntu.html)

[https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Or use: [www.googlubuntu.com](www.googlubuntu.com)

---

### Post by pqwoerituytrueiwoq on 2011-08-08
> **JoeBob9 said:**
> Sorry, I currently only speak Windows (but want to change that).  Are you saying I need to type the code listed in a terminal window?
that would do it giving a terminal command is easer and fsater than giving a guide to do it with the GUI which was given in a above post

---

### Post by amjjawad on 2011-08-08
> **pqwoerituytrueiwoq said:**
> that would do it giving a terminal command is easer and fsater than giving a guide to do it with the GUI which was given in a above post

I respect your opinion but at some point I disagree when it comes to "faster" solution.
IMHO, it's much better to:[COLOR=Black]

[/COLOR]> "Give a man a fish; you have fed him for today.  Teach a man to fish; and you have fed him for a lifetime”

---

