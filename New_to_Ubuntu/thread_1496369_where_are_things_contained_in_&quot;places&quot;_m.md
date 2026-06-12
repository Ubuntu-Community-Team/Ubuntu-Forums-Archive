---
title: "where are things contained in &quot;places&quot; mounted ?"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by womd on 2010-05-29
Hi !

this might be a easy one for you ubuntu-gurus... i only use terminal window in normal cases ... but now i'd like to use *nix as desktop and felt very comfortable with ubuntu .... but im still stuck at the basic's, so i'll explain:

i mounted a directory shared by samba over vpn using the "Places"->"Connect to Server" menu.

i can view the content by clicking on its entry under "Places", but now i want do make that directory as my workspace in eclipse ... and i cannot find it ...

generally if i use a program like gphpedit or similar .. i would like to use the "open - file" dialog, then browse there ...  

but where ist it mounted to ?   mtab and fstab don't show anything i could identify with this ...

someone could point me in the right direction please ?


tank you


--update:

things in "places" are shortcuts, from  /home/myuser/.gtk-bookmarks

there i can see the "shortcut" i want to use: 

smb://username@ip/directory foldername

... so far so good ... but i cannot use this in any "open file" dialog ...


--- update:

at ([https://help.ubuntu.com/7.04/user-guide/C/places-menu.html](https://help.ubuntu.com/7.04/user-guide/C/places-menu.html)) i read that the shrotcut "Desktop" should link to anything on my desktop.  The "remote-folder" is on my desktop, but using this "shoutcut" sends me to an empy place ?

-- update:

ok, got it working for gphpedit now,
if i drag the folder from my desktop to the "open file" dialog i get something like: 

x-nautilus-desktop:///username%20on%2010.9.8.1.volume

but does not work for eclipse, however it works , i'd like to know why what is happening here .  any clue ?


-- update:

reading about "nautilus-actions" configuration seemed to me that i'm trying todo something here which it is not built for .... 

got back to mount it by "hand" .... but still looking forward to get info ....

---

### Post by -humanaut- on 2010-05-29
cat /etc/fstab

and post back please.

---

### Post by womd on 2010-05-29
hi, thank you for your reply here is the output

```
womd@womd-dev-pc1:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=fb3ed6fa-1a8f-48b2-99c8-1cc1ebd7c3a3 /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
womd@womd-dev-pc1:~$ 

```

nothing else shown than the local disk .. or do i miss something ?

---

### Post by philinux on 2010-05-29
@womd most things get mounted under the /media folder. e.g usbsticks cd's external hard drives etc.

---

### Post by womd on 2010-05-29
hi! yes thank you, in the media folder my 2nd harddisk is shown.

but no trace of that "mounting" i did via "places" -> "connect to server"

greetings

---

### Post by Morbius1 on 2010-05-29
/home/your_user_name/.gvfs

Don't forget the "." before the gvfs .

---

### Post by womd on 2010-05-29
oh, yes ! that's it ! :guitar:
thank you !

---

