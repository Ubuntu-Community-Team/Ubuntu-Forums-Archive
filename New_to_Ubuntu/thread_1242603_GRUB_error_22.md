---
title: "GRUB error 22"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by Majik_420 on 2009-08-17
Ok, I've already searched some and I'm still reading some, but before I go trying to fix this, I'd rather get it crystal clear because it seems I'm treading in water I don't know how to swim in. I'm an aspiring computer genius, but for the moment, I'm learning the hard way.

Ok so I was trying to delete something like 3 screwed up installs of Kubuntu because my computer has power issues and would shut down during the install. That left me with about 7 partitions divided up all weird, so I deleted everything but Windows with GParted, and was gonna start over and try and get a clean install.

At this point, this little system rescue cd is the only thing keeping me alive. I'm reading that I should put in the windows cd and run bootrec from windows RE, But heres my question on this; This laptop originally came with Vista home or wahtever the regular one is. My dad bought Ultimate and said I could put it on my laptop. Problem is I think It can only be liscenced out to three computers or something, and he already put it on his three computers. Didn't find that out untill after I deleted the old vista, So then I was stuck with a "counterfeit" copy and had to try and find Timerstop hacks and what not that never really worked like they were supposed to.
But since my copy of Windows is not Genuine, Will the cd or any of that even work?

---

### Post by Buuntu on 2009-08-20
You can fix GRUB error 22 with a non genuine windows CD as far as I know.  What you will have to do is boot off of it and enter the recovery console, then type 
```
fixmbr
```
This will rewrite you master boot record.
The problem was that GRUB was installed to one of your Kubuntu partitions, which was deleted, so this will rewrite your boot record according to your current partition.
Basically, this will uninstall GRUB for the moment, and boot straight to Windows.  If you want to reinstall GRUB, just installing a new Ubuntu partition will do the trick.

Hope this helps.

---

### Post by LewRockwell on 2009-08-20
ummm....

we thinks, "correct power issues first" might be the most appropriate and prudent course of action at this present point

.

---

### Post by egalvan on 2009-08-20
> **LewRockwell said:**
> ummm....

we thinks, **"correct power issues first"** might be the most appropriate and prudent course of action at this present point
.

+1 for this.


And then download SuperGRUB.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

