---
title: "How to enable root login in kubuntu"
date: 2010-09-04
forum: New to Ubuntu
---

### Post by techfolkcmr on 2010-09-04
Hi all,

 I have set root passwd using terminal and when try to login it says root logins are not allowed. The main thing why i need to login as root is to edit the bootcfg file (i.e) grub.cfg file. Everytime when i update the generic header appends to the top of the list and the older one doesnt get deleted automatically and also i want to order my windows OS during boot. And also please tell me how to edit that grub.cfg in terminal. Thanks in advance.

---

### Post by ronnielsen1 on 2010-09-04
sudo gedit fileyouwanttoedit

---

### Post by mcduck on 2010-09-04
You don't need to enable the root account, or to log in as root, to edit any configuration file. Ubuntu uses "sudo" to allow you to do such tasks as your normal user.

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

What comes to removing old kernels from Grub, the best way to do it is not t edit the config file, but instead to actually uninstall the old kernel versions, and they will be removed from the boot menu automatically (plus you gain back the drive space taken by the old kernel files).

Furthermore, it's not recommended to even touch the grub.cfg file itself, instead you should edit the actual configuration files for Grub. This will also make the changes you make stick, so you don't need to edit files again and again after each update.

Here's a Grub2 HowTo for you: [http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

(for editing config files as root user you can simply run "kdesu kate /path/to /your/file" if you want to use a graphical editor, or "sudo nano /path/to/your/file" if you prefer a CLI editor.)

edit: By the way, giving instructions for enabling root account or logging in as root is actually prohibited by forum rules. The reasoning is that it's not generally recommended (for both security reasons and that it makes it a lot easier for you to accidentally break your system), it's not how Ubuntu's security model works (so doing it would make it harder for people to help you here), it's very rarely actually required for anything, and those few who might need to do that will definitely already know how to do it.

---

