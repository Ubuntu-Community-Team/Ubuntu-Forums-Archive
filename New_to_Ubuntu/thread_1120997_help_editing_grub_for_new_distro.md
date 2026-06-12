---
title: "help editing grub for new distro"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by nml on 2009-04-09
Hey All..

Have a successful duel boot of Ubuntu 8.1 and XPpro...

Today I added 'Puppy Linux' to another separate partition..unfortunately, I haven't been able to successfully add it to Grub....

here's what I was told to include in menu.lst:

```
title Puppy Linux 420 frugal
rootnoverify (hd0,2)
kernal /puppy420/vmlinuz pmedia=atahd psubdir=puppy420 nosmp
initrd /puppy420/initrd.gz
```


Where do I insert this in the menu.lst?

TIA,

Mick

---

### Post by taurus on 2009-04-09
Try adding those lines to the end of /boot/grub/menu.lst.

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by nml on 2009-04-09
> Try adding those lines to the end of /boot/grub/menu.lst.


thanks taurus....I had previously added them behind the last entry and it showed up in grub, but wouldn't boot when chosen.  I then added to the end after the 'XP' entry....same problem.

Should I just paste the lines at the very end...after the XP choice?

When I get home to my laptop, I can post a copy of the menu.lst....I have a copy of it here at work, but don't know how to make it show on this windows machine...

thanks again

Mick

---

### Post by Jakey_TheSnake on 2009-04-09
Wait, what's the problem, is it puppylinux or XP now?

---

### Post by Didius Falco on 2009-04-09
Check the spelling in your menu.lst - I noticed you had "kernal" instead of "kernel".

---

### Post by markbuntu on 2009-04-09
does puppy have its own grub?
It should.
Then you can just chainload it. That is how I have all my distros set up. Each with its own grub chainloaded from the grub on the mbr. 

!!One Grub to rule them all!!

Seriously though, it saves me a lot of trouble and far fewer chances of spelling errors.

---

### Post by nml on 2009-04-09
> Then you can just chainload it. That is how I have all my distros set up. Each with its own grub chainloaded from the grub on the mbr.

I have XP chainloaded, so how would I chainload Puppy Linux??

> Check the spelling in your menu.lst - I noticed you had "kernal" instead of "kernel".

I absolutely will as soon as I get home...

many thanks to you both..

Mick
(hoping a 2nd chainload will work)

---

### Post by markbuntu on 2009-04-09
> **nml said:**
> I have XP chainloaded, so how would I chainload Puppy Linux??


Mick
(hoping a 2nd chainload will work)

If puppy has its own grub on the puppy partition, just point the chainload to the correct partition and puppys grub should take over. I chainload all sorts of things


# Chainloader to i386 grub
root		(hd0,0)
chainloader	+1


#Chainloader to Mandriva
root		(hd2,0)
chainloader	+1

Chainloader to Intrepid
root		(hd3,1)
chainloader	+1

---

### Post by nml on 2009-04-09
> If puppy has its own grub on the puppy partition, just point the chainload to the correct partition and puppys grub should take over. I chainload all sorts of things

Excellent information....I'll keep this model for my next install.....

I installed Puppy in a frugal mode, so I'm not sure about it's own bootloader...but I changed 'kernal' to the correct spelling 'kernel' , then pasted the output below my XP install and I now can boot to it....

pretty cool...

thanks all

Mick
(more questions to follow soon, I'm sure)

---

### Post by bodhi.zazen on 2009-04-09
[How to Multi-boot (Maintain more then 2 OS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=724817")  - has a number of tips for multibooting.

---

### Post by nml on 2009-04-11
> How to Multi-boot (Maintain more then 2 OS) - Ubuntu Forums - has a number of tips for multibooting.

great (and useful) link....thanks

Mick

---

