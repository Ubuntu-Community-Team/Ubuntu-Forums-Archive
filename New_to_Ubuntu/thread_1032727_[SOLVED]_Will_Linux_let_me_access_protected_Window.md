---
title: "[SOLVED] Will Linux let me access protected Windows files?"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by MaxRabbit on 2009-01-06
If I ran Linux off a thumb drive, can I access everything on the hard drive, including files restricted by Windows such as the files of the administrator account and OS-essential files?

If it is indeed possible, do I have to do anything technical to do it, or is it automatically available?

Thanks,
max

---

### Post by bump_ on 2009-01-06
Yes you will have access to protected files. Nothing special is needed. Just get a distro with ntfs-3g installed by default and has a LiveCD feature and you should be good to go.

---

### Post by eatberrys on 2009-01-06
U should just be able to mount the HD if you shut windiows down properly I was just using to recover a password on a school comp and it allowed all access just fine.

---

### Post by MaxRabbit on 2009-01-06
Exactly what I was looking for :)

What a coincidence-my use is to "recover" a password, too ;)

---

### Post by JoshuaRL on 2009-01-06
> **MaxRabbit said:**
> Exactly what I was looking for :)

What a coincidence-my use is to "recover" a password, too ;)

Careful young padawan.  Be courteous with your newfound power, don't give FOSS a bad name.

Also, if Windows has the ext2 driver installed with read/write priviledges on ext3 filesystems, then you have full root access to it all.  I learned this the hard way recently when someone accidentally (among other things) put some Windows program folders in my root partition.  (facepalm)  Meh, I didn't like that install much anyway.  I guess.

---

### Post by Titan8990 on 2009-01-06
If password recovery is your only need you might find this ideal: [http://home.eunet.no/~pnordahl/ntpasswd/bootdisk.html](http://home.eunet.no/~pnordahl/ntpasswd/bootdisk.html)

---

### Post by MaxRabbit on 2009-01-06
Don't worry, JoshuaRL, my sole goal is to get a password for a WPA network-not about to get into anything awful. I just want to be able to get on the internet at school with my netbook.

Now, since I am looking for a network key, do you know if that will work, Titan? I am going to try it out right now-here's hoping!

If this doesn't work, anyone know bootable programs that can recover WPA keys from outside the Windows installation?

Thanks!
max

---

### Post by eatberrys on 2009-01-06
LOL I wasnt useing for wireless passwords I was useing for windows log on passwords.

Also u can use Bt3(google it if u havent heard of it) its a live linux distro that will allow u to crack wirless network keys along many other things.

---

### Post by MaxRabbit on 2009-01-06
> **eatberrys said:**
> LOL I wasnt useing for wireless passwords I was useing for windows log on passwords.

Also u can use Bt3(google it if u havent heard of it) its a live linux distro that will allow u to crack wirless network keys along many other things.

Unfortunately WPA is pretty much uncrackable. It would also be a little pointless when I have physical access to a PC with a password stored by Windows insecure security. Anyone have any other suggestions based on what I want to do?

---

### Post by eatberrys on 2009-01-06
Have you tryed asking to get on?

Wpa is diffuclt to crack yes but getting off the a computer may not work. Also if your admin at the school is smart mac filtering is enabled so you still wouldn't be able to get on with out spoofing your mac address which isnt to difficult.

[http://www.aircrack-ng.org/doku.php?id=cracking_wpa&DokuWiki=630d6f75932050125bb22d3c67c58e43](http://www.aircrack-ng.org/doku.php?id=cracking_wpa&DokuWiki=630d6f75932050125bb22d3c67c58e43)
that may help you if you find you cant get it off the computer

---

### Post by JoshuaRL on 2009-01-06
Well, this is getting a little bit iffy.  Best to just leave the blackhat instruction there.

MaxRabbit: I'm guessing it isn't an option to ask for the wpa key from the admin or someone that can get access to it?

---

### Post by Titan8990 on 2009-01-07
> MaxRabbit: I'm guessing it isn't an option to ask for the wpa key from the admin or someone that can get access to it?


That is the only advise we can give anyways....

---

### Post by MaxRabbit on 2009-01-07
> **eatberrys said:**
> [http://www.aircrack-ng.org/doku.php?id=cracking_wpa&DokuWiki=630d6f75932050125bb22d3c67c58e43](http://www.aircrack-ng.org/doku.php?id=cracking_wpa&DokuWiki=630d6f75932050125bb22d3c67c58e43)
that may help you if you find you cant get it off the computer
I appreciate your help. However, I'm not sure I want to go so far as to actively hack the network. I know I'm possibly on the unethical side here, but I'm not doing anything against the law: I am using a computer the school provides for any student to access, and I'm recovering the password stored on that laptop so I can get on with my netbook. The administration never set any rules against anyone using the network-they simply refuse to give out the key to it.

But doing a bruteforce attack on the network would probably be a lot more punishable, and perhaps unlawful (depending on if you look at it as if I had rights to the network going to that school or not). I'd rather not play *that* close to the line of danger.
> **JoshuaRL said:**
> MaxRabbit: I'm guessing it isn't an option to ask for the wpa key from the admin or someone that can get access to it?
I wish-believe me, I have. I have done everything I possibly can-I've talked to the administrator personally and asked him why he couldn't just register my MAC address on the network and therefore let me use the network and he could even track everything I do. Beats me why, but he won't let me do it.

---

