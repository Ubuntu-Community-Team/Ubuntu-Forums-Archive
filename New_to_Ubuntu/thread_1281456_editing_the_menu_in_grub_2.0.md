---
title: "editing the menu in grub 2.0"
date: 2009-10-03
forum: New to Ubuntu
---

### Post by libihero on 2009-10-03
I wanna get rid of some stuff showing in the grub 2.0, but i dunno how to do it :S
i opened the file called boot, but it said "do not edit"... but is that the one i'm supposed to edit?
plus... wat's the difference between grub 2.0 and the old grub?

---

### Post by drs305 on 2009-10-03
Here is a general introduction to Grub 2:
GRUB 2 BASICS  / GRUB 2 WIKI
[Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275")
[https://wiki.ubuntu.com/Grub2]("https://wiki.ubuntu.com/Grub2")

---

### Post by libihero on 2009-10-08
i can't figure out how to make it show only 9.10, 8.10, and windows vista :(

Found linux image: /boot/vmlinuz-2.6.31-12-generic
Found initrd image: /boot/initrd.img-2.6.31-12-generic
Found linux image: /boot/vmlinuz-2.6.31-11-generic
Found initrd image: /boot/initrd.img-2.6.31-11-generic
Found Ubuntu 8.10 (8.10) on /dev/sda1
Found Windows Vista (loader) on /dev/sda2

what should i put in the terminal?

---

### Post by drs305 on 2009-10-08
> **libihero said:**
> i can't figure out how to make it show only 9.10, 8.10, and windows vista :(

what should i put in the terminal?

What don't you want to see - extra kernels? recovery mode? memtest86+?

To avoid seeing recovery mode, open gedit as root:

```
gksu gedit /etc/default/grub
```

To avoid seeing recovery mode (maybe not recommended, think about it) add this:
> 
GRUB_DISABLE_LINUX_RECOVERY="true"


To avoid seeing memtest86+, run this command:
```

sudo chmod -x /etc/grub.d/20_memtest86+

```


[size="3"]**[COLOR="DarkRed"]Then run[/COLOR]**[/size]
```

sudo update-grub

```
Or is it the extra kernels you don't want?

---

### Post by ikisham on 2009-10-08
[Here]("http://ubuntuforums.org/showthread.php?t=1285897") is another how-to.

First, maybe you should leave the recovery mode entry since you may need it someday.
For the old kernel entry to be removed, the only thing I think now is removing the kernel itself but then there may be a way to hide it that I don't know yet.

---

### Post by libihero on 2009-10-08
isn't there a way to access the recovery mode if its not on the list? if not then ya i'll keep it there
i dunno why it repeats the 9.10 twice tho.... they both do the same thing

---

### Post by drs305 on 2009-10-08
> **libihero said:**
> isn't there a way to access the recovery mode if its not on the list? if not then ya i'll keep it there


To Boot to the Recovery Mode If Not Displayed as an Option:

1. If you have Grub 2 set to boot without displaying the menu at all, hold the SHIFT key down until the menu displays. (In Grub it was the ESC key.)

2. Press any key once the menu is displayed to 'freeze' it. Then arrow to the kernel you want to boot. 

3. Press E

4. Scroll to the end of the "linux /boot/vmlinuz...." line and add the word "**single**".

5. Press CTRL-X to boot to the Recovery menu.

---

### Post by mcduck on 2009-10-09
> **libihero said:**
> isn't there a way to access the recovery mode if its not on the list? if not then ya i'll keep it there
i dunno why it repeats the 9.10 twice tho.... they both do the same thing

You have two kernel versions installed, so each entry boots a different version.

To get rid of the old kernel you can simply uninstall it's packages with Synaptic and the Grub menu entry will be automatically removed.

---

### Post by libihero on 2009-10-09
> **drs305 said:**
> What don't you want to see - extra kernels? recovery mode? memtest86+?

To avoid seeing recovery mode, open gedit as root:

```
gksu gedit /etc/default/grub
```

To avoid seeing recovery mode (maybe not recommended, think about it) add this:


To avoid seeing memtest86+, run this command:
```

sudo chmod -x /etc/grub.d/20_memtest86+

```


[size="3"]**[COLOR="DarkRed"]Then run[/COLOR]**[/size]
```

sudo update-grub

```
Or is it the extra kernels you don't want?

i tried what you said to get rid of the recovery mode, but there was no file /etc/default/grub

---

### Post by drs305 on 2009-10-09
> **libihero said:**
> i tried what you said to get rid of the recovery mode, but there was no file /etc/default/grub

If you are sure you are/were running Grub 2, go into Synaptic see if Grub2 is still installed. I know there were some problems with an update a day or two ago that messed up some users' Grub 2 files. In fact, there were some reports that the updates reinstalled grub (and replaced grub 2).

See if reinstalling Grub2 restores the /etc/default/grub file.

---

