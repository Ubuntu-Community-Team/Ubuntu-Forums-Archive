---
title: "[SOLVED] &amp;quot;Permission Denied&amp;quot; after smbmount"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by mccartyj on 2007-08-07
Hello all,

I am trying to connect my Xubuntu laptop to my XP destop to a shared folder with all of my music. I had this working on another Xubuntu computer, but now nada.

The smbmount part works fine (or at least it gives me no errors), but when I do an ls to the mount point, I get "Permission Denied". I've tried chown and chmod and neither work. 

WIth CIFS, I get "mount error 20 = not a directory" (after I unmount the mount point and verify that I can browse it.

Most of the problems I have found associated with this error is lack of sudo use or ownership issues...

Thanks in advance!

---

### Post by jimrz on 2007-08-07
> **mccartyj said:**
> Hello all,

I am trying to connect my Xubuntu laptop to my XP destop to a shared folder with all of my music. I had this working on another Xubuntu computer, but now nada.

The smbmount part works fine (or at least it gives me no errors), but when I do an ls to the mount point, I get "Permission Denied". I've tried chown and chmod and neither work. 

WIth CIFS, I get "mount error 20 = not a directory" (after I unmount the mount point and verify that I can browse it.

Most of the problems I have found associated with this error is lack of sudo use or ownership issues...

Thanks in advance!

how are you trying to mount it?

---

### Post by mccartyj on 2007-08-07
sudo smbmount //PRIME/Music /Music -o guest

I have also tried it with user name and password. Again, no errors during the mounting...

Also chmod and chown only work when it is unmounted.

---

### Post by jimrz on 2007-08-08
> **mccartyj said:**
> sudo smbmount //PRIME/Music /Music -o guest

I have also tried it with user name and password. Again, no errors during the mounting...

Also chmod and chown only work when it is unmounted.
you need to make a mount point for the share
```
cd ~
mkdir samba
```
or whatever you choose to name the new dir, then you can mount it in your home directory and avoid permission issues by
```
sudo smbmount //PRIME/Music /Music /home/<your username>/samba -o username=<your username>,password=<your password>,uid=1000,mask=000
```
just adjust for your user name/pword

---

### Post by mccartyj on 2007-08-09
Nope, same effect and I did have a mount point originally (/Music) that I was mounting to.

---

### Post by jimrz on 2007-08-09
> **mccartyj said:**
> Nope, same effect and I did have a mount point originally (/Music) that I was mounting to.

you might see if using the ip address rather than "PRIME" [assume that is the host computer's name] works any better

---

### Post by mccartyj on 2007-08-10
Still the same thing. I am going to try removing Samba and SMBFS and reinstalling. I'm also going to update my other Xubuntu box and see if it has the same probled.

Thanks for your help.

---

### Post by mccartyj on 2007-08-11
Yep, same problem on my other box. I know that one worked and I didn't edit the FSTAB. It's gotta be something to do with Feisty and XP.

---

### Post by mccartyj on 2007-08-11
Figure it out. The problem was on the XP side. Under sharing and security, I had "Allow Users to Modify Files" selected. In the general properties, "Read Only" was greyed and checked. I unchecked this a while ago to make sure nothing was read only in the folder, but Windows resets that property everytime I come back.
[B]
Solution:[/B] Uncheck "Allow users to modify files" and voila! No "permission denied". I guess this means no editing permissions for me, but that's ok.

Thanks for the help jimrz

---

