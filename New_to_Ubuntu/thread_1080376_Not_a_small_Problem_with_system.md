---
title: "Not a small Problem with system"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by gotanothergrot on 2009-02-25
Somethings bad and i can't fix .

1. Desktop doesn't load
2. Nothing will play (music)
3. When i shut down (warnings)

please help me get ubuntu back as it should be, i do _not_ want to start booting vista and lots of my friends know i prefer linux (which i do) so i need to save face....

---

### Post by llamabr on 2009-02-25
So what happens when you boot?

Note also that you'll get better replies with a more descriptive subject.

As a last resort, probably you could do a fresh install, rather than giving up altogether.

---

### Post by gotanothergrot on 2009-02-25
Boot takes a little longer than usual, then when i get my desktop my shortcuts are missing.

I cannot drag anything to my desktop including the contents of my desktop folder.

---

### Post by stim on 2009-02-25
Sounds like you broke something with X.  Open a terminal and do the following.  You can also try selecting "failsafe" session from the sessions menu on the login screen, and see what errors that returns to you. (pasting them here would be good)

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by gotanothergrot on 2009-02-25
Thanks, 
what should i do (screen shot)

---

### Post by stim on 2009-02-25
Follow the instructions in the interactive menu for reconfiguring your system. For now, don't use the framebuffer device. All options are fine to leave at their defaults for now, unless its obvious that you need to change them.

---

### Post by gotanothergrot on 2009-02-25
I dont understand!

---

### Post by stim on 2009-02-25
Sorry, I suppose I could have been clearer. 
1) In the window that pops up when you execute the command I first sent you, follow the on-screen prompts (if you need to move the highlighted box, I think the arrow keys or 'shift' will do it)

2) Skip to around 1:26 in the video below, and watch as the user from the video does the same thing that you will be doing.  

3)Unless you have a nVidia card, dont select the nvidia driver as he is doing.  I am just posting this as a resource for you to see what is supposed to happen.  

4)when done, exit your session (ctrl + alt + backspace + backspace) and login again. 

5)Problem should be fixed. 

[http://www.youtube.com/watch?v=2QsP8GDTpno]("http://www.youtube.com/watch?v=2QsP8GDTpno")

---

### Post by gotanothergrot on 2009-02-25
This is where i got by just following the prompts, i didn't alter anything, how do i submit/highlight 'OK' to continue.

---

### Post by Therion on 2009-02-25
Use the "TAB" key.

---

### Post by gotanothergrot on 2009-02-25
now what?

---

### Post by Therion on 2009-02-25
You reboot your PC (and hope that your x-server has been staightened out by re-writing the config file).

Good luck!

---

### Post by gotanothergrot on 2009-02-25
Did the reboot, I have not fixed it but i have somehow altered my keyboard, now i cannot get the *at *key :(

---

### Post by jakupl on 2009-02-25
> **gotanothergrot said:**
> Did the reboot, I have not fixed it but i have somehow altered my keyboard, now i cannot get the *at *key :(

Go to System --> Preferences --> Keyboard. and fix the keyboard issue there.

---

### Post by gotanothergrot on 2009-02-25
Thanks, keyboard should be OK,
I still need to get system working as it should..

---

### Post by stim on 2009-02-25
If reconfiguring X did not solve the problem, think back to the last thing you did. Did you install updates (specifically those to kernel-headers, they tend to break my system on a regular basis), did you install new software?  I would remove the software if thats the case.

Alternatively you could select an older kernel at the grub boot screen, and use that if it doesn't give you problems.

I, personally do not update my kernel/headers. It has tanked my system almost every time I have done it.  While the updates may contain important security fixes, if I cannot use the OS after installing said update,  then it does me no good.

If you are running compiz, that could have gone awry at some point also.  Remove it with the package manager (or if you have the fusion-icon installed, just right click and put your window manager back to metacity)

---

### Post by gotanothergrot on 2009-02-25
> **stim said:**
> think back to the last thing you did. did you install new software?  I would remove the software if thats the case.


Yes, Things went pear shape after i downloaded Kompoze an html editor, within that software i clicked a css theme tab and the desktop grayed out.

 I removed the software but that did not put things right.

---

### Post by stim on 2009-02-25
[https://bugs.launchpad.net/ubuntu/+source/kompozer/+bug/306971](https://bugs.launchpad.net/ubuntu/+source/kompozer/+bug/306971)

Looks like kompozer has some issues with 8.10.  Did you make sure to do "Mark For Complete Removal" rather than "Mark for Removal"?

Boot into an earlier kernel.  If that solves it, use the earlier kernel.

---

### Post by gotanothergrot on 2009-02-25
Thanks i feel like i'm getting somewhere, i can't remember doing a complete removal as for kernals i remove all earlier ones in synaptic some months ago

---

### Post by gotanothergrot on 2009-03-01
Desktop doesn't load
 Nothing will play, (music)

And at start up,

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10400090

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

I have the original hardy 8.04.01 install disk, would doing a complete re-install fix the problem?
 I need pointing in the right direction.

---

