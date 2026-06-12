---
title: "Restore original greeter"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by stevebond001 on 2008-12-11
Hi
I have just installed a different login screen (greeter) under Intrepid.  However, since I have rebooted I get a message saying:
**The Greeter application appears to be crashing.  Attempting to use a different one**
I click on OK but just get in an endless cycle with the same message.

Is there any way to reset the greeter from the command line?  If so, what do I need to do?

Thanks very much

---

### Post by Kobalt on 2008-12-11
Hello,

Try to press Alt+F1 to access command line and log-in. Then enter : ```
sudo dpkg-reconfigure gdm
```

---

### Post by kpkeerthi on 2008-12-11
System -> Admin -> Login Window

---

### Post by stevebond001 on 2008-12-11
Thanks Kobalt
I ran the command and got a message saying that the changes will take effect when all current sessions have ended.
I then rebooted but am still getting the same original error message.

Any other ideas?

Thanks very much

---

### Post by stevebond001 on 2008-12-11
> **kpkeerthi said:**
> System -> Admin -> Login Window

kpkeerthi
Thanks for the advice, however I can't get to the gui in the first place, as the greeter isn't presented.

I'm looking for a command I can use to reset the logon screen (greeter) back to its default.

---

### Post by kpkeerthi on 2008-12-11
Press Ctrl + Alt + F1, and then login 
At the prompt, type **startx**. This should get you to gnome session. If starx fails, run this command
```
echo "exec gnome-session" > ~/.xinitrc
``` and then try **startx**.

Once you are back in GNOME session, you could change your greeter from System &#8594; Administration &#8594; Login Window

---

### Post by stevebond001 on 2008-12-11
kpkeerthi
Thanks very much for the reply.  However, I have actually given up with this so I've just re-installed Intrepid.  Bit of a pain but as my /home directory is on another partition I managed to reload it and kept the vast majority of settings.  Just got to re-install my apps now (bit of a pain but not too much work.  Once I've finished I'll image the build with quickstart in case of emergencies....

Would the **startx** command reset the greeter back to its default (you know, the brown one that comes with Intrepid)?  or would it just try and start the xServer?  The problem I have (had) was that I selected a greeter which obviously caused problems, and was trying to reset it back to the default one.

Thanks for the help

---

### Post by kpkeerthi on 2008-12-11
Just copy pasting from my last post:

>>> At the prompt, type startx. **This should get you to gnome session. **

>>> Once you are back in GNOME session, **you could change your greeter from System &#8594; Administration &#8594; Login Window**

---

### Post by Brandon Williams on 2009-01-08
> **kpkeerthi said:**
> Just copy pasting from my last post:

>>> At the prompt, type startx. **This should get you to gnome session. **

>>> Once you are back in GNOME session, **you could change your greeter from System &#8594; Administration &#8594; Login Window**


Actually, this doesn't work, because the 'Login Window' item is only available if GDM is running. If you have a non-functional GDM configuration, you can't use the graphical utility to reconfigure it. [**This thread**]("http://ubuntuforums.org/showthread.php?t=898201&highlight=gdm+cannot+start+the+greeter") explains a possible way to get to the 'Login Window'.

In most cases, if you know that the only reason GDM isn't working is a bad config and you just want to go back to the default, this should work:
```

    $ sudo aptitude purge gdm
    $ sudo aptitude install gdm
```
A reinstall without the purge most likely won't help, because the bad config probably will not be replaced. If you purge, the bad config is gone, so the default config will be restored when you reinstall.

If the problem is the greeter application and you don't want to purge the current config (maybe you've got some other changes there that you don't want to lose), then:
```

    $ sudo nano /etc/gdm/gdm.conf
    Find the line the start with 'Greeter=', and reset it to:
      Greeter=/usr/lib/gdm/gdmgreeter
```
If it's already set that way, then the problem is most likely a bad GDM theme, not a bad greeter.

--Brandon

---

### Post by mayagrafix on 2009-01-08
I'm a total newbie but isn't the GRUB loader emergency option better suited for a situation like this where you cant load the GUI?

In my set up GRUB comes up for about one second giving you the chance to press esc and choose another booting option. Is this not standard in all Ubuntu installs?

---

### Post by albinootje on 2009-01-08
> **stevebond001 said:**
> 
Would the **startx** command reset the greeter back to its default (you know, the brown one that comes with Intrepid)?  or would it just try and start the xServer? 

The answer to your second question (from the quoted text) is yes.

The command "startx" has probably been longer around than any Display Manager (although the display manager xdm is pretty ancient).
The command startx is simply meant to start X.
You would use this if you don't like using a Display Manager, or if you quickly want to experiment with some customized desktop setup.

The session you will use after using "startx" is already defined system wide, unless you create a ~/.xinitrc

Here's an example of a customized ~/.xinitrc :
```

# example .xinitrc assuming that openbox is installed
nautilus &
gnome-panel &
openbox

```

Note : In case the Display Manager is working well, and you want to play around with the "startx" command, you will need to use a different Display for it, like e.g. this :
```

startx -- :1

```

---

### Post by albinootje on 2009-01-08
> **stevebond001 said:**
>  Would the **startx** command reset the greeter back to its default (you know, the brown one that comes with Intrepid)?  or would it just try and start the xServer? 

The answer to your second question (from the quoted text) is yes.

The command "startx" has probably been longer around than any Display
Manager (although the display manager xdm is pretty ancient).
The command startx is simply meant to start X.
You would use this if you don't like using a Display Manager, or if you
quickly want to experiment with some customized desktop setup.

The session you will use after using "startx" is already defined system
wide, unless you create a ~/.xinitrc

Here's an example of a customized ~/.xinitrc :
```

# example .xinitrc assuming that openbox is installed
nautilus &   
gnome-panel &
openbox

```

Note : In case the Display Manager is working well, and you want to play    
around with the "startx" command, you will need to use a different Display
for it, like e.g. this :
```

startx -- :1

```

---

### Post by albinootje on 2009-01-08
> **stevebond001 said:**
> 
Would the **startx** command reset the greeter back to its default (you
know, the brown one that comes with Intrepid)?  or would it just try and
start the xServer? 

The answer to your second question (from the quoted text) is yes.

The command "startx" has probably been longer around than any Display
Manager (although the display manager xdm is pretty ancient).
The command startx is simply meant to start X.
You would use this if you don't like using a Display Manager, or if you
quickly want to experiment with some customized desktop setup.

The session you will use after using "startx" is already defined system
wide, unless you create a ~/.xinitrc

Here's an example of a customized ~/.xinitrc :
```

# example .xinitrc assuming that openbox is installed
nautilus &   
gnome-panel &
openbox

```

Note : In case the Display Manager is working well, and you want to play    
around with the "startx" command, you will need to use a different Display
for it, like e.g. this :
```

startx -- :1

```

---

### Post by albinootje on 2009-01-08
> **stevebond001 said:**
> 
Would the **startx** command reset the greeter back to its default (you
know, the brown one that comes with Intrepid)?  or would it just try and
start the xServer? 

The answer to your second question (from the quoted text) is yes.

The command "startx" has probably been longer around than any Display
Manager (although the display manager xdm is pretty ancient).
The command startx is simply meant to start X.
You would use this if you don't like using a Display Manager, or if you
quickly want to experiment with some customized desktop setup.

The session you will use after using "startx" is already defined system
wide, unless you create a ~/.xinitrc

Here's an example of a customized ~/.xinitrc :
```

# example .xinitrc assuming that openbox is installed
nautilus &
gnome-panel &
openbox

```

Note : In case the Display Manager is working well, and you want to play
around with the "startx" command, you will need to use a different Display
for it, like e.g. this :
```

startx -- :1

```

---

### Post by albinootje on 2009-01-08
> **stevebond001 said:**
> 
Would the **startx** command reset the greeter back to its default (you
know, the brown one that comes with Intrepid)?  or would it just try and
start the xServer? 

The answer to your second question (from the quoted text) is yes.

The command "startx" has probably been longer around than any Display
Manager (although the display manager xdm is pretty ancient).
The command startx is simply meant to start X.
You would use this if you don't like using a Display Manager, or if you
quickly want to experiment with some customized desktop setup.

The session you will use after using "startx" is already defined system
wide, unless you create a ~/.xinitrc

Here's an example of a customized ~/.xinitrc :
```

# example .xinitrc assuming that openbox is installed
nautilus &
gnome-panel &
openbox

```

Note : In case the Display Manager is working well, and you want to play
around with the "startx" command, you will need to use a different Display
for it, like e.g. this :
```

startx -- :1

```

---

