---
title: "1680x1050 isn't there."
date: 2009-08-08
forum: New to Ubuntu
---

### Post by KadirÖ on 2009-08-08
I have a neovo 1680x1050 resolution wide screen, and it seems that ubuntu doesn't wanna do this resolution?

My graphics card is Nvidia GeForce 8400, if that helps any?

---

### Post by Vakman on 2009-08-08
Are you sure your drivers are installed properly. 
The easiest way to check is to check if direct rendering is working, post the output of
```
glxinfo | grep direct
``` please.

---

### Post by KadirÖ on 2009-08-08
```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```

---

### Post by Joeb454 on 2009-08-08
Do you have the Nvidia restricted drivers installed? That output would suggest you don't - which would explain the missing resolution

---

### Post by KadirÖ on 2009-08-08
I don't know. How do I install them? :D

---

### Post by Vakman on 2009-08-08
As I thought, usually the reason when a resolution is the driver is likely not installed correctly. Hm, strange output though. But nevermind that for now. Open terminal:
```
sudo apt-get --purge remove nvidia-glx
``` - to remove any lingering (if any) drivers.
Next we need to download the drivers from nVIDIA.
This [link]("http://www.nvidia.com/object/linux_display_ia32_185.18.31.html") if you have a x86 system.
This [link]("http://www.nvidia.com/object/linux_display_amd64_185.18.31.html") if you have a x64 system. Download link is at the bottom of each page.
Follow Step 2 + 3 at the bottom of that page and things should work out. (Step 3 shows you how to install them)

---

### Post by KadirÖ on 2009-08-08
> **Thisislaw said:**
> As I thought, usually the reason when a resolution is the driver is likely not installed correctly. Hm, strange output though. But nevermind that for now. Open terminal:
```
sudo apt-get --purge remove nvidia-glx
``` - to remove any lingering (if any) drivers.
Next we need to download the drivers from nVIDIA.
This [link]("http://www.nvidia.com/object/linux_display_ia32_185.18.31.html") if you have a x86 system.
This [link]("http://www.nvidia.com/object/linux_display_amd64_185.18.31.html") if you have a x64 system. Download link is at the bottom of each page.
Follow Step 2 + 3 at the bottom of that page and things should work out. (Step 3 shows you how to install them)

When I did:
```
sudo apt-get --purge remove nvidia-glx
```

It output this:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Then I downloaded the nvidia driver from that page you wrote. Then I did, as they say on the page:
```
sh NVIDIA-Linux-x86-185.18.31-pkg1.run
```

But it said:
```
sh NVIDIA-Linux-x86-185.18.31-pkg1.run
```


Any help?

---

### Post by Vakman on 2009-08-08
The line that I told you to put does not matter, I just wanted to make sure that their were no lingering drivers that were going to hurt later :P
Anyway, do it with "sudo sh" instead of just "sh". And to make it easier you can just drag the file from your desktop or wherever it is saved. 
```
sudo sh "dragfilehere"
``` then just go from there.

---

### Post by KadirÖ on 2009-08-08
It nearly worked..
But now this came up, hahah :D

[IMG]http://i27.tinypic.com/xdfu2u.png[/IMG]

And if you click ok, this text comes up:
```
You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at www.nvidia.com.
```

---

### Post by Vakman on 2009-08-08
All right... the driver should be supported as long as you are sure it is an 8400. It is not a 8400m, for mobile is it?
Next, I guess we have to end the X-server for the driver to install. Try stopping the X-Server first then install the driver if possible.
```
sudo /etc/init.d/gdm stop
```

---

### Post by KadirÖ on 2009-08-08
Yes i'm sure it's a Nvidia GeForce 8400.
Also the command you gave me, just shut the OS down :D

---

### Post by Vakman on 2009-08-08
Yeah. That would be good if we had the driver installed. That would stop the X-Server. 
I found this howto, rather than me typing a bunch of commands one after another :lolflag:
[http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400)
Alternative option: would be to use EnvyNG but I find this does not always work well. But you are free to try. 
[http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A) but you may as well just follow that Howto. It is very well done.

---

### Post by KadirÖ on 2009-08-08
Already tried EnvyNG, it didn't work.
Also that tutorial.. I don't know, it just didn't seem to work for me.

The part:
```
sudo install NVIDIA-Linux-185.18.pkg.run /usr/src
sudo ln -s /usr/src/NVIDIA-Linux-185.18.pkg.run /usr/src/nvidia-driver
```

Because when I do sudo install NVIDIA-Linux-185.18.pkg.run /usr/src, it says that it couldn't find the file, even if it is in /usr/src..

---

### Post by Vakman on 2009-08-08
> **KadirÖ said:**
> Already tried EnvyNG, it didn't work.
Also that tutorial.. I don't know, it just didn't seem to work for me.

The part:
```
sudo install NVIDIA-Linux-185.18.pkg.run /usr/src
sudo ln -s /usr/src/NVIDIA-Linux-185.18.pkg.run /usr/src/nvidia-driver
```

Because when I do sudo install NVIDIA-Linux-185.18.pkg.run /usr/src, it says that it couldn't find the file, even if it is in /usr/src..

Just to be sure on what you have can you post the output of ```
lspci
```
Also what happens when you try to enter those lines?

---

### Post by ibuclaw on 2009-08-08
> **KadirÖ said:**
> Already tried EnvyNG, it didn't work.
Also that tutorial.. I don't know, it just didn't seem to work for me.

The part:
```
sudo install NVIDIA-Linux-185.18.pkg.run /usr/src
sudo ln -s /usr/src/NVIDIA-Linux-185.18.pkg.run /usr/src/nvidia-driver
```

Because when I do sudo install NVIDIA-Linux-185.18.pkg.run /usr/src, it says that it couldn't find the file, even if it is in /usr/src..

Did you go through the tutorial from the start?
From looking at that, I see that it is mine. :)

I've just had a quick review of this thread, and you have downloaded: NVIDIA-Linux-x86-185.18.31-pkg1.run is that correct?

If so, what you should do different is
```
sudo install NVIDIA-Linux-x86-185.18.31-pkg1.run /usr/src
sudo ln -fs /usr/src/NVIDIA-Linux-x86-185.18.31-pkg1.run /usr/src/nvidia-driver
```
instead.

Then carry on with the rest of the guide as usual.

Regards
Iain

---

### Post by Vakman on 2009-08-08
> **tinivole said:**
> Did you go through the tutorial from the start?
From looking at that, I see that it is mine. :)

I've just had a quick review of this thread, and you have downloaded: NVIDIA-Linux-x86-185.18.31-pkg1.run is that correct?

If so, what you should do different is
```
sudo install NVIDIA-Linux-x86-185.18.31-pkg1.run /usr/src
sudo ln -fs /usr/src/NVIDIA-Linux-x86-185.18.31-pkg1.run /usr/src/nvidia-driver
```
instead.

Then carry on with the rest of the guide as usual.

Regards
Iain
Ah, hello. That is a great Howto. Just had to put that :P
Let's see if he gets it working now.

---

### Post by 3rdalbum on 2009-08-08
You know, this is the reason why people think Ubuntu is too command-line dependent: People have been telling this user how to manually install the Nvidia driver when it's clear that he hasn't tried going to System > Administration > Hardware Drivers. (he posted the output of a command that showed he didn't have nvidia-glx-180 installed)

And then when he manually installs the Nvidia driver and updates the kernel, the driver will break, and he'll think that Ubuntu's updates are faulty.

Kadiro: There's an easier way. Go to System > Administration > Hardware Drivers. Ubuntu will briefly look for drivers that it knows about, and then give you the option to activate and install the Nvidia driver with just one mouse click. It seems that the other people who were trying to help you, either didn't remember this or thought you had already tried it.

---

### Post by Vakman on 2009-08-08
> **3rdalbum said:**
> You know, this is the reason why people think Ubuntu is too command-line dependent: People have been telling this user how to manually install the Nvidia driver when it's clear that he hasn't tried going to System > Administration > Hardware Drivers. (he posted the output of a command that showed he didn't have nvidia-glx-180 installed)

And then when he manually installs the Nvidia driver and updates the kernel, the driver will break, and he'll think that Ubuntu's updates are faulty.

Kadiro: There's an easier way. Go to System > Administration > Hardware Drivers. Ubuntu will briefly look for drivers that it knows about, and then give you the option to activate and install the Nvidia driver with just one mouse click. It seems that the other people who were trying to help you, either didn't remember this or thought you had already tried it.

I find that this does not usually install the drivers correctly or they do not work well for whatever reason. As such, they come here because that does not work. So I suppose what you said is true "thought you already tried this" to some extent. Not that the downloaded driver is better or anything though. I just find it is not often successful. So if you haven't already, it would be a good idea to try it.

---

### Post by KadirÖ on 2009-08-09
I'll try 3rdalbum's way, and if that doesn't work, I'll try tinivole/thisislaw's way, and if that doesn't work either, I'll install a fresh version of Ubuntu and try again. :D

EDIT: There seems to be no System > Administration > Hardware Drivers...

EDIT2: I tried:
```
sudo install NVIDIA-Linux-x86-185.18.31-pkg1.run /usr/src

```

But then this came out:
```
kadir@kadir-desktop:~$ sudo install NVIDIA-Linux-x86-185.18.31-pkg1.run /usr/srcinstall: cannot stat `NVIDIA-Linux-x86-185.18.31-pkg1.run': No such file or directory

```

ANYTHING WITH PERMISSIONS TO DO? Because before I couldn't move the NVIDIA-Linux.....run thing to usr/src, but then I chowned it via terminal?

---

### Post by Narada on 2009-08-09
** If you haven't already, first make a copy of /etc/X11/xorg.conf before installing anything! **
[quote=KadirÖ]EDIT2: I tried:
```
sudo install NVIDIA-Linux-x86-185.18.31-pkg1.run /usr/src

```

But then this came out:
```
kadir@kadir-desktop:~$ sudo install NVIDIA-Linux-x86-185.18.31-pkg1.run /usr/srcinstall: cannot stat `NVIDIA-Linux-x86-185.18.31-pkg1.run': No such file or directory

```[/quote]
Make sure you're in the same directory as NVIDIA-Linux-x86-185.18.31-pkg1.run before running the command to install it. ex. If you downloaded it to /home/kadir/src you would want to type ```
cd /home/kadir/src
``` to change to that directory before running it.

If sudo install doesn't work try this instead:
```
sudo sh NVIDIA-Linux-x86-185.18.31-pkg1.run
```

Also, you can't run this while X is running. Depending on your version of X, pressing Ctrl+Alt+Backspace can drop you out of X to a terminal from which you can run the above commands. If that key sequence doesn't work you can run the command "sudo init 3" to drop to runlevel 3, which I believe is the equivalent runlevel for Ubuntu. (I'm not 100% sure on that.) If gdm simply restarts X after you kill it you need to kill the gdm process first:
```
ps aux | grep gdm
```
Find the PID associated with gdm,
```
sudo kill <PID>
```
where <PID> is the process number of gdm.

After the driver is installed navigate to /etc/X11/xorg.conf and make sure it's loaded in the config. (If confused, just skip to the "Before you Initiate the Driver" section of the guide that was linked a few posts up.) After xorg.conf is configured to use the nvidia driver you can restart X by typing:
```
gdm
```

---

