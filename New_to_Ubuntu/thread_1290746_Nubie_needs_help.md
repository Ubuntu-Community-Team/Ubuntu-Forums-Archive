---
title: "Nubie needs help"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by jaysonwil on 2009-10-13
Alright, finally get to install Ubuntu but I'm completely a nubie with both Ubuntu and fresh install of os's. I'm installing on an old 80g hard drive and not sure of the partitioning size, logical or primary and then theres the mounting??? I'm sure what I'm asking is in here somewhere but I guess I'm just not asking the right questions...Please help, I would love to get this installed and working tonight. Ultimatly I would like to have a boot portion and os portion seperated from everything else like pictures, music and games due to my kids playing on the computer and getting viruses. Whats your suggestion???

---

### Post by chuckyp on 2009-10-13
It sounds like you want to create an extra partition for /home. Thats where all your pictures files etc.. are stored. Everything else like the OS and applications will go in / .  The only other partition you need is a /swap. I would create the following if you do not want to use the guided partitioning.

/ = the root partition give it 10 gigs
/swap = twice the amount of ram you have in your machine
/home = the remainder of the drive.

That way if something is serverly wrong with your system you can reload / and still keep all your files settings and everything. Keep in mind you aren't going to have to worry about viruses and spyware on linux. So guided partitioning works for most people. You can easily create a seperate /home later.

---

### Post by |Mitch| on 2009-10-13
the / should be the primary

/home is logical

swap is just swap

I have my / set to 20 gigs

---

### Post by ddnev45 on 2009-10-13
Once you have it installed, give your kids their own user name(s).

And take a look at this:

[Free Beginners Guide]("http://ubuntuforums.org/showthread.php?t=1052065")

---

