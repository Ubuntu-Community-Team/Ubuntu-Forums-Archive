---
title: "Error 11 when reinstalling Grub after windows install"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by B-80 on 2009-09-14
Hey, I am really new at linux and I have been searching around for the solution to this for a while, but I cant seem to figure it out.

I installed windows 7 today on a diff hard drive than my ubuntu install. 

now I know windows messes up grub or something, so I booted into my ubuntu live cd and tried running the commands to reinstall grub.

This is basically what my termial looks like

 ~/ sudo grub

> find /boot/grub/menu.lst
(hd1, 4)

> root(hd1, 4)
Error 11: Unrecognized device string

> setup (hd1)
Error 27: Invalid device requested

All my Hard drives are mounted and everything(idk if that matters).

but I really am stuck here. any help is appreciated

---

### Post by zeroseven0183 on 2009-09-14
I noticed that immediately following your "root" command is "(hd1,4)".
Insert a space between that two and see what the result is.

You can also check out this thread: [GRUB: Error 11: Unrecognized device string]("http://ubuntuforums.org/showthread.php?t=485022")

---

### Post by B-80 on 2009-09-14
> **zeroseven0183 said:**
> I noticed that immediately following your "root" command is "(hd1,4)".
Insert a space between that two and see what the result is.

You can also check out this thread: [GRUB: Error 11: Unrecognized device string]("http://ubuntuforums.org/showthread.php?t=485022")

I actually didn't have a space, without a space it gives me an unrecognized command error. I'll look at that link

---

### Post by zeroseven0183 on 2009-09-14
You might also want to post the content of your [B]/boot/grub/menu.lst

[/B]```
vi /boot/grub/menu.lst
```[B]

[/B]

---

### Post by B-80 on 2009-09-14
> **zeroseven0183 said:**
> You might also want to post the content of your [B]/boot/grub/menu.lst

[/B]```
vi /boot/grub/menu.lst
```[B]

[/B]
shows me a bunch of "~" and then outputs
```
"/boot/grub/menu.lst" [New DIRECTORY]
```

also I ran "fdisk-l" and the generated list doesn't show any hard drives, just my cd drive.

---

### Post by egalvan on 2009-09-14
> **B-80 said:**
> 
 ~/ sudo grub

> find /boot/grub/menu.lst
(hd1, 4)

> **root(hd1, 4)   [COLOR="Red"]<--- bad spacing, see below[/COLOR]**
Error 11: Unrecognized device string


There needs to be a space after the "root"
and no space inside "(hd1,4)"

```
root (hd1,4)
```

---

### Post by egalvan on 2009-09-14
> **B-80 said:**
> 
also I ran "fdisk-l" and the generated list doesn't show any hard drives, just my cd drive.

proper syntax for this...

```
sudo fdisk -l
```

spaces are off, make sure you have them right...

And "sudo" is needed, or else you will not get the proper output.

---

### Post by B-80 on 2009-09-14
> **egalvan said:**
> proper syntax for this...

```
sudo fdisk -l
```

spaces are off, make sure you have them right...

And "sudo" is needed, or else you will not get the proper output.

yeah, I know. I ran all those commands correctly in the terminal, I just copied them on the forums wrong. 

IDK what the hell happened, but It just randomly worked one time for me for no reason. But it doesn't show windows in grub now. Well, thats the next thing to work on

---

