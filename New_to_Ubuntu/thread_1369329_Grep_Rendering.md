---
title: "Grep Rendering"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by phatlarry on 2009-12-31
Quick description:   Installed ubuntu, grep rendering worked correctly.  Had some problems with my partitioning, fixed the issues and reinstalled ubuntu. Now when i run

glxinfo | grep rendering

I get ....

larry@phat:~$ glxinfo | greprendering
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
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
greprendering: command not found



xorg.conf doesn't exist so i can't even try most of the troubleshooting tips i've found when searching for similiar issues.

Any help would be aprpeciated, thanks!

---

### Post by phatlarry on 2009-12-31
I installed ubuntu and do glxinfo | greprendering and it said it was ON....
I then had some issues with my partitions and reisntalled ubuntu and then used the same command and now i get..

```

larry@phat:/etc/X11$ glxinfo | grep rendering
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
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```

I'm pretty sure that nothing during the second installation was changed except that I only created one logical partition within the extended partition instead of two. I can't think of anything else that may have changed and can't figure out what the problem could be. I also can not find my /etc/X11/xorg.conf file.

Any help would be appreciated!

---

### Post by phatlarry on 2009-12-31
I've gotten the xorg.conf created and tried to add the Load GLX section to it and that didn't help me out either... 

I'm pretty sure that nothing had changed between the two installtions and I can't figure out why it's decided to not work during this installation.

---

### Post by overdrank on 2009-12-31
Hi and welcome, please do not create multiple threads on the same issues.
Threads merged.
Have you installed the drivers for your graphics card?

---

### Post by phatlarry on 2009-12-31
I have an on-board Intel 945gm card. Just assumed it was installed automatically.

```

larry@phat:~$ sudo lshw -c video
  *-display:0             
       description: VGA compatible controller
       product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:dc100000-dc17ffff ioport:1800(size=8) memory:c0000000-cfffffff(prefetchable) memory:dc200000-dc23ffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:dc180000-dc1fffff


```


That means it's installed? If not let me know where to check.. been almost four years since using linux.
System -> admin tools -> hardware drivers just gives me a screen with nothing but Software Modem listed

---

### Post by phatlarry on 2010-01-01
So, I just found this in the newly created xorg.conf....

```

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

```


I don't have an nvidia card, it's an oboard intel 945gm graphics card. How would I go about updating my drivers?

---

### Post by Methuselah on 2010-01-01
In situations like this I usually let X configure itself.
Swtich to a text based login with CTRL + ALT + F1.
Enter your login (password will not be echoed but enter it anyway)
[Note that the following step will log you out of your desktop so make sure you've saved/printed anything you want]

Then

```

sudo etc/init.d/gdm stop
sudo X -configure
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo cp /root/xorg.conf.new /etc/X11/xorg.conf 
sudo /etc/init.d/gdm start

```

When your login screen comes back log in and try 
```
glxinfo | grep rendering
```

The space between 'grep' and 'rendering' is important!
If at this point you're worse off than before copy your backed up xorg.conf back with:

```

sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf

```

This is they way I had learned to configure X but maybe there is some preferred GUI method now.

---

### Post by phatlarry on 2010-01-01
Thank you for the help but I can't get to a text based login.

both ctrl alt f1 and gdm stop both take me to a solid black screen that does nothing. I left it alone for atleast 5 minutes with no result. Just a black screen. Also tried password and login/password in the dark. no result. Just a black screen.

---

### Post by Methuselah on 2010-01-01
> **phatlarry said:**
> Thank you for the help but I can't get to a text based login.

both ctrl alt f1 and gdm stop both take me to a solid black screen that does nothing. I left it alone for atleast 5 minutes with no result. Just a black screen. Also tried password and login/password in the dark. no result. Just a black screen.

CTRL + ALT + Fn

where n is any of 1 2 3 4 5 or 6 should work.
You should see a login prompt on at least one of the screens.
The screen will be mostly black with only the login prompt at the very top.
You have to log in at that prompt before you can run any of the other commands.
[By the way, I think that on ubuntu the F7 option will show your desktop again. That is, until you stop gdm]

Basically, your xorg.conf should not be showing nvidia when you have intel graphics.
If you're having trouble with my other suggestion try changing the **Driver** and **VendorName** to "intel" in the section of xorg.conf you copied in a previous post.
This will tell X to use the intel driver (which is already included in just about any Ubuntu installation).
Then you should restart your computer.

---

### Post by dostyvsky on 2010-12-06
I had an intel card that seemed to work better after I ran synaptic and removed everything related to nvidea

---

