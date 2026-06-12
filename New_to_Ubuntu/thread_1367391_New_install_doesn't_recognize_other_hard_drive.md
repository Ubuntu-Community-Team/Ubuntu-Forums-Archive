---
title: "New install doesn't recognize other hard drive"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by Flo'Daddy on 2009-12-29
Hello 

I'm a newbie; I just installed Ubuntu 9.10 on my old computer; here's my question.  The install went great and no more Microsoft Windows XP!!!  I have two drives on my computer and the second drive is not recognized by Ubuntu.  It gives me an error when I try to look at it.  It is partitioned; half of it is almost entirely pictures and the other half is some music files and old Windows programs, etc.  Am I going to have to reformat the extra drive and start fresh or is there a way to possibly salvage some of the contents?  I have already backed up the contents that I didn't want to lose, mainly the family pictures, but as I'm learning, I thought I'd ask.  I just installed WINE on the computer last night using ubuntu-tweak (thanks to this forum ;)).  I have not tried anything as of this time, but will when I can get to that computer.

Thanks in advance,

John

---

### Post by metalf8801 on 2009-12-29
I'm not sure if I can help but can you please post the error message your getting?

---

### Post by Muttley99 on 2009-12-29
So it doesn't mount?

type 

[HTML]df [/HTML]

in the terminal, and post the output.
also type;

[HTML]fdisk -l[/HTML] (thats an el not a one)

and again post the output.

You can use gparted to examine your drives from a gui also. TBH, if you've backed up your drive; you'd be better off formatting it.

---

### Post by Flo'Daddy on 2009-12-31
I searched in this forum and on the internet and found that I might need to run a checkdisk in Windows.  I don't have Windows XP on this computer any more, but do have a mini XP disc that I ran and was able to run checkdisk on the other drive.  Then when I went back to the tools in system, I am able to mount the drive immediately.

Thanks for your help and hope this helps anyone else!

john

---

