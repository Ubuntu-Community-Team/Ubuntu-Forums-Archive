---
title: "How do I save my NVIDIA driver?"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by theopneustos on 2010-02-04
At first installation of Ubuntu 9.10 on my HP Pavillion 5000 laptop, I could not use my 19"  flatscreen. Then somebody gave me the following advise, which works well: ( I am pasting the advise from another thread below)

System > Admin > Synaptic

settings tab:
Repositories

Other software > add
paste ppa:nvidia-vdpau/ppa

reload

search for nvidia-190

mark for install


I did that, it works well. But the problem is as follows: When I restart my machine, the screen settings for the flatscreen is lost. Then i have to redo the whole process of starting System > Preferences > Display and reconfigure the screen settings. It just doesn't want to save the settings. What to do? I am very new, so please be spesific? Thanks

---

### Post by wojox on 2010-02-04
You want to open a terminal and use 

```
gksudo nvidia-settings
```

---

### Post by doas777 on 2010-02-04
if you are using an nvidia card with an nvidia driver, then instead of using the standard display config, hit alt+f2 and run:
```
gksu nvidia-settings
```it is important that nvidia-settings gets run as admin (with gksu), so it can update your system persistently; otherwise you lose the settings on reboot.

---

### Post by ibuclaw on 2010-02-04
Press **Alt+F2** to open the Runcmd box, and paste in:
```
gksudo nvidia-settings
```
And make all changes there.

Then in one of the menus, there should be "Save X Configuration".

Click it, then logout/login to see if it sticks.

Regards
Iain

---

### Post by theopneustos on 2010-02-04
> **wojox said:**
> You want to open a terminal and use 

```
gksudo nvidia-settings
```
I do not have a problem reaching the nvidia settings configuration window. The problem is that i get a message (when attempting to save the settings) which is as follows:

Failed to parse existing X config file '/etc/X11/xorg.conf'!

What to do then?

---

### Post by howefield on 2010-02-04
In terminal type

```
sudo rm /etc/X11/xorg.conf
```

Then try again to save.

---

### Post by doas777 on 2010-02-04
> **theopneustos said:**
> I do not have a problem reaching the nvidia settings configuration window. The problem is that i get a message (when attempting to save the settings) which is as follows:

Failed to parse existing X config file '/etc/X11/xorg.conf'!

What to do then?


well the best bet is to run this command to backup your xorg.conf and remove the original:
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf-backup20100204

```

you can also try 
```

sudo nvidia-xconfig

``` but usually I have to delete the file anyway.

---

### Post by wojox on 2010-02-04
Try:

```
sudo mv /etc/X11/xorg.conf.orginal
```

Then:

```
gksudo nvidia-settings
```

If it asks where to save tell it

```
/etc/X11/xorg.conf
```

---

### Post by theopneustos on 2010-02-04
> **doas777 said:**
> if you are using an nvidia card with an nvidia driver, then instead of using the standard display config, hit alt+f2 and run:
```
gksu nvidia-settings
```it is important that nvidia-settings gets run as admin (with gksu), so it can update your system persistently; otherwise you lose the settings on reboot.
I did what you said, (hit alt+f2 and run:  [CODE]gksu nvidia-settings )  
but after typing what you said, I hit the run command in the screen, nothing happened.Sorry, i am still very inexperienced, have to be fed spoon by spoon...

---

### Post by theopneustos on 2010-02-04
> **wojox said:**
> Try:

```
sudo mv /etc/X11/xorg.conf.orginal
```Then:

```
gksudo nvidia-settings
```If it asks where to save tell it

```
/etc/X11/xorg.conf
```
I did this, but it replies the following:
Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

What now?

---

### Post by doas777 on 2010-02-04
> **theopneustos said:**
> I did what you said, (hit alt+f2 and run:  [CODE]gksu nvidia-settings )  
but after typing what you said, I hit the run command in the screen, nothing happened.Sorry, i am still very inexperienced, have to be fed spoon by spoon...

I hope you tried it after I corrected my spelling mistake. I am in a nautilus thread as well, and accidentially typed it as nautilus-settings instead of nvidia-settings.

if 'gksu nvidia-settings' is not asking you for your password, then somthing is not right. is it asking?

---

### Post by ibuclaw on 2010-02-04
> **theopneustos said:**
> I did this, but it replies the following:
Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

What now?

That sounds like a warning message to me.

Check /etc/X11/xorg.conf (you can browse there).

The file should exist.

---

### Post by doas777 on 2010-02-04
> **theopneustos said:**
> I did this, but it replies the following:
Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

What now?

lol. chicken->egg

I think nvidia is trying to back up your existing file to that name, but there is already a file there.

rename xorg.conf.backup to somthing else. doesn't matter what as long as it isn;t xorg.conf, or xorg.conf.backup.

nvidia shoudl really use a timestamp when they backup.

---

### Post by theopneustos on 2010-02-04
> **doas777 said:**
> well the best bet is to run this command to backup your xorg.conf and remove the original:
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf-backup20100204

```you can also try 
```

sudo nvidia-xconfig

``` but usually I have to delete the file anyway.
I removed the original. Am I still to save the settings in the Nvidia settings?

---

### Post by doas777 on 2010-02-04
> **theopneustos said:**
> I removed the original. Am I still to save the settings in the Nvidia settings?
yep. everything we have mentioned here, is designed specifically to get nvidia to save into that file. once that is done, hopefully your problem is gone.

---

### Post by theopneustos on 2010-02-04
> **doas777 said:**
> yep. everything we have mentioned here, is designed specifically to get nvidia to save into that file. once that is done, hopefully your problem is gone.
Ok, now when I tell it to save in X configuration file, it wants me to browse for a location to save the file. To which file must I save?

---

### Post by doas777 on 2010-02-04
> **theopneustos said:**
> Ok, now when I tell it to save in X configuration file, it wants me to browse for a location to save the file. To which file must I save?
/etc/X11/xorg.conf

note that the x in X11 is capital

---

### Post by theopneustos on 2010-02-04
> **doas777 said:**
> /etc/X11/xorg.conf

note that the x in X11 is capital
While waiting for a reply, I restarted my laptop to see if there is any change. Now my flatscreen doesn't work again. When I start the nvidia displau manager, it gives the following message:
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

What am i to do now?

---

### Post by doas777 on 2010-02-04
> **theopneustos said:**
> While waiting for a reply, I restarted my laptop to see if there is any change. Now my flatscreen doesn't work again. When I start the nvidia displau manager, it gives the following message:
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

What am i to do now?


ok then. go to system -> Administration-> hardware drivers, and see if a driver is available for your card. if so, enable it, and reboot

when you are done rebooting, hit alt+f2, and run 'gksu nvidia-settings' again.

do not reboot until the settings are saved, or you will have to reinstall the driver, or manually edit the xorg.conf. considering all the trouble we've had with the comparitively minor nvidia-settings config, I'd say maunal editing shoudl be our last resort.

---

### Post by theopneustos on 2010-02-04
> **doas777 said:**
> ok then. go to system -> Administration-> hardware drivers, and see if a driver is available for your card. if so, enable it, and reboot

when you are done rebooting, hit alt+f2, and run 'gksu nvidia-settings' again.

do not reboot until the settings are saved, or you will have to reinstall the driver, or manually edit the xorg.conf. considering all the trouble we've had with the comparitively minor nvidia-settings config, I'd say maunal editing shoudl be our last resort.
Thanks for your kindness. i did everything just as you said. It saved. Should I restart now to see, or is there a way to find out if it's ok without starting?

---

### Post by theopneustos on 2010-02-04
Thank you, doas777. I restarted, everything works fine. Now i can enjoy my 9.10 Christian Edition much better! Keep upt he good advice...

---

### Post by Troya.one on 2010-02-06
such problem.new xorg.conf file, after rebooting - resolution seems to be fine on ubuntu welcome screen, but then it changing to old one...any ideas

---

