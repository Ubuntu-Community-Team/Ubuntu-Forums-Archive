---
title: "GRUB Loading Error 18,  IDE Failed OPT Code Unknown"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by quicksilver1234 on 2009-06-17
I'm a mostly newbie, and not at the Ubuntu computer right now, I'll try to describe this from memory.
-
Yesterday, I reset my root password. 
Today, I cannot get the computer to boot up. 
I get "GRUB Loading... Error 18", sometimes if I waited, the errors would pass and I could log in, in recovery mode, as root and see my files. 
I tried to change my password for my user account, but it said the password could not be changed "authentication token lock busy"
I read that deleting the password file in /etc/shadow? (not at computer to be exact) might allow me to reset it. But simply CDing to that directory, cause the computer to lock up and generate errors. It's like that part of the hard drive is corrupt?
What does "IDE Failed OPT Code Unknown" mean?
And then more often than not, when restart, I intermittently get "Hard drive not found, put in boot disk"

Any idea what's going on?

---

### Post by quicksilver1234 on 2009-06-17
I was hoping somebody would post that this happens with the "NumsLock on" or something. 
That if I Turned off NumLock, everything will be fine.

---

### Post by LewRockwell on 2009-06-17
[http://www.linuxjournal.com/content/resetting-root-password](http://www.linuxjournal.com/content/resetting-root-password)

---

### Post by 123456789123456789123456 on 2009-06-17
> **quicksilver1234 said:**
> I'm a mostly newbie, and not at the Ubuntu computer right now, I'll try to describe this from memory.
-
Yesterday, I reset my root password. 
Today, I cannot get the computer to boot up. 
I get "GRUB Loading... Error 18", sometimes if I waited, the errors would pass and I could log in, in recovery mode, as root and see my files. 
I tried to change my password for my user account, but it said the password could not be changed "authentication token lock busy"
I read that deleting the password file in /etc/shadow? (not at computer to be exact) might allow me to reset it. But simply CDing to that directory, cause the computer to lock up and generate errors. It's like that part of the hard drive is corrupt?
What does "IDE Failed OPT Code Unknown" mean?
And then more often than not, when restart, I intermittently get "Hard drive not found, put in boot disk"

Any idea what's going on?

Hi, read your post.  From what I have read, GRUB error 18, disk partiton celendars exceeds that supported by BIOS.  IDE Failed opt code unknown seems to be a result of hard drive failure, that would also support the assumption of the startup disk error you got at one point.  This is only a teory, I would say that the hard drive is about to fail, I can't believe it has anything to do with your changing root's password.  I would assume that for some reason one or more of the cylendars on the disk, is damaged, possibly one holding the password file, saving your user password, and it is entirely possible that the cylendar holding MBR(Master Boot Record) which holds GRUB stage 1, could also be damaged.  that would result in hard drive or boot disk not found. error.  surch for Unerversal boot test cd, this is a cd that contains several hardware tests, including hard drive file system checks, this should determine if the disk has any bad sectors, bad blocks so on.  If you can access mount the disk from live cd Ubuntu, attempt to recover your data.  if the disk does turn out to be bad, you will have to replace the disk.  There is no way to fix bad sectors, the disk itself, has become physically corrupt, possibly degrading.

---

### Post by quicksilver1234 on 2009-06-17
[Deleted by author]

---

### Post by quicksilver1234 on 2009-06-17
> **123456789123456789123456 said:**
> This is only a teory, I would say that the hard drive is about to fail
There is no way to fix bad sectors, the disk itself, has become physically corrupt, possibly degrading.
That is somehow cruelly appropriate. Somewhere, I have pissed off the computer gods. I just had a Windows PC die, so I switched over to the Linux box. Now it's likely to die after a few days.  

If you want me, I'll be at the volcano, sacrificing a PDA to the vengeful digital spirits.

---

### Post by 123456789123456789123456 on 2009-06-17
> **quicksilver1234 said:**
> That is somehow cruelly appropriate. Somewhere, I have pissed off the computer gods. I just had a Windows PC die, so I switched over to the Linux box. Now it's likely to die after a few days.  

If you want me, I'll be at the volcano, sacrificing a PDA to the vengeful digital spirits.

unfortiantly, hard drives fail, I had a customer who just bought a new hard drive, and one week after she bought it, it died, in a big way, developed the click of death, The symptoms of your drive are not as serious, your data can still be recovered, I would say around 99% of your data could be recovered, and a 96% possibility that your entire system could be recovered by a sucessful clone of the drive.
The drive I am assuming is IDE interface, these are not very expensive, go to [www.newegg.com](www.newegg.com), even [www.geeks.com](www.geeks.com), they have the best deals on drives, possibly able to get a 500gb for around $35, if the deal is still on that is.
I could help you with recovering data, and even installing the drive if you would like.
note that the error "HAD ABSULUTELY NOTHING TO DO WITH WHAT YOU DID."
hard drives fail all the time, that is what happens when you have moving parts.  I have noted at least 5 reasons why hard disks fail.
I just had one, it powered on, started spinning, then completely stopped moving inside.  that would be a complete failure, second is the click of death, means and results from the read/write heads comming out of alignment, therefore they can no longer read the platters.  third, over time, the magnetic disk, in the platters become unstable, and loose integrity, loose data, or can no longer be read from, nor written to, which seems to be happening to yours, next is exposure to magnetic fields, resulting in loss of data, and destruction of integrity of the magnetic media inside platters.  and last is failure of internal disk BIOS, or IDE interface card, usally caused by power surges.

---

