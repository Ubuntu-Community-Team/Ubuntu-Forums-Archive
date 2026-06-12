---
title: "dual boot XP and ubuntu, grub won't load XP"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by powerman15 on 2009-03-17
Hi guys, 
im completely new to ubuntu, hence why im using it alongside XP, i've gotten 3 hard drives set up, 2 SATA and 1 IDE.
1 SATA has XP on it, other has just games/storage, and IDE now has ubuntu on it...

bios is set to boot from IDE (ubuntu drive) obviously, but under "other operating systems" windows xp comes up with unsupported format.. i've been reading and i need to change some menu.lst file??? but im so new to the terminal and commands, how to do change it? and what to?

i've attached some of the files that might be useful

cheers

---

### Post by Bearly Able on 2009-03-17
I don't know the answer, but I had [a very similar problem]("http://ubuntuforums.org/showthread.php?t=1060203") and posted in the "installation and upgrades" section of the forums, where I got excellent, step-by-step advice from folk who clearly know exactly what they're talking about. If no-one helps you here, I'd suggest posting again in that forum.

---

### Post by presence1960 on 2009-03-17
in terminal run > sudo fdisk -l

post the output here. Since windows is not on your boot drive you are missing map lines in your menu.lst. This will let us know which drives to add in those map lines for windows. Plus it looks as though your hard drive # and partition are incorrect for windows in menu.lst.

BTW that is a lower case "L" not a 1!

I will go to work soon, but if you post the output of that command someone here will gladly show you how to edit your windows entry in menu.lst

---

### Post by powerman15 on 2009-03-17
thanks, but in the mean time i found another thread on a forum that was pretty much what was my problem, just had to change the Windows XP Pro grub settings, map (hd0) (hd1) etc etc..
thanks anyway :)

---

### Post by presence1960 on 2009-03-17
> **powerman15 said:**
> thanks, but in the mean time i found another thread on a forum that was pretty much what was my problem, just had to change the Windows XP Pro grub settings, map (hd0) (hd1) etc etc..
thanks anyway :)

That's exactly what I said, but before I gave you the map settings I wanted to see the order of your hard disks and which OS was where on those disks... But at any rate I am glad to see you solved it. I have never had to start a thread for a problem. But God knows I have had them. I always seem to find my answers in a previous post by searching the forums.

---

