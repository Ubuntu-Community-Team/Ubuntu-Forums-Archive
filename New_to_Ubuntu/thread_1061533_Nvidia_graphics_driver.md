---
title: "Nvidia graphics driver"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by JPB666 on 2009-02-05
I need to install a nvidia graphics driver. The computer than runs ubuntu is not internet connected. I downloaded the driver from another computer and copied to the ubuntu computer. But it won't run.
Help!

Thanks

---

### Post by Temposs on 2009-02-05
You need to show what you do to make it run, and what the response of the computer is

---

### Post by OutOfReach on 2009-02-05
What did you try to do?
X must not be running, you have to be in a virtual console.
Just type in 'sh NVIDIA-xxxxx-xxxxx' and it should do the rest

---

### Post by Partyboi2 on 2009-02-05
When you are at the Desktop press Ctrl+Alt+F2 to get to a terminal then stop gdm
```
sudo /etc/init.d/gdm stop
```Then change directory to where you have the nvidia driver, so if its on your Desktop
```
cd ~/Desktop
```then run the installer with
```
 sudo sh NVIDIA-xxxxx-xxxxx
```Once it has finished restart gdm
```
sudo /etc/init.d/gdm start
```and press Ctrl+Alt+F7 to get back to the gui Desktop.

---

### Post by JPB666 on 2009-02-05
It says can't open

---

### Post by JPB666 on 2009-02-05
I was in terminal. Ctrl alt f7 didn't do anything.

---

### Post by JPB666 on 2009-02-06
I did that and message says can't open nvidia XXXX

---

### Post by pissedoffdude on 2009-02-06
Download the latest nvidia driver from another computer and then put it on your desktop.  Then, rename the driver to nvidia.run
Be sure to write down or print the following instructions before proceeding:

Do a Ctrl+Alt+F2 

Then you stop gdm:  
```
sudo /etc/init.d/gdm stop
```

then
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

then 

```
sudo rm /etc/X11/xorg.conf
```

then

```
cd Desktop
sudo bash nvidia.run
```

When the installer asks if would like nvida-xconfig to automatically configure your xorg.conf, tell it yes.

Once it's done, do a ```
sudo reboot
```

And when it reboots, you should have your nvidia driver properly installed.  Good luck!

---

### Post by JPB666 on 2009-02-06
Followed direction and it doesn't recognize file (Xorg.conf). How do I install that?

No matter what i do it 'can't open the Nvidia 180.22. Even after i renamed it to just nvidia.run.
Thanks

---

### Post by pissedoffdude on 2009-02-06
> **JPB666 said:**
> Followed direction and it doesn't recognize file (Xorg.conf). How do I install that?

No matter what i do it 'can't open the Nvidia 180.22. Even after i renamed it to just nvidia.run.
Thanks

Are you capitalizing any letters?  Linux is CaSe SeNsItIvE, so be careful and only capitalize the letters I capitalized in the instructions

---

### Post by JPB666 on 2009-02-06
I should've mentioned this before--ubunto 8.1 is installed. There is no other OS on that machine.

---

### Post by JPB666 on 2009-02-06
I copied exactly. Where do I download the Xorg files?
Thanks

---

