---
title: "Two boot menus"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by jestang93 on 2009-09-18
I installed Ubuntu 9.04 with Wubi. Before installation, I had installed the CD Boot Helper. There were no problems with the installation and everything went fine but I ended up with two boot menus.

The first one is:
Ubuntu 9.04 kernel ...
Ubuntu 9.04 kernel (recovery mode) ...
Other operating systems:
Windows XP professional


When I choose Windows XP, a second menu opens up:
Windows XP Professional
Ubuntu


I would like to remove this second menu.

Thanks!

---

### Post by seshomaru samma on 2009-09-19
You need to edit the boot.ini file in the root of your Windows installation
Go to control panel>folders and make sure all system files and hidden files are accessible. Then go to your Windows partition (most probably " C: ") and look for boot.ini.[U][B]
Make sure to make a back up of boot.ini before you do anything [/B][/U] (if something goes wrong ,you can always restore the original file) 
Open it with wordpad or whatever and you will see those two line , get rid of the Ubuntu line.

---

### Post by talsemgeest on 2009-09-19
Easier to go to Start>Run and type in msconfig, then push enter. Go to the "Boot" tab, select the "Ubuntu" option, and click delete.

---

### Post by seshomaru samma on 2009-09-19
I wasn't aware of that...
a much easier way indeed

---

