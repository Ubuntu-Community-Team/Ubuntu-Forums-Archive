---
title: "Do I have the sequence of putting backups back correct ?"
date: 2011-03-24
forum: New to Ubuntu
---

### Post by Ghost_Mazal on 2011-03-24
Lo Guys ,

Please indulge me. I know it is discussed a lot , I just want to make sure I get this right.

I'm going to move over from Desktop pc to laptop.
As I understand it , the following procedure should work:

- Copy contents of home folder to external drive
- Install Ubuntu on Laptop
- Copy everything from the home folder backup on the external hdd to home folder on laptop
- Reboot.
- Everything should then be there including my Evolution email and all my home folder data.

Is that correct ?

PS: I am only 1 user on the pc and I will make my username on the laptop exactly the same.

---

### Post by fabricator4 on 2011-03-24
> **Ghost_Mazal said:**
> Lo Guys ,

Please indulge me. I know it is discussed a lot , I just want to make sure I get this right.

I'm going to move over from Desktop pc to laptop.
As I understand it , the following procedure should work:

- Copy contents of home folder to external drive
- Install Ubuntu on Laptop
- Copy everything from the home folder backup on the external hdd to home folder on laptop
- Reboot.
- Everything should then be there including my Evolution email and all my home folder data.

Is that correct ?

PS: I am only 1 user on the pc and I will make my username on the laptop exactly the same.

That's correct, except you might want to configure evolution before you copy the data.  I haven't moved evolution files so I don't know if it might be better importing them, rather than copying in place.  Possibly, copying all the directories will copy the evolution config also, see what others say.

Also, there's probably no need to "reboot", simply boot up the laptop and copy all your stuff to the home folder.  It's not like they're system files  - It's your home folder.

Make sure you get all of the hidden directories of course.

When moving files around here I've never had a problem just copying them into the live system, even with program config files etc.  I just make sure that I'm not running any applications that might be dependent on any of the config files I'm moving.

Edit:  I've also always used the same login name on my machines, and I've never had a problem with permissions getting messed up.  I even did some experiments with an ext2 formatted USB thumb drive and different 'desktop' users and found no problems with permissions. One thing to be aware of is that when you copy all the hidden config directories and files over, it copies your keyring as well, complete with password.

Chris.

---

### Post by Ghost_Mazal on 2011-03-24
Won't the .evolution folder contain the config and everything ?

And yes , I will use ctrl-h to make sure I copy all the hidden stuff.

---

### Post by fabricator4 on 2011-03-24
> **Ghost_Mazal said:**
> Won't the .evolution folder contain the config and everything ?


It should do, but you have to make sure that evolution is not running, by forcing a shutdown.  Have a look at [this post]("http://www.linuxforums.org/forum/applications/144130-moving-evolution-new-machine.html"), the third answer.

An alternative would be to boot the LiveCD, copy the files to the external drive, then boot the LiveCD on the laptop, and copy the files to the home directory, then reboot.  This would get around the main concern; that something would prevent the files being copied successfully because they are in use.

(So yes, I retract my statement that you should not have to reboot.  It's just that I normally try to take the easiest way around a situation first :-))

Chris.

---

### Post by Ghost_Mazal on 2011-03-24
Ah yes !!! Copy with bootable cd. Why didn't I think of that hehehe. See this is why it's always best to ask here.

Thanx for that tip man :)

I'm gonna do the copy that way with a live cd. ;)

---

### Post by Ghost_Mazal on 2011-03-24
Ok , I had a struggle but got it working finally.

This what I did.

- The live cd copy didn't work. just kept on giving permissions errors.

- So I booted my pc with parted magic and did the copy with that.

- Did the same thing on the new laptop and copied the data with parted magic.

- Then just corrected my home folder permissions settings and everything works.
Even my auto start apps is there :)

---

