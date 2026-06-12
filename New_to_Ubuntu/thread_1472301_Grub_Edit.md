---
title: "Grub Edit"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by hussein1985 on 2010-05-04
Hey every one,

am a new user of ubuntu. I have a problem with my grub.

I have a Toshiba TECRA A8-EZ8512 laptop. installed on it windows 7 and ubuntu 9.04 with a gnome of version 2.26.1.

the problem is that the grub is not appearing on starting up the laptop, it is hidden by the Toshiba welcome screen. I can randomly choose from the grub by using the arrows but I can't see what I am choosing.

The only way to see the grub is by loging into ubuntu and restarting the machine.

But after shuting down and restarting the machine, the problem will resume.

I appreciate any help in trying to edit the grub in way that it can be seen.

---

### Post by RetchingRabbit on 2010-05-04
You might want to try getting into the bios settings and see if you can disable the splash screen from there. 
This doesn't sound like a grub issue, per se.

---

### Post by xumuk37 on 2010-05-04
could you show us your /boot/grub/grub.cfg ?

---

### Post by Animal X on 2010-05-04
i have this problem too, but also with my bios screen, i think its because im using a tv instead of a monitor, once grub loads up the menu im good ,but new installations and my bios and live cds are always way over to the left.

---

### Post by hussein1985 on 2010-05-04
thx for the help retching rabbit but i cant disable the splash screen or maybe i missed knowing how. i entered the bios and didnt find anything related to it.

xumuk37 i cant find the grub.cfg file in the path you mentioned. could it be hidden? or there is no hidden files in ubuntu?

can't i change the time the grub appear in ?? so that i can postpone it to appear after the splash screen?

---

### Post by nitstorm on 2010-05-04
ubuntuforums.orgubuntuforums.org/showthread.php
ubuntuforums.orgubuntuforums.org/newreply.php
> 
xumuk37              **Re: Grub Edit**
         could you show us your /boot/grub/grub.cfg ?     
The person is using Ubuntu 9.04 which uses The legacy GRUB by default.

@Hussein1985: Look [here]("https://help.ubuntu.com/community/GrubHowto") and [here]("http://www.dedoimedo.com/computers/grub.html"). I don't know if you can delay the GRUB menu to show up later but you can alter the TIMEOUT so that it stays longer(longer than the splash screen)

---

### Post by Animal X on 2010-05-04
> **nitstorm said:**
> ubuntuforums.orgubuntuforums.org/showthread.php
ubuntuforums.orgubuntuforums.org/newreply.php
The person is using Ubuntu 9.04 which uses The legacy GRUB by default.

@Hussein1985: Look [here]("https://help.ubuntu.com/community/GrubHowto") and [here]("http://www.dedoimedo.com/computers/grub.html"). I don't know if you can delay the GRUB menu to show up later but you can alter the TIMEOUT so that it stays longer(longer than the splash screen)
is that the same thing as timeout=sec on the menu.lst ?

---

### Post by xumuk37 on 2010-05-04
so  cat /boot/grub/menu.list

---

### Post by Animal X on 2010-05-04
> **xumuk37 said:**
> so  cat /boot/grub/menu.list
list wouldnt be spelled out though, just .lst

---

### Post by nitstorm on 2010-05-04
ubuntuforums.orgubuntuforums.org/newreply.php
> **Animal X said:**
> is that the same thing as timeout=sec on the menu.lst ?
yes :)
and
> 
so  cat /boot/grub/menu.list 	

and that would just display the file not give you the option to edit it.

so,
```

sudo gedit /boot/grub/menu.lst

```
to edit it, and please be careful. Cheers!

---

### Post by hussein1985 on 2010-05-04
thx for trying guys but i tried to cahnge the timeout and it worked but the splash screen is still stuck with the grub for 2 min (the time i changed) 

it is like an error both starting at the same time

---

