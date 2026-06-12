---
title: "Grub 2 OS Order"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by kiddieland on 2011-06-03
Okay, I have recently been messing around with grub2 menu settings and I have found an easy way of editing the order of the OS displayed on boot. ( Windows XP first )

(OPTIONAL)First paste this code into the terminal to see some info about what I'm going to do.
```
gedit /etc/grub.d/README 
```From the readme file,  you can see that the numbers at the beginning determine what is done  first when you run update-grub in the terminal

Thus, to make Windows XP the first in the grub2 menu, just run this command in the terminal

```
sudo mv 30_os-prober 08_os-prober
```This command renames 30_os-prober to 08_os-prober so it goes before linux 

Finally, run
```
sudo update-grub
```So the grub.conf file is regenerated.
And voila, Windows XP option is at the top again when you reboot the computer :biggrin:  You can also change the order of the other files by renaming the numbers at the front using the same method as above.

---

