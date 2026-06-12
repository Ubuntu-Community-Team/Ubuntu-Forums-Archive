---
title: "Backing up repositories/downloaded updates etc"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by thescubadude on 2009-11-05
Hello, so I am completely new to Ubuntu and linux, installed it for the first time about 3 weeks ago and have been using it as my internal webserver for testing web development projects.

I was on Ubuntu 9.04, upgraded to 9.10, had issues with virtual servers in apache which I could not resolve. I then downloaded the iso, did a fresh install, experienced the same problems. I am now back on 9.04 after downloading all the updates and other features I needed. I have limited, slow, capped internet at home!

I have now found what I think may be the solution to my problem and want to do a fresh install of 9.10. However should I not succeed I would like to be able to revert to 9.04 without having to download all the stuff again.

I came across an application called APTonCD which seemed perfect. Only problem is it keeps crashing at about 80% scan so I can't make a backup of my repositories....

Is there any way I can back-up all my downloaded apps so I can install them without the need to download them again should I need to revert to 9.04 (i.e. LAMP Server, phpmyadmin, all the updates for 9.04, Amorak etc)

---

### Post by JamesUser on 2009-11-05
You don't really need AptonCD. You might want to check this out.  [http://ubuntuforums.org/showthread.php?t=819396](http://ubuntuforums.org/showthread.php?t=819396)

---

### Post by jimmy the saint on 2009-11-05
If it is a configuration issue, you can probably just put in the cd you burned to do the installation and boot into it.  That way you can test the changes without even touching your HD.  If they don't work you don't have to worry because your 9.04 installation will not have been touched.  If any of the changes require a restart of the system, though, this won't work because on a live CD, changes are not saved through power offs.

---

### Post by JamesUser on 2009-11-05
Check out the community documentation too [https://help.ubuntu.com/community/InstallingSoftware#Backup/Restore%20installed%20packages](https://help.ubuntu.com/community/InstallingSoftware#Backup/Restore%20installed%20packages)

---

### Post by thescubadude on 2009-11-05
Thanks

---

