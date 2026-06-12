---
title: "How-to update nVidia?"
date: 2010-02-15
forum: New to Ubuntu
---

### Post by lockalidiot on 2010-02-15
Hi again guys and girls!

I've been having a little issues with my GeForce GT 220 and I thought of updating the drivers for it, just in case. The trouble is, I can't find what I need from synaptic or software center. So, I downloaded(I know, it's not the linux way, but I couldn't find it from repos!) the driver from nVidia homesite. Now, I have a .run file lying around in my "downloads" and I have no idea what to do with it.

---

### Post by NightwishFan on 2010-02-15
You have to install using the command line. Uninstall any proprietary Nvidia drivers you have now before you attempt this. When you have to type the name of the nvidia installer, you can use the "tab" key to autocomplete the exact name. You should print this howto, as to install Nvidia you need to have the GUI disabled, and cannot see a screen.

[LIST=1]
[*]Move the .run installer to your desktop and log out
[*]Press CTRL+ALT+F5 to get to a command line.
[*]Type this command: ```
sudo stop gdm
```
[*]Type this command: ```
cd /Desktop
```
[*]Then type this command: ```
sudo sh NAMEOFNVIDIAINSTALLER.run
```
[*]Follow the instructions. Just hit "Yes" to every question.
[*]When it is done, press CTRL+ALT+Delete to reboot. If it does not work, then you can boot to recovery mode to repair.
[/LIST]

---

### Post by Peter09 on 2010-02-15
Try using envyng (its in the repos). I believe it will download the latest nvidea drivers and install them for you.

---

### Post by bruno9779 on 2010-02-15
I have been doing what NightwishFan says for a while, and it works fine untill you get a kernel update and you have to do it again.

I have asked the same question a while ago: 

[http://ubuntuforums.org/showthread.php?t=1380026](http://ubuntuforums.org/showthread.php?t=1380026)

that is the best solution, install Nvidia ppa and never worry about your nvidia drivers again

@ peter09

I have tried using envyng, but it pulls an older driver version, that does not work with regnum (at least it did 4 months ago)

---

### Post by NightwishFan on 2010-02-15
The PPA may be a good option for when you have a new kernel.

---

### Post by philinux on 2010-02-15
> **bruno9779 said:**
> I have been doing what NightwishFan says for a while, and it works fine untill you get a kernel update and you have to do it again.

I have asked the same question a while ago: 

[http://ubuntuforums.org/showthread.php?t=1380026](http://ubuntuforums.org/showthread.php?t=1380026)

that is the best solution, install Nvidia ppa and never worry about your nvidia drivers again

@ peter09

I have tried using envyng, but it pulls an older driver version, that does not work with regnum (at least it did 4 months ago)

+1

```
sudo add-apt-repository ppa:nvidia-vdpau
```

---

### Post by lockalidiot on 2010-02-15
Thank you all for answers!
I'll try the PPA first and then, depending on the result, I'll do or not do as NightwishFan advised.

We'll see how this goes.

---

