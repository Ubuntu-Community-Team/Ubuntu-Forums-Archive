---
title: "Booting ubuntu and OS X off second HDD w\o Grub"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by RipcordAFF on 2008-12-13
Hey everybody,

I am new here and thinking about giving Ubuntu a whirl along with OSX. I have a vista machine and what I think I would like to do is leave that HDD alone, and then have another one, divided into two bootable partitions, one ubuntu, one OSX. 

Now, I have done some searching, but I cant seem to find anything talking about the feasibility of something like this. I don't really want to install GRUB onto the MBR of my main HDD, I would just switch by hitting f8 during my boot sequence to have the computer boot from the 2nd HDD (ideally THEN getting a grub choice between OSX and ubuntu).

I am sure this is making far more sense in my head than this post, but ideally if I were to remove the 2nd HDD w ubuntu and OSX the computer would be exactly the same as if I had never done anything at all, no changes at all to the vista HDD. 

If you say this is possible, any direction would be fanstic, if its not, and Im overlooking some basic detail (highly probable), I will have to rethink my plan of attack.

Thanks in advance for the help, im really looking forward to getting involved in the community!!


Reed

---

### Post by mkvnmtr on 2008-12-13
If you have a Vista box it is easy to do with Ubuntu. To get OS X to run on that equipment you might have to talk to some of the guys that have done it. It is not easy. I forget  what they call it but it a special adaption of OS X.

---

### Post by RipcordAFF on 2008-12-13
> **mkvnmtr said:**
> If you have a Vista box it is easy to do with Ubuntu. To get OS X to run on that equipment you might have to talk to some of the guys that have done it. It is not easy. I forget  what they call it but it a special adaption of OS X.

Yeah, I know OSX will be tricky, but aside from the inherent problems in that, does my plan seem like it will work with minimal problems?

---

### Post by falcon61102 on 2008-12-13
To accomplish the boot from the second HD without having the GRUB on your first HD's MBR, you would just need to install it into the MBR of the second drive.  That way when you boot up your computer, it will either go straight to Vista or if you press F8 it will then load the GRUB and you can select Ubuntu or OSX (provided you can install OSX).  

The easiest way to do this without risking messing anything up would be to disconnect your first HD during the installs.  That way it is physically impossible for anything to get installed on it.  Install as usual, selecting to install the GRUB on the second HD, which during the install will look like the only HD.  Once you get it installed and running, plug the other drive in and boot up.  You should automatically go to Vista.  Then try hitting F8 and it should go to the GRUB which will take you to Ubuntu.

---

### Post by richaoj on 2008-12-13
The technical issues with the ubuntu do not seem to difficult, but there are certainly legal issues with installing OSX on non-apple hardware.

---

### Post by RipcordAFF on 2008-12-14
> **falcon61102 said:**
> To accomplish the boot from the second HD without having the GRUB on your first HD's MBR, you would just need to install it into the MBR of the second drive.  That way when you boot up your computer, it will either go straight to Vista or if you press F8 it will then load the GRUB and you can select Ubuntu or OSX (provided you can install OSX).  

The easiest way to do this without risking messing anything up would be to disconnect your first HD during the installs.  That way it is physically impossible for anything to get installed on it.  Install as usual, selecting to install the GRUB on the second HD, which during the install will look like the only HD.  Once you get it installed and running, plug the other drive in and boot up.  You should automatically go to Vista.  Then try hitting F8 and it should go to the GRUB which will take you to Ubuntu.


Thats exactly what I was hoping would happen. So the computer will function exactly as normal if I dont do anything during boot up, right? Only if I force the comp to boot from the 2nd HDD will it display grub and then a OS selector (between just OSX and ubuntu, right?). There will no issues with these two HDs running side by side? I obviously wont try to write from one to another, but the OSes themselves wont either...correct?

Frankly, I hear alot of people people messing during install, deleting the wrong partion, corrupting the mbr of their primary HDD, im just surprised more people dont do it this way, seems the risk of trying ubuntu is absolutely zero, whereas there are always risks associated with partioning active OSs....anybody know why more people dont do it this way? Is there something im overlooking?

Thanks!!

---

### Post by egalvan on 2008-12-14
> **falcon61102 said:**
> To accomplish the boot from the second HD without having the GRUB on your first HD's MBR, you would just need to install it into the MBR of the second drive.  That way when you boot up your computer, it will either go straight to Vista or if you press F8 it will then load the GRUB and you can select Ubuntu or OSX (provided you can install OSX).  

The easiest way to do this without risking messing anything up would be to disconnect your first HD during the installs.  That way it is physically impossible for anything to get installed on it.  Install as usual, selecting to install the GRUB on the second HD, which during the install will look like the only HD.  Once you get it installed and running, plug the other drive in and boot up.  You should automatically go to Vista.  Then try hitting F8 and it should go to the GRUB which will take you to Ubuntu.


While I agree that this is a fool-proof tactic to elimnate possible damage to the Vista drive,
the drive designation may change when it is plugged back in,
and that may confuse GRUB.

Be aware of this.

Also, it can be fixed by editing "boot/grub/menu.lst".

---

### Post by falcon61102 on 2008-12-14
As Egalvan pointed out, the drive designations may change once you plug your other drive back in, but that is about a 5 minunte fix compared to trying to recover an entire HD full of lost data.  

Visa will not even be able to see your Ubuntu partition and I doubt that it will see your OSX partition so you don't have to worry about that either.  Ubuntu will see you Vista partition but will not write to it unless you give it specific write priviledges.  I'm not sure how OSX works in that matter, but I'm sure it's something similar.  Basically, unless you set it up to write to your other HD, it shouldn't. 

As far as running both HD's and all OS's, you shouldn't have any problems once you get them all installed and booting.  That is the challenge; once that is complete, it's a piece of cake to run things.

---

