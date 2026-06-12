---
title: "fixing lag in jaunty"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by crabclaw on 2009-05-03
I got rid of the lag in jaunty by downgrading the visual effects. Not wanting this to be permanent I upgraded my Ram from 1gb to 1.5gb. The lag is still there though. I was wondering two things:

I booted into BIOS and saw that the extra Ram had installed properly but is there something I need to do in addition to this for jaunty to 'see' the Ram? I ask because in systems monitor I can see that barely 20% of memory is being used.

Is there a way of forcing jaunty to use up all available resources? In Ibex & Hardy my machine was so much faster than it is now, Am really surprised that it's slowed down for jaunty.

Thanks,

crabclaw

---

### Post by nandemonai on 2009-05-03
Desktop effects has little to do with RAM, it's more a graphics issue. What sort of graphics adapter do you have?

Btw, Jaunty will use all available RAM, when it needs it.

---

### Post by crabclaw on 2009-05-03
I have a NVidia Go 7600 with 512mb dedicated memory. This was working fine pre-jaunty.

---

### Post by nandemonai on 2009-05-04
Been doing a little reading and some suggestions I came across were:

[LIST]
[*]Revert to the 173 version of the drivers via System -> Admin -> Hardware Drivers

[*]Try installing the nvidia driver directly from the nvidia site (make sure you remove all versions of the nvidia driver that are currently installed)
[/LIST]

---

### Post by crabclaw on 2009-05-04
I changed the drivers as you recommended but to be honest there wasn't much, if any, improvement. The hard drive light is constantly on and it really seems as though the computer is being overworked when in reality I am only using rhythmbox, word processor (openoffice) and from time to time firefox. I'm not sure what it is since as I think I may have said it was fine in previous distros. Perhaps a clean install of jaunty would work but then there's the problem of cdrom permissions that I'm trying to fix in another thread which prevents me from burning iso cds....

---

### Post by 3rdalbum on 2009-05-04
If things are lagging and slow, and the hard disk looks like it's being worked hard, have you had a look in "top" to see what is taking up your computer's resources?

---

### Post by apienk01 on 2009-05-04
If your hard drive is working continuously you will always experience some system lag. This activity is probably a scheduled update of tracker database or Ubuntu update-manager. Wait for the disk activity to cease, and then run nvidia-settings. You should have this program in your System/Administration, if not, install from repositories.

Once in nvidia-manager, select PowerMizer tab (you may have to update the driver to 180 to get this). There you should be able to see if your video card is working with full capacity and clock speed. If you ever fiddled with nvidia driver settings in your xorg.conf, you might have set powersave options.

If the above doesn't help try installing fusion-icon and turn on (or turn off) indirect rendering option.

---

