---
title: "Stuck with Ugly Log In Screen..."
date: 2010-04-21
forum: New to Ubuntu
---

### Post by GMHilltop on 2010-04-21
I Like the log in screen on 9.10 (that was there :confused:)  -- see  cool-ubuntu-login.jpg

I was tinkering with the settings just to see what they would do -- see  the settings.jpg

I checked off the enhance contrast in colors (yuck) - and then unchecked  it.  Now it won't go away.

I am stuck with the ugly login -- see  ugly-login.jpg  attached.

Any Ideas on how to get it back to normal?

---

### Post by drs305 on 2010-04-21
Take a look at System, Preferences, Startup Programs. See if Visual Assistance it ticked. If so, deselect it and see if that fixes it.

Also, since the pix looks like it is prior to you logging on, this may need to be corrected as 'root' since it would affect all users.

---

### Post by GMHilltop on 2010-04-21
Yes I was tinkering before logging in.

The location I found was System, Preferences, *Startup Applications*

I think that that is what you meant.

I un-checked it and rebooted - it didn't help.  And after the reboot Visual Assistance was still unchecked.

How would I fix this as 'root'?

Log In as 'root' ?  I don't think I can do that from the log in screen - can I?

---

### Post by drs305 on 2010-04-21
Yes, it's Startup Applications, but the Startup Programs tab. So you looked in the correct place.

No, you don't log in as root; you just might have to use "sudo" if you find a command to run in terminal so it is applied universally.

TBH, I've never played with that setting prior to (or after) logging in. The next time I reboot I'll see if I can learn something about the process.

---

### Post by drs305 on 2010-04-21
I was just rebooting and playing with the Universal Access Preferences. Were you trying to reset them (unsuccessfully) before logging in?

I disabled the automatic login via the System, Administration, Login Screen settings. Then I rebooted to the login screen and set some preferences. After login, I rebooted.

On the login screen, before entering my username,  I clicked on the UAP icon at the lower right, then right clicked on the UAP banner. This opened the options and I was able to deselect the option I had previously made. The change stuck and everything is back to normal.

Is that how you tried to correct it?

My next course would be to search the system boot logs to see if I could find the way the change was made, but haven't done so yet.

---

### Post by GMHilltop on 2010-04-23
[INDENT]re:  ....  Were you trying to reset them (unsuccessfully) before logging in?
[/INDENT]Yes - all boxes where un-checked.  Especially the one that made it so ugly (even before logging in the first time.
[INDENT]re:  
On the login screen, before entering my username,  I clicked on the UAP  icon at the lower right, then right clicked on the UAP banner
[/INDENT]I am not sure why you 'right clicked on the banner'.  It does nothing for me, and I have all the check boxes there to choose from right away after clicking on the UAP icon.

[INDENT]re:  I was able to deselect the option I had previously made. The change  stuck and everything is back to normal.  Is that how you tried to correct it?
[/INDENT]Yes, but they ALL are already deselected.

[INDENT]re:  My next course would be to search the system boot logs to see if I could  find the way the change was made, but haven't done so yet.
[/INDENT]I am not sure how to do that, and I am not sure what I'd be looking for. :confused:

---

### Post by ohbwon on 2010-04-23
i just bought a emac2006 from a garage sale and it has ubuntu on it ,but i cant get passed the username,the people at the sale bought that way too,i need to reset it some how

---

### Post by arrrghhh on 2010-04-23
> **ohbwon said:**
> i just bought a emac2006 from a garage sale and it has ubuntu on it ,but i cant get passed the username,the people at the sale bought that way too,i need to reset it some how

You can reset it if they didn't password-protect GRUB, but why don't you just do a fresh Ubuntu install?  No need to reuse their installation...

Kinda stealing a thread here too buddy, this really has nothing to do with the topic.

---

### Post by GMHilltop on 2010-04-25
How would I go about doing this:
[B][COLOR=Blue]
[/COLOR][/B][INDENT][B][COLOR=Blue]re:  My next course would be to search the system boot logs to see if I  could  find the way the change was made, but haven't done so yet.

[/COLOR][/B][/INDENT]Anyone?

---

### Post by P4man on 2010-04-25
Id try this:
```
sudo aptitude reinstall ubuntu-gdm-themes
```

No guarantees it will work, but easy to try :) it will reinstall the login themes, so maybe it will reset to the default settings.

---

