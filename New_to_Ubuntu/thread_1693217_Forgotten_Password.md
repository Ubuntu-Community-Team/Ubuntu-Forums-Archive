---
title: "Forgotten Password"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by happytuesdays on 2011-02-22
I have forgotten my password.  I sent my netbook off for repair and can't remember the password.

Booting into recovery mode and dropping to root shell prompt I am asked for the root password (don't remember it or setting one)

Editing the kernel line in the recovery mode option in grub (by adding ro init=/bin/bash) gives me a passwordless root BUT

When I do :
passwd netbookuser 
and I am prompted for password twice   I get Authentication Token Manipulation Error.

So I have no idea what to do.

:popcorn:

---

### Post by Foxheadz on 2011-02-22
GOOGLE IS YOUR FRIEND:[http://www.debuntu.org/recover-root-password-single-user-mode-and-grub](http://www.debuntu.org/recover-root-password-single-user-mode-and-grub)

---

### Post by uRock on 2011-02-22
> **ajgreeny said:**
> Anyway, to answer your problem have a look at  [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword) but don't forget that the  ubuntu family of OSs, do not use a root password, but sudo instead  which raises the permissions of a user in the admin group to that of  root until the terminal is closed, or the pre-defined time limit is run.
+1 The advice on that link should be sufficient.

---

### Post by sisco311 on 2011-02-22
> **happytuesdays said:**
> 
Editing the kernel line in the recovery mode option in grub (by adding ro init=/bin/bash) gives me a passwordless root BUT

When I do :
passwd netbookuser 
and I am prompted for password twice   I get Authentication Token Manipulation Error.


You have to use the `rw init=/bin/bash' kernel parameters and you may have to remount the root partition as rw:
```
mount -o remount,rw /
``` 

If this doesn't work, then you can reset the password with a Live CD or USB. 

[list=i]
[*] Boot a Live media and open a terminal.


[*] mount the root (`/') partition; assuming that it's /dev/sda1:
```

sudo mkdir /mnt/root
sudo mount /dev/sda1 /mnt/root

```


[*] mount the virtual filesystems:
```

for file in dev dev/pts proc sys; do
  sudo mount /$file /mnt/root/$file
done

```


[*] chroot into Ubuntu:
```

sudo chroot /mnt/root

```


[*] change your password and lock or change the root password:
```
passwd username
usermod -p '!' root     # or: passwd root

```


[*] log out from the chroot:
```
exit    # or press Ctrl+d
```


[*] reboot:
```
sudo reboot
```
[/list]

---

### Post by sisco311 on 2011-02-22
> **uRock said:**
> +1 The advice on that link should be sufficient.

It's not. If the root account is enabled, then the single user mode (a.k.a Recovery Mode) will prompt for the root password. The OP also has issues with the init=/bin/bash kernel parameter...

I know that there is a video at the end of aysiu's guide which shows you how to reset the password with a Live CD, but I don't like his method. I think, chrooting is much safer and perhaps more elegant. :evil:

---

### Post by happytuesdays on 2011-02-25
I had tried adding rw=init /bash/bin to the kernel paramters but got the error that the disk wasn't writable.
mount -o remount, rw on a new line fixed that

add

 rw=init /bash/bin 
to the end of the kernel line
and add
mount -o remount, rw 
on a newline 

Thanks  Again

---

