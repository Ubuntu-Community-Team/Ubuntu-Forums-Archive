---
title: "Making certain partition the default boot up os"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by mjp29 on 2009-09-26
I installed kubuntu on a smaller partition after I already had ubuntu on the computer.

I decided I prefer ubuntu, but the computer boots up into kubuntu by default unless I make a selection each time to force it to go to ubuntu.

Anyway to force computer to choose ubuntu as default bootup partition?

---

### Post by yeats on 2009-09-26
boot into kubuntu and install a program called startupmanager (either from Adept) or in the terminal:

```
sudo apt-get install startupmanager
```

This will give you a nice graphical interface to set all of your GRUB options, including the default OS.

---

### Post by themusicalduck on 2009-09-26
Easiest way is to use startup manager.

Type ```
sudo apt-get install startupmanager
``` into a terminal.

Run the program under System > Administration and it's on the first tab.

---

### Post by ajgreeny on 2009-09-26
Or you could boot to ubuntu from the kubuntu grub and then use command ```
sudo grub-install /dev/sda
``` This assumes that the MBR is on sda, of course.  If it is elsewhere use that in the command.  You will then be using ubuntu's own grub and will boot to ubuntu first, not kubuntu.

---

### Post by mjp29 on 2009-09-26
deleted post by user

---

### Post by mjp29 on 2009-09-26
deleted post by user

---

### Post by mjp29 on 2009-09-26
ok, installing it now through terminal on kubuntu

additional question:  is there any way to just wipe out kubuntu on the hd and have ubuntu reclaim that partition space for ubuntu only

---

### Post by ajgreeny on 2009-09-27
> Aditional question: is there any way to just wipe out kubuntu on the hd and have ubuntu reclaim that partition space for ubuntu only Yes, you can do it with the System-> Partition-editor on the live CD very easily.  You need to know for certain which partition is which then simply delete the kubuntu partition, and its swap if you made a separate swap for it, and sinply enlarge your ubuntu partition into the unallocated space made by the deletion.

Make sure your new grub works first, and backup before you do it just in case anything goes wrong;  it shouldn't, but better safe than sorry.

---

### Post by mjp29 on 2009-10-03
> **ajgreeny said:**
> Yes, you can do it with the System-> Partition-editor on the live CD very easily.  You need to know for certain which partition is which then simply delete the kubuntu partition, and its swap if you made a separate swap for it, and sinply enlarge your ubuntu partition into the unallocated space made by the deletion.

Make sure your new grub works first, and backup before you do it just in case anything goes wrong;  it shouldn't, but better safe than sorry.

In your previous post and this post I'm not sure what "grub" means.

Additional questions:  

1 - Can I boot from live cd (ubuntu live cd) and do this without installing any software beforehand.

2 - you said "and its swap if you made a separate swap for it" 
My question here is how does one know (how do i know) if they made a separate swap.  All I know is that I installed Ubuntu entirely on an HD that had MS Windows on it (wiped out ms windows completely by choice) and later decided to try out Kubuntu and booted from a Kubuntu disk and told it to install on a portion of my HD that had Ubuntu already on it.

For the record, I am trying out things now and don't fear wiping anything out.  Therefore, I have no fear of attempting to boot from any Ubuntu (or Kubuntu) live cd and telling system to wipe out Kubuntu and reclaim that space for Ubuntu.


p.s. you still haven't told me who your avatar is - lol

---

### Post by mjp29 on 2009-10-03
i just booted from ubuntu (live cd i suppose) and clicked through a few things

and then the partition screen came up to tell me what i had on hd and so forth

i recognized that it showed two ubuntu operating systems on the hd (one I knew was Ubuntu I want to keep using because it was around 3/4 of my hd drive).  The other ubuntu I knew must have really been kubuntu as it was a fraction in size.  oh, i also remember a very small portion being "swap" and another slim portion being something else (that i can't recall what was called)

anyways i was fully ready to wipe out kubuntu (which i knew was the more smaller of the 2 ubuntu's on my partition which was being called ubuntu also) 

but i chickend out because i couldn't see any option where i could retain my larger ubuntu partition (what i wanted to keep - the real ubuntu i call it).  all i can remember is that it (live cd) wanted to completely wipe out everything and put Ubuntu on hd.

which i really do not have a problem with since i'm in testing mode (but i will have to reconfigure evolution email, get printer to work again, install restricted-extras, etc... which will take me time i would rather not spend if i can avoid).

to make a long story short - i want to wipe out kubuntu on partition and have ubuntu reclaim that space for ubuntu (preferably without using any software but i will use the software suggested in previous replies in this post if that must be done).

---

### Post by mjp29 on 2009-10-03
> **chrissharp123 said:**
> boot into kubuntu and install a program called startupmanager (either from Adept) or in the terminal:

```
sudo apt-get install startupmanager
```

This will give you a nice graphical interface to set all of your GRUB options, including the default OS.


ok did that and got it to work

now i am working on (asking how do i) wiping out kubuntu [completely] so that ubuntu reclaims that hd disk partition space for itself only.

no use having kubuntu taking up any space (even a small partition space as it does now) when i don't plan to use it any more

---

