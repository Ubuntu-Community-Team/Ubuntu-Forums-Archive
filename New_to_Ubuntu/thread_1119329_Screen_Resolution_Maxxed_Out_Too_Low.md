---
title: "Screen Resolution Maxxed Out Too Low"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by Glurf on 2009-04-07
I hooked my laptop up to a tv the other day, so we would be able to watch a movie. It adjusted my resolution so that the screens would match, fine, but now I am unable to get it back to 1440x900. The highest setting I can choose is 1024x780. I ran sudo apt-get update, and update manager, in hope that some xorg update would fix the problem, no luck. I tried plugging it back into the tv and fiddled with that for awhile, no avail. I spent hours searching for the solution, leading me mostly to xrandr. So I tried xrandr, and it doesn't give me the option of setting it to 1440x900 either.

My screen has black bars of about an inch on either side, and all my panels are smashed together, please help!

---

### Post by fabricator4 on 2009-04-09
Have you tried running:

```
sudo dpkg-reconfigure -phigh xserver-xorg

```

If that fails, it seems like the EDID data from the monitor is not being recognised for some reason.  Are you running through a KVM switch or something?

Also tell us how you're trying to change resolution, through System->Preferences->Screen Resolution or through <ctrl><alt><num+> ?


Chris

---

### Post by Jakey_TheSnake on 2009-04-09
Run:

```
displayconfig-gtk
```

Choose your exact monitor make and model from the list, choose the correct resolution and hit OK. 

However, updating your xorg.conf using the above file should work.

---

### Post by fabricator4 on 2009-04-09
> **Jakey_TheSnake said:**
> Run:

```
displayconfig-gtk
```

Choose your exact monitor make and model from the list, choose the correct resolution and hit OK. 

However, updating your xorg.conf using the above file should work.

When I try this I get:

```

chris@chris-ubuntu:~$ displayconfig-gtk
bash: displayconfig-gtk: command not found
chris@chris-ubuntu:~$ man -k displayconfig-gtk
chris@chris-ubuntu:~$ 

```

Is that command found in a package that isn't installed by default?

Chris

---

### Post by Jakey_TheSnake on 2009-04-09
Strange, I didn't think I'd installed it on this machine, and therefore was a default. Unless it comes with ubuntu-restricted-extras or something? 

Either way, it can be installed with a simple "sudo apt-get install displayconfig-gtk".

---

### Post by kimberlite on 2009-04-09
In this: [http://ubuntuforums.org/showthread.php?t=996478](http://ubuntuforums.org/showthread.php?t=996478) they are saying this package has been removed from repositories...

---

### Post by fabricator4 on 2009-04-09
> **Jakey_TheSnake said:**
> Strange, I didn't think I'd installed it on this machine, and therefore was a default. Unless it comes with ubuntu-restricted-extras or something? 

Either way, it can be installed with a simple "sudo apt-get install displayconfig-gtk".

Unfortunately not.  It's been removed from the repositories as obsolete, even though there's nothing to replace it.

I run my monitor through a KVM switch and I can tell you that almost _none_ of the methods recommended in this forum actually work any more.  Even worse, the KVM actually does pass the EDID data through - I (and windows XP) can read it fine.  Ubuntu however gets rather snotty nosed about it and refuses to accept it as valid because it's no longer in the EXACT format required by the standard, presumably.

I spent weeks (months, really) of hell thinking it was me that was at fault when none of the forum suggestions did the slightest bit of good.  I can't remember how long I was stuck in the world of 640x480 resolution under Ubuntu.  You might almost forgive me for feeling positively joyful when I pressed the button on the switch which changed me back to the XP box so I could get some real work done.

So many of the bits that could have actually helped me like displayconfig.gtk and CustomEDID in xorg.conf have been removed or no longer function, while the auto configuration only works if the EDID data from the monitor is perfect and conforms to some ideal standard.

Jaunty is due on my machine in two weeks.  Dare I hope that full functionality will finally be mine, or should I expect the removal of the last remaining hack that lets me run Ubuntu through my KVM?  

That hack, BTW, is setting HorizSync and VertRefresh values for my monitor in xorg.conf.  In at least one case this resulted in a default VESA mode for the login screen that could not be displayed on my HP1740, but at least it lets me see a valid mode once Gnome has logged me in.

Sorry for the rant, but it's the result of 5 months of frustration, and the worry that Jaunty will be less functional that Intrepid.  We have a name for hardware and software that is supposed work automagically, but if it doesn't, provides no way of easily correcting it.  It's called plug and pray.

Chris.

---

