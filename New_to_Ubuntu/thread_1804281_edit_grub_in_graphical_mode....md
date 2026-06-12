---
title: "edit grub in graphical mode..."
date: 2011-07-14
forum: New to Ubuntu
---

### Post by owiknowi on 2011-07-14
does a package similar to easybcd for closed windows, also exists for linux?

easybcd let's you add all kinds of entries to the closed windows bootloader from a gui. i would prefer to use grub as bootloader though.

thanks in advance for any suggestions!

---

### Post by Quackers on 2011-07-14
I think such a thing exists (Grub Customizer, maybe but you should be aware of something.
When you introduce anything to a boot process you increase the risk of future boot failures. The booting process is like a chain with link after link. This chain can easily be broken. Any change made today may have no detrimental effect until you run an update 3 months down the line. Then you don't know where to look!
What is it that you want to do, exactly?

---

### Post by owiknowi on 2011-07-14
@quakers:
thanks for your reply.

doing a lot of penguin testing and most of the time have about 8 different distros installed.
but often, sometimes even on a daily base, new penguins get installed.

with easybcd i'm able to add a new entry to the bootloader from closed windows very quickly.
manually editing grub, as i used to do in the past, takes more time.

been using easybcd now for several years and never encountered any problems (always have one enterprise or lts penguin installed as default os).

only downside are those closed windows on my computers... but they come shipped with the laptop anyways.

---

### Post by Quackers on 2011-07-14
If you're using grub2 and it is in control of the mbr all you have to do to get the new menu entry is run sudo update-grub in the system whose grub has control.

---

### Post by owiknowi on 2011-07-14
thanks quackers, also on behalf of the penguins, that sure seems worth a try!

the penguins don't like closed windows even less than me, it all becomes a bit musty inside that way (you probably dispose of closed windows in your puddle?) ;)

---

### Post by Quackers on 2011-07-14
Yes, I'm in the open air :wink:

If you want to install grub to the mbr of the drive just boot into the system which you want to have in control of grub (the latest Ubuntu version would be best as the latest grub will then be used) and in the terminal just run ```
sudo grub-install /dev/sdX
``` where /dev/sdX is the hard drive you boot from (most would be /dev/sda, for instance, but not all).

---

### Post by owiknowi on 2011-07-14
have also 11.04 installed on sda, so that shouldn't be a problem.
thanks again for your help and advise.

p.s. just saw that 10.04.2, my default working penguin, also provides grub2.

---

### Post by Quackers on 2011-07-14
No problem and good luck.
Feathered friends should help each other :-)

---

