---
title: "Moving picture folder out of Root user"
date: 2011-08-19
forum: New to Ubuntu
---

### Post by toastermm on 2011-08-19
I recently had to recover a partition with pictures on it.  Shotwell did a great job, but put all the pictures in the root user's picture folder.  I am trying my hardest to move the picture folder over to my current user's pictures directory.  The user has an empty picture folder, so no need to worry about overwriting.  Here is what I'm trying.

```
user@computer:~$ gksudo mv -r ~/Pictures/ /user/Pictures/
```

It thinks for about 5 seconds, and gives no error message.  But alas, the user's picture folder is empty.  I thought using the '-r' option meant recursive, but no pictures are showing.  Hrm.  So I tried the following.

```
user@computer:~$ mv -r ~/Pictures/ /user/Pictures/
mv: invalid option -- 'r'
Try `mv --help' for more information.
```

Now I'm confused.  I thought '-r' was an option for moving. Correct?

---

### Post by LowSky on 2011-08-19
nope -r isn't maybe your thinking of rm command.

and just use sudo, no need for gk.

```
sudo mv /pictures /home/user/pictures
```

---

### Post by toastermm on 2011-08-19
Thanks for the quick reply.  Changing to sudo and using no -r option gives...

```

user@computer:~$ sudo mv /pictures/ /home/user/pictures/
mv: cannot stat `/pictures/': No such file or directory

```

I'm not sure how to reference the root user without gksudo.  I can see the pictures if I type in "gksudo nautilus" and browse to the pictures folder in root.  I just would like to move them to the user directory.

---

### Post by Ozymandias_117 on 2011-08-19
sudo is to reference root for command line programs, gksudo is for graphical apps (In Gnome).  Are you sure you got the case correct for the folder you're trying to move? Linux is case-sensitive.

---

### Post by toastermm on 2011-08-19
Got it.

First changed to root:

```
user@computer:~$ su -s
root@computer:~# mv /root/Pictures /home/user/Pictures

```

Done.  Thanks for the help- finally figured it out.

---

### Post by mikewhatever on 2011-08-19
The problem now is that the 'Pictures' folder and content are owned by root and you can't modify them. To change the ownership, run the following as user, not as root:
```
sudo chown -R $USER:$USER /home/$USER/Pictures
```

---

