---
title: "[SOLVED] network manager is gone..."
date: 2009-01-03
forum: New to Ubuntu
---

### Post by dsmcginn on 2009-01-03
i accidently removed NM from my toolbar. i tried to right click and hit add to panel, but it's not listed as an option. i also hit alt+f2 and type in nm-applet --sm-disable (an idea i got from another thread) and rebooted and that didnt work. then i tried to go to system-> preferences -> sessions and adding it to the start up list, but it was already there. so i removed it, added it back, rebooted and still got nothing.

any suggestions?

thanks!

=)

---

### Post by AlexBellisBrown on 2009-01-03
Could you try checking it in System-Admin-Services? Is it listed there also?

edit: For me its not listed there.... so actually this might not work.... :S

---

### Post by dsmcginn on 2009-01-03
its not listed as an option.
edit: me neither!

:p

---

### Post by AlexBellisBrown on 2009-01-03
Could this help? [http://ubuntuforums.org/showthread.php?t=676181](http://ubuntuforums.org/showthread.php?t=676181)

---

### Post by 2hot6ft2 on 2009-01-03
System->Preferences->Sessions

Go to "+ Add"

Then fill in the fields as follows:

Name: Network Manager
Command: nm-applet --sm-disable
Comment: Network Manager applet

And click "Save"

Then logout and log back in to and see if you have the applet on your tool bar.

---

### Post by teh_yodeler on 2009-01-03
I've not experienced this problem before, but perhaps if you can go to synaptic, search for "network-manager" and reinstall this may solve your issue?

Just what I would try if it happened to me.

---

### Post by 2hot6ft2 on 2009-01-03
> **teh_yodeler said:**
> I've not experienced this problem before, but perhaps if you can go to synaptic, search for "network-manager" and reinstall this may solve your issue?

Just what I would try if it happened to me.
Removing the applet from the toolbar didn't uninstall it. Just need to recreate the applet.

---

### Post by bump_ on 2009-01-03
Something similar happened to me once. First make sure nm-applet is still running when you reboot by typing this in the terminal

```
 ps -e | grep nm
```

If nm-applet is running, you should see something along the lines of

```
5640 tty1     00:00:01 nm-applet
```

So if nm-applet is indeed running, but not showing up, the problem might be it has no where to show up. Try adding a Notification Area applet to your panel and restart x with CONTROL-ALT-BACKSPACE and see if that helps.

It solved the problem for me.

---

### Post by dsmcginn on 2009-01-04
> **AlexBellisBrown said:**
> Could this help? [http://ubuntuforums.org/showthread.php?t=676181](http://ubuntuforums.org/showthread.php?t=676181)

this worked!!!

=)

thanks!

---

