---
title: "ubuntu boots only 1 in 5 times"
date: 2011-05-24
forum: New to Ubuntu
---

### Post by skilgannon82 on 2011-05-24
i have ubuntu and when its working it runs perfect but it will only boot about 1 in 5 times its annoying but i just put up with it but tonight it seems it will just not boot at all i have been running ubuntu for about a week now and it has loaded most times but now even when i try to boot it with the failsafe graphics mode it still will not boot 
i hope somebody knows what is wrong with this because i have no idea please help

---

### Post by skilgannon82 on 2011-05-24
it gets to grub menu and i choose ubuntu and it gives me a black screen with a flashing _ for a few seconds then it goes to a complete black screen and just hangs till i turn it off

---

### Post by oldfred on 2011-05-24
At the grub menu, press e for edit and remove splash quiet. You will then see every line of the boot process and see what stops or when it works what the next line is. It can go by fast. 

The same info is in the log files with time stamps - System, Administration, Log File Viewer. Several files have different info on history of your system. So if you can boot you can see some of the history and if something either repeats many times trying to load or has a long time between entries meaning it took too long.

---

### Post by skilgannon82 on 2011-05-24
sorry but im a total noob i did press e and saw all the options but i wouldnt have a clue what the information i got back from it means

---

### Post by oldfred on 2011-05-24
When it stops booting what is on the screen. Or what error messages or long time waits are in the log files?

---

