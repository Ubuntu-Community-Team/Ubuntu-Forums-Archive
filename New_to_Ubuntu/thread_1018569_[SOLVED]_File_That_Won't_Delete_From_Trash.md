---
title: "[SOLVED] File That Won't Delete From Trash"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by RookieUbuntuUser58 on 2008-12-22
Im able to put it in the trash but not delete it from there.When I restore it I notice it has a lock on the upper right, probably the reason it won't delete. The file contains my drivers for my webcam which I already installed through terminal (using the files in that folder), so I dont need the file anymore. Ive been able to delete it permanently  before, not sure what is different this time. Thanks for any help.

---

### Post by taurus on 2008-12-22
Look to see who is the owner of the file.

---

### Post by DieB on 2008-12-22
as u mentioned with the lock-sign it might be, that u ain't got proper permissions. right-click on the file and check the tab permissions. (if u ain't the owner this will make u it: "sudo chown USER:USER -R /path/to/file/" ,where u replace USER with your name and path to file to the correct path, the tab-key is a help, due to autocompletion)

if u are the owner try: shift-Del for delete without the trash.

---

### Post by RookieUbuntuUser58 on 2008-12-22
> **DieB said:**
> as u mentioned with the lock-sign it might be, that u ain't got proper permissions. right-click on the file and check the tab permissions. (if u ain't the owner this will make u it: "sudo chown USER:USER -R /path/to/file/" ,where u replace USER with your name and path to file to the correct path, the tab-key is a help, due to autocompletion)

if u are the owner try: shift-Del for delete without the trash.

Thanks that worked. Still getting use to Ubuntu. It had my username as the owner but I had to use the code you mentioned and then delete.

---

### Post by DieB on 2008-12-22
that was because some file inside might have had different permissions. probably u compiled it with "sudo make"?

(if u don't know exactly, simply open following file /home/$user/.bash_history and take a look at your last bash actions.

---

### Post by drs305 on 2008-12-22
Here's a link that can further teach you more than you want to know about trash:
[How To: Disk Full? - Check Your Trash]("http://ubuntuforums.org/showthread.php?t=898573")

It explains why some files won't delete, how they came to exist and different methods of finding and deleting them.

---

