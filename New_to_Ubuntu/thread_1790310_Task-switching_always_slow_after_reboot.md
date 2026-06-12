---
title: "Task-switching always slow after reboot"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by eHalcyon on 2011-06-24
Hi there,

I'm absolutely new to ubuntu.  I've had some experience with various linux distros before, but as far as administrative work I'm pretty much absolute beginner.

I installed Natty via CD.  Pretty standard stuff.  I found task switching to be excruciatingly slow, something like 2 seconds just to alt+tab, or min/max a window. 

I searched around and found that it's a common problem and I did everything that I could find, tweaking all the relevant CCSM settings (e.g. manually set monitor refresh rate, uncheck sync to  vblank, remove the delay on the static application switcher, probably some other things I've forgotten).  None of it seemed to work.  I kept playing and the problem eventually seemed to resolve itself magically - but it doesn't persist.

The solution that I've found is to enable metacity compositing, reboot, and then disable metacity compositing.  Via the command line, it looks like this:

```
gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool true
gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool false
```Then, alt+tab is near instantaneous.  This is the only thing that I've found to work, but the problem returns if I reboot the machine.  If I then enable and disable the compositing manager without rebooting again inbetween, it stays slow.  If I reboot, it is slow UNTIL I disable the manager.  It's just bizarre.

So my question is two-fold:

1. Why does this and only this sequence of steps work?  I'd really like to understand.
2. Is there something I can do to make the fix permanent?  I don't plan on rebooting the machine often, but it is still very annoying.

Thanks for your help!

**Edit:** I've just found that it isn't only rebooting that causes this - logging in and out does the same.  Logging in and out between enabling and disabling the metacity compositing manager also fixes the issue (temporarily, as with the original case).

**Edit again:** I should add that I am using Classic, not Unity as it isn't supported by my hardware.

---

### Post by Ozymandias_117 on 2011-06-24
1. For some reason compositing is turning itself back on every time you login.

2. At least a temporary fix would be to create a script with those commands and add it to your autostart. 

This would be the script, disable_compositing.sh
```
#!/bin/bash

gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool true
gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool false
```

Then navigate to wherever you saved it and make it executable:
```
chmod +x disable_compositing.sh
```

Then add it to your autostart (I believe it is in System->Preferences->Session but I don't actually use Gnome, so you may have to search a little bit for the location.)

---

### Post by eHalcyon on 2011-06-25
I don't think compositing is turning itself back on.  If it is, the option in gconf-editor isn't showing it.

Is there a way to have a script run at the end of a session?  As I said, the reboot (or log out) is necessary inbetween.  So what I would need is to set compositing to "true" whenever I end the session and then to switch it back to "false" whenever I start a new session.  But toggling it at the start of a session wouldn't help at all.

Thanks for the suggestion!

---

### Post by Ozymandias_117 on 2011-06-25
Sorry. It's really late here and I missed part of what you said, and made an assumption on something I'd seen a while back. :P  I feel like I recall seeing something in GDM's config files that would run on login and logout, but I don't currently have any machines with it installed to mess with it.  Hopefully someone who has more information can help you!

---

### Post by eHalcyon on 2011-06-27
Thanks anyway, Ozymandias.  I will see if I can find a way to get things to run on login and logout.  

Unfortunately, these are still just workarounds.  I'm still curious about the core problem.  Anyone else have any suggestions?

---

### Post by eHalcyon on 2011-06-28
I came up with a workaround, but it is rather ugly.

The idea is to have a script run on logout that turns ON the metacity compositing manager and a script that runs on login that turns it off again.

From [here]("http://www.linuxquestions.org/questions/linux-desktop-74/gnome-run-script-on-logout-724453/"), I found a way to run a command when logging out. I have to modify the Default file in /etc/gdm/PostSession to include the line

```
su - $USER -c "command"
```where "command" is the one given in the previous posts to set compositing to true. Using su is sadly necessary because the script is executed as root and not as the user.

To run a command on logging in, I tried putting a similar script in /etc/gdm/PreSession, but it did not work. I also tried /etc/gdm/PostLogin, but that didn't work either. In both cases metacity was successfully turned off after, but the slow task-switching issue was not resolved.

I ended up writing a simple script and setting it as a startup application through System > Preferences > Startup Applications (this solution found [here]("http://ubuntuforums.org/showthread.php?t=989069")). There's probably a better way of doing a startup script, but at least this gets the job done.

After all this, it still doesn't work if the user reboots without logging out. Apparently the script in gdm/PostSession only runs on an an actual log out. So to catch the reboot, I followed the steps in [this thread]("http://ubuntuforums.org/showthread.php?t=185261").

It works... but it's a messy bandaid solution at best. Still hoping someone can offer an actual fix, or at least an explanation of why this stuff happens.

**Edit:** Solution seems not to work on reboot sometimes.  There must be some sort of race condition...

---

