---
title: "How to Dual boot Windows 7 professional and Ubuntu 9.10 ??"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by Sari.S on 2009-12-23
[COLOR=Blue][B]Hello members,

I installed Ubuntu 9.10 few weeks ago (after win 7) and whenever I start my laptop I see this menu with too many options (image below)
[/B][B][http://i47.tinypic.com/27zsdt.jpg](http://i47.tinypic.com/27zsdt.jpg) << click to see

and I just want the the original OS's W7 and Ubuntu, I would like windows 7 (the first and the default OS) and ubuntu 9.10 the second OS option. So whenever I start my computer (after 10 seconds) it takes me to Win7 if I don't choose Ubuntu.

can anyone tell me how to go about doing that?

I'm a beginner with Linux Ubuntu :) So Please make it simple for me! :) 
and an easy image or video tutorial would be great :)

sorry if this is posted in the wrong section and if this question has been posted before.


Thanks in advance

Sari.S[/B][/COLOR]

---

### Post by cariboo on 2009-12-24
To remove the second kernel entry use Synaptic Package Manager to remove it. Search for:

```
linux-image
```

and remove the version you don't want.

To change boot order, timeouts and others, you have to edit /etc/default/grub. For more info have a look at the grub2 [wiki]("https://wiki.ubuntu.com/Grub2")

---

### Post by oldfred on 2009-12-24
In the instructions in the wiki above is reference to using numbers or names:

If you refer to Windows by its number, you will have to edit on every update. But Grub 2 also lets you use the title. Suppose your Windows title is "Windows Vista (on /dev/sda1)". Then you can use in /etc/default/grub, and you won't have to edit Grub after kernel updates.

to copy entry from- must be exact:
gedit /boot/grub/grub.cfg
To paste entry into ( I have to have both windows open for the copy/paste to work):
gksudo gedit /etc/default/grub
Change GRUB_DEFAULT=0 to your windows entry like this as example
GRUB_DEFAULT="[COLOR=DarkRed]Windows Vista (on /dev/sda1)[/COLOR]"

---

### Post by Sari.S on 2009-12-26
thanks for answering you guys but I really know nothing about Ubuntu 

so can you make it easier for me :) like in easy 123 steps ;)

thanks in advance

Sari.S

---

### Post by oldfred on 2009-12-26
Open a terminal window from aplications, accessories, terminal copy code into terminal:

1. to copy entry from- must be exact:
```
gedit /boot/grub/grub.cfg
```
2. To paste entry into ( I have to have both windows open for the copy/paste to work):
```
gksudo gedit /etc/default/grub
```
3. Change GRUB_DEFAULT=0 to your windows entry like this as example
GRUB_DEFAULT="[COLOR=DarkRed]Windows Vista (on /dev/sda1)[/COLOR]"

You can lead a horse to water but you can not make him drink.

---

### Post by Sari.S on 2009-12-28
Thanks :)

---

