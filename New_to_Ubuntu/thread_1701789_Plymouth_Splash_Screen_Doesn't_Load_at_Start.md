---
title: "Plymouth Splash Screen Doesn't Load at Start"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by RichieB07 on 2011-03-06
My Plymouth file (under /lib/plymouth/themes/default.plymouth) says:
> [Plymouth Theme]
Name=Paw OS X
Description=OS X like boot splash
ModuleName=script

[script]
ImageDir=/lib/plymouth/themes/Paw-OSX
ScriptFile=/lib/plymouth/themes/Paw-OSX/paw-osx.script


However, when I start my computer up, it loads the Ubuntu 10.10 text with the 4 dots underneath it, like this:
[IMG]http://www.liberiangeek.net/wp-content/uploads/2010/09/perfect_desktop_mav_thumb.png[/IMG]


It's supposed to be like this:
[IMG]http://ubuntuguide.net/wp-content/uploads/2010/09/PAW_OS_X_Plymouth_Theme_by_love2spooge.png[/IMG]


I've installed gnome-splashscreen-manage-0.2-12 and startupmanager.  Neither of these have worked to fix the problem.  Any idea why it's not doing this?


I'm running 10.10 on an Acer Aspire D255 netbook.

---

### Post by grahammechanical on 2011-03-07
Your heading is not correct. The Plymouth splash screen is loading. It is your choice or replacement that is not loading.

I would like to change the splash screen on my machine. I do not like your choice but each to his own. I want the one with the flying Windows (copy right) logo. Only joking.

Is the image in the correct directory?

Regards.

I have just had a look in my plymouth folder. In the Themes folder there is a text file called default.plymouth. In the unbuntu-logo folder there is a ubuntu-log.plymouth text file that has exactly the same text in it as the default.plymouth text file.

Your new screen image would require a default.plymouth file that matches a Paw-OSX.plymouth file in a Paw-OSX foler. Is this the case?

---

### Post by xtremesupremacy3 on 2011-03-07
This is not a problem with your image or Plymouth.

My guess is that you are most likely using a Nvidia graphics card.
Basically it's something extremely trivial.

The pixel size has been incorrectly set.

You can make it better by clicking System, Administration, Start-up manager.

If you can't find it. Use something like Ubuntu Software Centre(?) (Sorry I'm using Linux Mint).

Once inside Start-up manager, look under Display and change the Resolution or depth. For instance, mine is 1024x768 (recommended) and set to 24bits (naturally).

If all is well and you close the application, restart your computer and you should have a better Plymouth experience

---

### Post by RichieB07 on 2011-03-08
> **xtremesupremacy3 said:**
> This is not a problem with your image or Plymouth.

My guess is that you are most likely using a Nvidia graphics card.
Basically it's something extremely trivial.

The pixel size has been incorrectly set.

You can make it better by clicking System, Administration, Start-up manager.

If you can't find it. Use something like Ubuntu Software Centre(?) (Sorry I'm using Linux Mint).

Once inside Start-up manager, look under Display and change the Resolution or depth. For instance, mine is 1024x768 (recommended) and set to 24bits (naturally).

If all is well and you close the application, restart your computer and you should have a better Plymouth experience


I am using a NVidia card.  In the Start-Up Manager, I have my screen set to the same as yours, as that is the largest a netbook can handle. I changed it to the 800x600 and it works just fine now.  Is there some rule where it has to be one size smaller than what the screen is?

Also, how would I go and change the splash screen?

---

### Post by stinkeye on 2011-03-08
To change your plymouth screen...
```
sudo update-alternatives --config default.plymouth
```
```
sudo update-initramfs -u
```


I also had to create this file to see plymouth for longer than a couple of secs.
```
gksu gedit /etc/initramfs-tools/conf.d/splash
```
and add this option 
```
FRAMEBUFFER=y
```
save the file.


Then
```
sudo update-initramfs -u
```


The fix for text only showing in plymouth is to add 
GRUB_GFXPAYLOAD_LINUX="[COLOR="Magenta"]1680x1050[/COLOR]"
[COLOR="#ff00ff"](Using your native resolution.)[/COLOR]

to
```
gksudo gedit /etc/default/grub
```

and then run ```
sudo update-grub
```

---

### Post by RichieB07 on 2011-03-08
> **stinkeye said:**
> To change your plymouth screen...
```
sudo update-alternatives --config default.plymouth
``````
sudo update-initramfs -u
```
I also had to create this file to see plymouth for longer than a couple of secs.
```
gksu gedit /etc/initramfs-tools/conf.d/splash
```and add this option 
```
FRAMEBUFFER=y
```save the file.


Then
```
sudo update-initramfs -u
```
The fix for text only showing in plymouth is to add 
GRUB_GFXPAYLOAD_LINUX="[COLOR=Magenta]1680x1050[/COLOR]"
[COLOR=#ff00ff](Using your native resolution.)[/COLOR]

to
```
gksudo gedit /etc/default/grub
```and then run ```
sudo update-grub
```

Awesome, thank you!

---

