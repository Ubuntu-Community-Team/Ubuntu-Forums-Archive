---
title: "Terminal cant find file"
date: 2010-04-13
forum: New to Ubuntu
---

### Post by tottetotte on 2010-04-13
Im about to go insane. Ive tryed to get my dual monitor working on Nvidia but everytime I reboot my computer I have to fix my xorg.conf file to save Nvidia config. But now all the suddon it dosnt work. The command is 
[FONT=Verdana][COLOR=Black][B]sudo mv -i /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
cannot stat '/etc/x11/xorg.conf/' no such file or directory
[/B][/COLOR][/FONT]It worked before but now it wont let me do it. Ive checked like 10 times if the file is gone or somthing but its there. Even the backup.

What is wrong? Why do I suffer this nonsense?

---

### Post by tottetotte on 2010-04-13
Just found out that this command works fine
Sudo gedit /etc/x11/xorg.conf

---

### Post by tottetotte on 2010-04-13
I had to change them too '/etc/x11/xorg.conf' '/etc/x11/xorg.conf.backup'. I found it out on the hard way.
Thanks for the help everyone. Without you I wouldnt be here :confused:

---

### Post by tottetotte on 2010-04-13
AW ****. Its sensetive cases. Thanks again everyone

---

