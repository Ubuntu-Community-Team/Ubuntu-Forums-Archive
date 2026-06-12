---
title: "Ubuntu 10.10 No GUI on Reboot"
date: 2011-03-12
forum: New to Ubuntu
---

### Post by newbietux on 2011-03-12
I've been using Ubuntu 10.10 on my HP dv9000 laptop for about two months, and following a bad shutdown today, I'm having the following problem.

On startup, instead of the typical gnome splash screen, I got a text-only "Ubuntu 10.10" on a purple background that switched to black.  I was able to access the command line and login.  All my files and apps seem to be intact, but I have no GUI.

Things I tried based on various posts in this forum: uninstalling and reinstalling the gnome desktop.  Installing KDE (this meant no change except a text splash saying "Kubuntu 10.10" on a blue background.)  I booted from a USB ISO with no problems.

So, I am really at a loss.  Any suggestions?  I'd prefer to avoid reinstalling.

---

### Post by Hippytaff on 2011-03-12
what graphics card do you have?

---

### Post by newbietux on 2011-03-12
nVidia Geforce Go 6150.

---

### Post by Dorsenstein on 2011-03-12
try this after you login

```
sudo /etc/init.d/gdm start
```

That should work, if it doesn't, tell us what happens.

---

### Post by Hippytaff on 2011-03-12
> **newbietux said:**
> nVidia Geforce Go 6150.

You might need to reinstall the driver - Try the above suggestion first though.

---

### Post by newbietux on 2011-03-12
Dorsenstein, thanks.  When I try that (like when I tried service gdm start), the screen blinks back and forth a few times and then returns me to the command prompt.

---

### Post by Hippytaff on 2011-03-12
Are you dual booting? if so, when you get to the grub menu (the bit where you choose OSs) highlight ubuntu, press e. Then change 'quiet splash' to 'nomodeset, then press CTRL+X to boot. If you get into the GUI then reinstall the Nvidia drivers.

If this doesn't work it might be a x.org problem

---

### Post by Dorsenstein on 2011-03-12
Hm, that's interesting. Try
```
sudo /etc/init.d/gdm stop
```

And then navigate into /etc/X11. There should be a file called xorg.conf Copy that and name it something like xorg.conf.1

Then delete xorg.conf, and try starting gdm again. It should generate a new xorg.conf file.


EDIT: Looks like we posted at about the same time, try the above first, and then try the xorg.conf method.

---

### Post by Hippytaff on 2011-03-12
> **Dorsenstein said:**
> Hm, that's interesting. Try
```
sudo /etc/init.d/gdm stop
```And then navigate into /etc/X11. There should be a file called xorg.conf Copy that and name it something like xorg.conf.1

Then delete xorg.conf, and try starting gdm again. It should generate a new xorg.conf file.


EDIT: Looks like we posted at about the same time, try the above first, and then try the xorg.conf method.

you might have hit the nail on the head...was thinking it might be an xorg issue. Thought I'd suggest the nomodeset thing first to eliminate a driver issue

---

### Post by Dorsenstein on 2011-03-12
> **Hippytaff said:**
> you might have hit the nail on the head...was thinking it might be an xorg issue. Thought I'd suggest the nomodeset thing first to eliminate a driver issue

It's a good idea, but I have had some Nvidia driver issues in the past. If you have a driver issue, Ubuntu should give you the option to start in safe graphics mode.

---

### Post by Hippytaff on 2011-03-12
Cool - I never got that prompt (unless I ignored it :roll: ). But that's worth bearing in mind in situations like this

---

### Post by newbietux on 2011-03-12
Okay.

```
sudo /etc/init.d/gdm stop
```

told me to use the service utility.

There is no xorg.conf file in /etc/X11.  There is a xorg.conf.failsafe.

I'm not dual-booting, and I've tried to use grub to load past kernels/versions/recoveries with the same result.  Text-only splash, then command prompt.

Thanks for the help so far!  now what?

---

### Post by newbietux on 2011-03-12
P.S.  Replacing 'quiet splash' with 'nomodeset' just dumped me to the command line in much bigger type.

---

### Post by Hippytaff on 2011-03-12
Did you say reinstalling wasn't really an option. I'd back everything up and reinstall...but that's just what I would do if I didn't have the time to mess around.

---

### Post by wweeks on 2011-03-12
Try switching graphic styles. Right click on the desktop and get the "Change Desktop Background" option. Then change to a high contrast and back until you get a GUI. 1 or 2 times should do it. If it does then we can go from there.

---

### Post by Dorsenstein on 2011-03-12
> **newbietux said:**
> 
There is no xorg.conf file in /etc/X11.  There is a xorg.conf.failsafe.


Try copying the xorg.conf.failsafe and renaming it xorg.conf and then do
```
service gdm restart
```

See if that works.

---

### Post by newbietux on 2011-03-12
cannot create regular file xorg.conf, permission denied.

Reinstalling is an option but it feels like admitting failure.  (Also it was a royal PITA to get wireless working the first time and I'd prefer not to have to redo it, along with reinstalling all my software.  Data's backed up, tho.)

---

### Post by Hippytaff on 2011-03-12
try doing ```
sudo service gdm etcetc
```

---

### Post by Dorsenstein on 2011-03-12
> **newbietux said:**
> cannot create regular file xorg.conf, permission denied.


You tried sudo? And stopped gdm first?

---

### Post by newbietux on 2011-03-13
Oops.  Okay.  Copied xorg.conf, but now there seems to be a problem with the service utility, in that it won't let me restart gdm and I get the same message (instructions to use the service utility) that I was receiving earlier.

I'm starting to think a fresh install is my only option.  I wish I knew what I'd done!

---

### Post by Hippytaff on 2011-03-13
You could try looking at the logs in var/log/
.
There is an xorg log and others that might hold some useful information

---

