---
title: "Sudo: unkown user: root error (Please Help!)"
date: 2011-04-22
forum: New to Ubuntu
---

### Post by xxthegonzxx on 2011-04-22
Ok so first off, I'm a TOTAL newbie! I'm just learning as I go so thank god this is a test machine. Anyway, this is what happened...

I was using vi to edit the passwd file within etc/passwd.
I wasn't too sure how to use it completely and ended up ruining the first line of code:

"moot:x:0:0:root:/root:/bin/bash" 1 simple little word and instead of root i have "moot" lol.

As I tried to change it back I kept getting the error "E45: 'readonly' option is set (add ! to override)"
ok...I then proceed to type ":w!"
then I get ""passwd" E212: Can't open file for writing".

The permissions on the passwd file are "-rw-r--r-- 1 moot root 2024 2011-04-22 17:37 passwd"
I know I need to use chmod to change the permissions but I can't without using the sudo command!
Everytime I use "sudo chmod 777 passwd" i get an error stating "sudo: unknown user: root".

Can anyone please help? I don't want to reinstall Ubuntu again. I read somewhere that the passwd- file is the original needed but since I cannot edit or delete the current passwd file there's nothing I can do. Thanks a million in advance.

---

### Post by pi3.1415926535... on 2011-04-22
You can use a live CD will give you sudo access automatically. In order to do this you must first boot the live CD, then mount the drive Ubuntu is installed on, then navigate to the passwd file and change it.

---

### Post by xxthegonzxx on 2011-04-24
Thank you! After doing some digging, I performed Live CD solution. I had to insert Live CD and copy passwd file from cd to HDD installation of ubuntu using the terminal. I was able to properly copy over the file but was not able to login due to the password for login being incorrect. I tried changing the password for the user but to no avail. :(

Final Solution: I said "screw it" and decided to re-install Ubuntu again on HDD. Copying the passwd file from LIVE CD looks like it's the best and easiest option. You might have to do some additional steps after but If it's just a test machine re-install is way easier!

---

### Post by Karlchen on 2011-04-24
Hello, xxthegonzxx.

After you had booted you LiveCD, you should _not_ haved copied the /etc/passwd file of the Live CD to the Ubuntun installation on your harddisk.
Instead you should have edited the passwd file on your harddisk and corrected the mistyped "moot" to read "root".

Kind regards,
Karl

---

### Post by Thewhistlingwind on 2011-04-24
> **Karlchen said:**
> Hello, xxthegonzxx.

After you had booted you LiveCD, you should _not_ haved copied the /etc/passwd file of the Live CD to the Ubuntun installation on your harddisk.
Instead you should have edited the passwd file on your harddisk and corrected the mistyped "moot" to read "root".

Kind regards,
Karl
This ^ 

Remember, physical access == root access, that is, anything you could do with root in the actual install can also be done with a boot CD.

---

