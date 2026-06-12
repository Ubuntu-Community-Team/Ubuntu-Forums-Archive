---
title: "Switching from ubuntu to xubuntu"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by n213978745 on 2011-01-31
hi all,

Recently I want to switch to Xfce Desktop Environment instead of Gnome.  I have intention of doing clean-reinstallation of whole OS, except the home directory:

I want to backup the home directory, and getting rid of those irrelevant files that will only be used on Gnome Desktop Environment -- I want to get rid of configuration data sush as gedit, nautilus, Brasero etc. under my home directory.

And my question is: is there a command to enable me to find configuration data easily under the home directory?

I know there is a command named:
```
$ dpkg -L <pakcage>
```This will allows me to see the file location of package, but it doesn't tell me any installed under the home directory.  And I need a command that will indicate the location of preference/configuration files under one's home directory.

Sorry to trouble you guys and I thank everyone who read it and try to help me

---

### Post by tpprynn on 2011-02-01
Recently I did something similar and used a method that just occurred to me would enable me to preserve music, video, pictures and so on without keeping any Ubuntu settings.

I went into /home as root with 

alt + F2

gksu nautilus [Enter]

navigating to /home/[my name] and then made visible hidden files with ctrl H, highlighted everything with ctrl A and then unhighlighted the relevant folders like Documents, Videos and so on. Then I pressed the Delete key to delete all these highlighted files, which the new O.S. would cleanly reinstall and rebooted with my live CD. The clean operating system with fresh settings was installed - choosing not to format /home during the process - and all my data was completely intact.

This might not be the recommended method but worked perfectly.

---

