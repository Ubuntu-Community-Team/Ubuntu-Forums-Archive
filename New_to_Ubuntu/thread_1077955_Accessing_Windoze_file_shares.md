---
title: "Accessing Windoze file shares"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by Ponderous on 2009-02-22
I'm trying to access windoze file shares.  I go to places, but I don't see anything that says Network or Windows Network.

Thanks for any help.

---

### Post by llamabr on 2009-02-22
What does this mean "I go to places"?

Plus, pardon my windows ignorance, but what's windows shares?  You just want to mount a windows partition, and browse files?

---

### Post by abn91c on 2009-02-22
if you installed using wubi the windows files are under /host
in a regular dualboot it may be under the /media or /mnt folders

---

### Post by Ponderous on 2009-02-23
I'm sorry I wasn't specific enough.  I can access the Windows files from the dual boot.  I'm talking about my Windows desktop.  For instance, I want to access all my music, photos etc that are shared on my Windows desktop. I'm trying to see them on my Xubunut laptop.  I'm trying to use Samba and don't know where to start.  The help docs say to go Places\Network but that isn't an option for me under Xubuntu.  It's not there.

---

### Post by theozzlives on 2009-02-23
did you do:
```
sudo apt-get install samba
```
you also have to edit /etc/samba/smb.conf as root to change the workgroup, then:
```
sudo /etc/init.d/samba restart
```

---

### Post by tarps87 on 2009-02-23
The network option is not in xfce desktop manager, my suggestion would be to install a program called pyneighborhood it is the the Ubuntu repositories.
You will also need to install samba as suggested in the post above

---

### Post by roger_1960 on 2009-02-23
Hi

Have a look at this post:
[http://ubuntuforums.org/showthread.php?t=304131]("http://ubuntuforums.org/showthread.php?t=304131")

---

### Post by sydbat on 2009-02-23
AFAIK, you don't do anything with samba if you are just accessing the NTFS partition on the same computer. The OP has stated this is a dual boot situation.

What you need to do is mount the NTFS partition(s) to access the data you want (music, etc). You will only be able to look at the folder that contains the Windows desktop icons.

If I am wrong, please try the other samba-related advice posted.

---

