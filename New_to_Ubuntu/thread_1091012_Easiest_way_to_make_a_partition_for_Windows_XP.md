---
title: "Easiest way to make a partition for Windows XP?"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by Edward B. on 2009-03-08
I just solved a problem that resulted in wonky graphic glitches on my Ubuntu desktop, and I'm pretty satisfied with it as an OS except I can't play no games! Or just a select few games anyway.

What's the easiest way for me to create a partition to install Windows XP on and a few games = Rome: Total War and maybe Tropico?

I have no experience doing this - how will I choose which OS to boot into when turning on the computer?

How do I delete Windows XP if I need to after I create the partition?

Any help would be much appreciated.

---

### Post by Lostin60's on 2009-03-09
> **Edward B. said:**
> I just solved a problem that resulted in wonky graphic glitches on my Ubuntu desktop, and I'm pretty satisfied with it as an OS except I can't play no games! Or just a select few games anyway.

What's the easiest way for me to create a partition to install Windows XP on and a few games = Rome: Total War and maybe Tropico?

I have no experience doing this - how will I choose which OS to boot into when turning on the computer?

How do I delete Windows XP if I need to after I create the partition?

Any help would be much appreciated.

Typically, you should install Windows first. If you install it after Ubuntu, it will foul up the grub boot manager. My Windows does not even recognize my Ubuntu..lists it as free space..lol With Windows already in, Ubuntu will take care of the boot issue when installing.


You might also see if your games run under Wine.

[COLOR="White"]aa[/COLOR]

---

### Post by Edward B. on 2009-03-09
> **Lostin60's said:**
> Typically, you should install Windows first. If you install it after Ubuntu, it will foul up the grub boot manager. My Windows does not even recognize my Ubuntu..lists it as free space..lol With Windows already in, Ubuntu will take care of the boot issue when installing.


You might also see if your games run under Wine.

[COLOR="White"]aa[/COLOR]

Son of a B!

So I have to friggin' uninstall Ubuntu, then reinstall Windows, then reinstall Ubuntu?

Argh!!!

Wine will not run Rome: Total War at all from the user reports I've seen on Wine's site. Tropico doesn't run well either.

So what if I decide to reinstall Windows? Is there something special I need to do to wipe the hard drive of Ubuntu? Or will Windows automatically do that when it is installed?

---

### Post by Mark Phelps on 2009-03-09
You don't have to uninstall Ubuntu, it's just that it's easier to have both if XP is installed first.

Just install XP, understanding that it will overwrite the MBR and wipe out GRUB in the process.

Then, use the Ubuntu LiveCD to reinstall GRUB as follows:

[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

Then, you'll have to manually add an entry to the end of the GRUB config file for XP.

---

### Post by bailbath on 2009-03-09
You could use a virtual machine. Run XP from it and it's games.
see this thread- [http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)
Ian

---

### Post by Edward B. on 2009-03-09
> **Mark Phelps said:**
> You don't have to uninstall Ubuntu, it's just that it's easier to have both if XP is installed first.

Just install XP, understanding that it will overwrite the MBR and wipe out GRUB in the process.

Then, use the Ubuntu LiveCD to reinstall GRUB as follows:

[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

Then, you'll have to manually add an entry to the end of the GRUB config file for XP.

Thanks for the link.

One question: the post says that "sudo" means you need to enter the command at a root terminal. How do you access a root terminal?

---

### Post by benerivo on 2009-03-09
> **Edward B. said:**
> One question: the post says that "sudo" means you need to enter the command at a root terminal. How do you access a root terminal?
I think the post is wrong. You can use sudo in any terminal. A 'root terminal' is generally not used in ubuntu.

---

### Post by Edward B. on 2009-03-09
> **benerivo said:**
> I think the post is wrong. You can use sudo in any terminal. A 'root terminal' is generally not used in ubuntu.

And how do I access the terminal again? I know someone told me this a while back, but I can't remember.

---

### Post by Miljet on 2009-03-09
Applications -> Accessories -> Terminal

---

### Post by Edward B. on 2009-03-09
Thanks!

---

