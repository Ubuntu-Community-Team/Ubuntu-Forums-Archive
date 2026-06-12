---
title: "data recovery"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by watchstone on 2009-05-08
Whilst updating from version 8.10 to 9.04 I had a power cut.     On boot up later it was obvious that the installation is partial and it is corrupted.     The start-up screen tells me that various files do not exist and it is dropping to a shell.

Then:-     BusyBox v1.10.2 (Ubuntu 1:1.10.2) built in shell (ash)
               (initramfs)  _

I have only been using Ubuntu for a short time and this is beyond me at present.

I have installed version 8.10 on a spare hard drive and can access the corrupted Ubuntu partition. I intend to copy my data if possible and then start again with the upgrade.

I was using Evolution mail. Can anyone tell me where the program saves the mail. I can't seem to find it.

---

### Post by louieb on 2009-05-08
Don't use Evolution myself. But its like most of the Gnome desktop and stores its settings and mail in your home directory in a hidden folder named **.evolution  **

to toggle showing hidden  files and folders press ctrl+h 

Good Luck.

---

### Post by LowSky on 2009-05-08
copy all your information fomr your /home folder to save the data. I'm not sure we Evolution keeps the downloaded messages (it might be in it hiddne home file, just I'm not sure), maybe someone else on here knows the file name exactly

---

### Post by watchstone on 2009-05-08
Many thanks, will give it a try

---

### Post by thomps on 2009-05-08
I've used this post to recover Evolution data before:

[http://ubuntu.wordpress.com/2005/12/03/how-to-backup-evolution/]("http://ubuntu.wordpress.com/2005/12/03/how-to-backup-evolution/")

It mentions the folders the data is stored in under Step #2.

---

### Post by gandaran on 2009-05-08
evolution mail is stored in /home/'user'/.evolution/mail/local
copy/paste only the files in the local folder like inbox or whatever the folder name you keep email to the same location in the new .evolution setup.

---

### Post by watchstone on 2009-05-08
Hello everyone - 

E-mails and all data recovered and also backed up

Many thanks for your advice  :P

---

