---
title: "Advice: installing windows xp on spare partition"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by Lakeside5 on 2008-12-05
Ok, I don`t want to keep posting in the beginner thread, but I`m not sure where this goes, so feel free to move, of course :) Well, I had good intentions of my computer being just for Linux (have Hardy Heron server installed in a 69gb partition, and another 100 or so gb partition, with some junk stored on it (slowly deleting, don`t really need it) and about 30gb of that free. Hate me ;) but I can`t get into gimp(I tried, really) or break my PS addiction. My question, how can I install a windows xp os on that 100gb partition (actually not on the whole 100 gb, maybe I would want to keep another partition with 50 or so gb free). Of course I will google for this, but always like to ask here first too. thanks.

---

### Post by nakama85 on 2008-12-05
> **Lakeside5 said:**
> Ok, I don`t want to keep posting in the beginner thread, but I`m not sure where this goes, so feel free to move, of course :) Well, I had good intentions of my computer being just for Linux (have Hardy Heron server installed in a 69gb partition, and another 100 or so gb partition, with some junk stored on it (slowly deleting, don`t really need it) and about 30gb of that free. Hate me ;) but I can`t get into gimp(I tried, really) or break my PS addiction. My question, how can I install a windows xp os on that 100gb partition (actually not on the whole 100 gb, maybe I would want to keep another partition with 50 or so gb free). Of course I will google for this, but always like to ask here first too. thanks.

Boot to Windows disk. 
Create partition you want it on in empty space. (make sure it's on the hard drive you want otherwise you will end up writing over Ubuntu and will lose the install)
Install Windows on that partition. 
After install boot from ubuntu live cd. 
Reinstall Grub bootloader. 
Finished

You will need to reinstall grub because windows does not give you the option to bypass its boot loader install.

Furthermore the windows boot loader will not see Ubuntu where Grub WILL see Windows.

---

### Post by Paqman on 2008-12-05
Have you tried Photoshop in Wine?

---

### Post by yellowaeroplane on 2008-12-05
It's a lot less frustrating if you do it the other way around (ha, but I'm sure you realized that). But honestly, if you don't have tons of files on your Ubuntu install, just back up your basic home directories (documents, images, Firefox profile... etc) to an external hard drive or something and then just install Windows first... it'll probably save you a lot of headache.

By the way, I'm running Photoshop CS2 in Ubuntu under Wine and it works pretty damn well.

Good luck!

---

### Post by Lakeside5 on 2008-12-05
Thanks for all the great replies everyone. Yes, I see now that I`ve done it backwards lol.  Just to make things simpler, I might try running Photoshop cs2 on wine again, although I just could not do it. I am curious to know how you did it. And if that doesn`t work I shall use Nakama85`s great instructions. thanks

---

