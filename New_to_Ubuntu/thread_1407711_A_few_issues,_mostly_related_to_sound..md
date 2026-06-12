---
title: "A few issues, mostly related to sound."
date: 2010-02-15
forum: New to Ubuntu
---

### Post by JerichoKru on 2010-02-15
Hello, I recently installed Xubuntu 9.10 on my notebook, and a few things bother me.

1.) While not explicitly related to sound, the semi-transparent on-screen pop up appears about an inch below where the system tray is.  I'd rather have it appear right below it.

2.) Using Fn volume controls, have stopped working.  When they were working, they modified the incorrect volume bar, having no effect on the volume.

How would I go about fixing these issues?

---

### Post by Julita on 2010-02-15
As to second question, what are your specs? For each laptop it is different. I, for example, need to install eeepc-acpi-scripts for Fn to work...

---

### Post by JerichoKru on 2010-02-15
> **Julita said:**
> As to second question, what are your specs? For each laptop it is different. I, for example, need to install eeepc-acpi-scripts for Fn to work...

It's an Asus K50AB:  AMD Turion 64 X2 RM-75, 4GB DDR2-800, ATi Mobility Radeon HD 4570, VIA VT1708S for sound(according to xfce mixer's OSS option).  It was working before..though I was removing programs I didn't want...perhaps the proper Fn scripts went with it (though screen brightness Fn's work).

I'll see if the eeepc scripts work later.

EDIT: I cannot install the eeepc scripts > ```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  eeepc-acpi-scripts: Depends: acpi-support-base but it is not installable
E: Broken packages
```

Checking synaptic, my system has acpi-support installed...but the base package it mentions, and correctly says, that it doesn't exist.

---

### Post by JerichoKru on 2010-02-16
Well, my Fn for volume is working again...not sure why.

To be a bit more specific about the Fn volume moves the incorrect volume bar (Master Front), when the speaker volume is actually "Front".  How would I go about changing this?

Also ignore #1 in the original post, I found out why the pop-up has a gap between it and the panel, so It doesn't interfere with the volume pop-up.

---

### Post by Julita on 2010-02-16
My Fn also controls only Master Front... I manually edit my sound system via 
```
alsamixer
```...

and ```
xfce4-mixer
```

---

### Post by JerichoKru on 2010-02-16
> **Julita said:**
> My Fn also controls only Master Front... I manually edit my sound system via 
```
alsamixer
```...

and ```
xfce4-mixer
```

So...there's no permanent solution?

---

### Post by Julita on 2010-02-16
Nope! I have googled, asked, but still nothing. Wish you luck!

---

### Post by Julita on 2010-02-17
Hi! I guess I have found the solution. It is posted here: [http://ubuntuforums.org/showpost.php?p=7395063&postcount=4](http://ubuntuforums.org/showpost.php?p=7395063&postcount=4)
You would need to install amixer for this to work; additinally, instead of "Master" in the command you would need to specify your control. To find the correct name for it, you need to run the command from terminal: amixer scontrols You will see the available controls; supposedly, Front should be there. Supposedly because for me (for some reason) it doesn't work. Judging by the responses, it works for others, so it may work for you as well. The whole discussion is here: [http://ubuntuforums.org/showthread.php?t=1165082](http://ubuntuforums.org/showthread.php?t=1165082)

---

