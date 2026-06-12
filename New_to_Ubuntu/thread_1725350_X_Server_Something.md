---
title: "X Server Something"
date: 2011-04-09
forum: New to Ubuntu
---

### Post by rosone on 2011-04-09
Yea, silly topic but I don't even know what's wrong so didn't know what to call it...

...anyway:

I figured I'll give Ubuntu a try, let it run twice from a CD, decided to install it, cleared a HD and did a fresh clean install.

After the install some update stuff did some updating and after it was done I tried to set up my monitors.

In that nvidia panel i set the displays to "seperate", hit apply and ubuntu told me I need to restart x server. So I just quit that nvidia panel thingy and rebooted. After the reboot I found myself in text mode where I have completely no idea what to do... 

Since I figured I might have done something wrong I decided to do another clean install. Long story short, I'm looking at the text mode again and have to idea how to reach my desktop.

What am I supposed to do now? :)

---

### Post by TeoBigusGeekus on 2011-04-09
```
sudo rm /etc/X11/xorg.conf
```
to delete your x server (display) settings) followed by 
```
sudo reboot
```
to reboot.
Once on Ubuntu, open a terminal (Applications>Accessories>Terminal) and give
```
gksu nvidia-settings
```
Give your password and the nvidia settings program will launch.
Do want you want with it, but don't forget to press the "Save changes to X configuration file" (or something like that) before you quit the program.
Reboot and report back.

---

### Post by rosone on 2011-04-09
Thanks for the reply. After the reboot I can see my desktop again (yay). I started the terminal and after using:```
gksu nvidia-settings
```Ubuntu told me that> You do not appear to be using the NVIDIA display driver. Please edit your X configuration file (just run nvidia-xconfig as root), and restart the X server.

---

### Post by TeoBigusGeekus on 2011-04-09
Are you sure your graphics card is an nvidia one?
Post us the output of
```
lshw -C display
```

If you are using nvidia, have you installed the restricted drivers for your card?

---

### Post by Wiebelhaus on 2011-04-09
He should run jockey-gtk first and install any drivers it suggests.

---

### Post by rosone on 2011-04-09
After running```
nvidia-xconfig
``` and rebooting the nvidia control panel works again. I'm using a 8800GT, definitely nvidia. As for the driver, I just clicked on the first one - version 173) and it says that the driver is activated and in use.

I'm guessing my main problem at this point is the inability to set up both my monitors at the same time. I pick their resolutions, I set both to "separate x view", I save the X file and then I'm a bit lost. As I understood it restarting my pc should have applied those settings but it only results in me being in text-mode-only.

This time I tried ctrl+alt+f1 and```
sudo service gdm restart && exit
``` but that didn't have any effect. So I tried```
killall5 && exit
``` after that and eventually rebooted just to find myself back in text-only-land.

I'm confused

---

### Post by TeoBigusGeekus on 2011-04-09
Install the latest driver from Additional Drivers and try again with
```
gksu nvidia-settings
```

---

### Post by rosone on 2011-04-09
Ok, on it. Thanks for the help

**EDIT** I switched the the 2nd nvidia driver on the list and it seems to be working as expected now. Thanks a lot for all the help.

...off to try to install both sound cards now ;]

---

