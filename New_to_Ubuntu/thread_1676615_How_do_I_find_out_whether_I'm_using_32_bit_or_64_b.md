---
title: "How do I find out whether I'm using 32 bit or 64 bit?"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by Ranger_Joe on 2011-01-27
Ok,
My laptop is meant to run 64 bit operating systems. Meaning... it came with 64 bit Windows 7 pre-installed. So, I know it's a 64 bit computer.

However, I could swear I installed 32 bit Maverick Meerkat. I did this on the advice of someone more knowledgeable than myself. If in fact I am, they were right, as I never have any problems.

The issue is, I have a few other versions installed. I want to free up some space on my hard disk and therefore delete a few partitions. 

The point is: I don't know how to find out what version I'm using right now. I came across a few terminal commands that tell me what type of computer I have but nothing that tells me what version I'm running right now. Please help!

---

### Post by perspectoff on 2011-01-27
uname -a

(Enter that command in a command-line interface Terminal).

---

### Post by Ranger_Joe on 2011-01-27
This is the output I get:

```

Linux joe-laptop 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64 GNU/Linux

```

I would assume this means I'm running 64 bit?

---

### Post by mharrison on 2011-01-27
Correct, the x86_64 would indicate 64 bit.

---

### Post by daniell59 on 2011-01-27
> **perspectoff said:**
> uname -a

(Enter that command in a command-line interface Terminal).

Please let me know how I can learn the commands.

---

### Post by mharrison on 2011-01-27
> **daniell59 said:**
> Please let me know how I can learn the commands.

First, I would start your own thread rather than hijacking someone elses....

That being said...
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a good place to start.  A google search will also yield results as well.

---

### Post by Ranger_Joe on 2011-01-27
Daniel,
I would have to agree with Harrison. That said, that's an excellent manual. that's how I learned.

---

### Post by daniell59 on 2011-01-27
> **mharrison said:**
> First, I would start your own thread rather than hijacking someone elses....

That being said...
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a good place to start.  A google search will also yield results as well.

sorry, and thanks

---

### Post by perspectoff on 2011-01-27
> **Ranger_Joe said:**
> Ok,
The issue is, I have a few other versions installed. I want to free up some space on my hard disk and therefore delete a few partitions. 

The point is: I don't know how to find out what version I'm using right now.

I'm not sure why, but Ubuntu has been recommending 32-bit versions of Maverick. Probably something hardware related.

The problem is to figure out which OS you are booting up, and where the Grub bootloader is stored.

A way to see which partition you are currently booting is to get into the Grub menu immediately after power up (using the ESC key) and then "edit" the commands (which will show you the commands for loading up the partitions). Look at which partition is listed for the OS at the top of the Grub menu list, and you'll know which partition you are using.

It is sometimes difficult to otherwise remember to which partition the MBR refers. The MBR generally refers to the copy of Grub2 in the partition of whichever Ubuntu you installed most recently. (Every installation of Ubuntu has its own copy of Grub2, and the MBR is just a pointer to one of them. "Installing to the MBR" really means resetting the MBR to point to one of them.)

If you don't remember which partition has the currently designated Grub2, then when you delete a partition you have a good chance of also deleting Grub2 along with the partition. Be prepared to "re-install"/reconfigure the MBR to point to another copy of Grub2 on one of the retained partitions (using a recent Ubuntu LiveCD).

---

### Post by Ranger_Joe on 2011-01-27
Attached is a picture of my GRUB menu.

It doesn't say anything about 32 vs. 64 bit.

---

### Post by steveneddy on 2011-01-27
> **mharrison said:**
> Correct, the x86_**[COLOR="Red"]64[/COLOR]** would indicate 64 bit.

that's it

---

