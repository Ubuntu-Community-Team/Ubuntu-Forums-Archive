---
title: "Why can't I edit fstab?"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by manwood on 2010-05-26
I have just setup a dual boot with windows 7 and ubuntu 10.04. The windows partitions have been mounted and appear in the places menu and on the desktop. I want to remove them - I definitely don't want to be accidentally tampering with windows partitions outside of windows. So.. I tried just unmounting them, but get an error. I have tried commenting out the relevant lines in fstab, but I cannot save the file as I don't have permissions - why do I not? I'm admin surely? How can I edit this file?
 
Thanks

---

### Post by -humanaut- on 2010-05-26
sudo nano /etc/fstab

that should do the trick.

---

### Post by drs305 on 2010-05-26
Looks like it's time to dust off this classic:
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

Even though you may be the only person using the computer, to change system files you have to gain temporary privileges to do so. The above post describes this aspect of Linux.

---

### Post by TheStroj on 2010-05-26
Exactly as -humanaut- said. You must edit file as root. For easier editing you can also do 'sudo gedit /etc/fstab'

---

### Post by GSF1200S on 2010-05-26
> **-humanaut- said:**
> sudo nano /etc/fstab

that should do the trick.

Just to add to this comment: you can substitute 'nano' for any text editor of your choice. Technically, for root priveledges when running a GUI application, you would use gksu:
```
gksu gedit /etc/fstab
```

nano is a command line based editor that aims to be simple to use. The above commands basically equate to the following:
sudo nano /etc/fstab
as super-user (root) do >> open application nano >> to location /etc/fstab.

Maybe you already know all this, but perhaps it will help someone :)

---

### Post by lil0tik on 2010-05-26
And, just to add a touch more...

You'll need to "sudo [favorite text editor] [filename]" for any file that is not in your home directory.

---

### Post by fooman on 2010-05-26
> **TheStroj said:**
> Exactly as -humanaut- said. You must edit file as root. For easier editing you can also do 'sudo gedit /etc/fstab'

to expand a little on that:  when using a graphical file editor as root,  you should use gksudo:

```
gksudo gedit /etc/fstab
```save regular sudo for command line editing (like nano).

an expalnation is in the link that drs305 posted above (see: graphical sudo).

EDIT: sorry,  already posted above by GFS1200S ...i type sooo slow.

---

### Post by bodhi.zazen on 2010-05-26
> **-humanaut- said:**
> sudo nano /etc/fstab

that should do the trick.

For the lazy typer :twisted:

```
sudo -e /etc/fstab
```

---

### Post by manwood on 2010-05-26
Thanks for the quick and helpful responses guys, great stuff :)

---

