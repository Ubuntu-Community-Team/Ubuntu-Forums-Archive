---
title: "Blank Screen after Restart Ubuntu."
date: 2011-02-18
forum: New to Ubuntu
---

### Post by Linyx on 2011-02-18
When i reboot or Start my PC, Blank-Screen Appear after Loading Ubuntu, At that stage, Ubuntu can't get my commands e.g Alt+Ctrl+F1, All i have to do is Alt+Ctrl+Del to restart My OS, & after that it just run fine.

It happens two days ago and after that, it now happening Everytime after Starting my PC.

OS Lucid-x64

Pentium-D 945 Integrated-Gfx

I thought may-be this is because of broken packages or Something similar, thats why, i run commands to clean/Recover packages & its done Successfully with no Errors But Still the Problem Persist.....

Any suggestions...?

---

### Post by Rubi1200 on 2011-02-18
This sounds like a graphics issue.

What specific graphics card do you have?

Are you able to access the GRUB menu when the computer boots?

---

### Post by Linyx on 2011-02-18
> **Rubi1200 said:**
> This sounds like a graphics issue.

What specific graphics card do you have?

Are you able to access the GRUB menu when the computer boots?

thanks for reply,

Maybe you are right,but i don't think so that it is Graphics issue,

My Graphics card is > **82945G/GZ Integrated Graphics Controller**

Moreover, i had Dual-booted Ubuntu with XP, and yes i am able to access grub menu,

---

### Post by Rubi1200 on 2011-02-18
Okay, so let's try this:

when the computer starts and you see the entry for Ubuntu in the GRUB menu press "e" to edit.

Find the line that ends with quiet splash and add this i915.modeset=1

It should look like this > quiet splash  i915.modeset=1

Then "Ctrl" + "x" to boot.

Let me know if this makes a difference.

---

### Post by Linyx on 2011-02-18
Ok, Done, now the line looks like:-

> quiet splash i915.modeset=1

but when i Shutdown my PC,Start it again, Ubuntu loads but after that it Shows blank Screen Again..

---

### Post by Rubi1200 on 2011-02-18
When you did it the first time were you able to get to the desktop?

Was everything normal?

If yes, we can make this permanent.

Next time you boot, follow the same instructions.

At the desktop, go to the terminal and type this in:

```
gksu gedit /etc/default/grub
```

In the file, find this line:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

change it to this:

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=1"

Save and then run this;

```
sudo update-grub
```

That should fix things.

---

### Post by Linyx on 2011-02-18
Ok, I have Edited grub-file as you suggested and Now their isn't any blank screen anymore, thanks for that :P

But it will be Great if you **Explain** a little bit this line:-
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=1"
& Why this problem happens...As far as i know **i915** is the driver of my Graphics card,

Thanks once again,

---

### Post by Rubi1200 on 2011-02-18
First, I am glad you got this sorted out :-)

The line you edited controls the default for the kernel or linux line (as it is known in GRUB2).

quiet splash means just that; you don't see all the normal messages flashing past as the kernel boots.

By appending the parameter you can add instructions to be carried out at boot time.

The i915 parameter is for Intel graphics cards; so correct.

Just out of curiosity, how did you manage to install 10.04 in the first place without using this?

For more information on Intel graphics cards, including workarounds for 10.04, see here:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

### Post by Linyx on 2011-02-18
> **Rubi1200 said:**
> Just out of curiosity, how did you manage to install 10.04 in the first place without using this?


I didn't get that line, sorry...

Edit:-Anyway,Problem is Solved.

---

