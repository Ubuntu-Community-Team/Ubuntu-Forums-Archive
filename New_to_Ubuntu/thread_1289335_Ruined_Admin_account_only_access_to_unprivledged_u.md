---
title: "Ruined Admin account only access to unprivledged user"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by xaxtree on 2009-10-12
Ok so I might have messed up a little bit...  Or a lot.
What I've been trying to do is change me login name, not on the login screen but under edit users and groups, I wanted to change the middle login name.  I'm running Ubuntu 8.10 also.  What I was copied my /etc/passwd file and made it /etc/passwd.old,  I edited /etc/passwd to change my login name, and as I was about to do the next steps, I was able to use sudo or anything. I don't know the password now, it is not my original sudo password, does anyone have any idea how I can run sudo or anything from an unprivileged user to delete or change /etc/passwd or remove it and change /etc/passwd.old to /etc/passwd?  My apologise if I'm not making anything sense, just a bit frustrated because I did something dumb.

---

### Post by sandyd on 2009-10-12
bootfrom livecd, mount the partition and rename it back to normal from there.

---

### Post by nothingspecial on 2009-10-12
> **xaxtree said:**
> Ok so I might have messed up a little bit...  Or a lot.
What I've been trying to do is change me login name, not on the login screen but under edit users and groups, I wanted to change the middle login name.  I'm running Ubuntu 8.10 also.  What I was copied my /etc/passwd file and made it /etc/passwd.old,  I edited /etc/passwd to change my login name, and as I was about to do the next steps, I was able to use sudo or anything. I don't know the password now, it is not my original sudo password, does anyone have any idea how I can run sudo or anything from an unprivileged user to delete or change /etc/passwd or remove it and change /etc/passwd.old to /etc/passwd?  My apologise if I'm not making anything sense, just a bit frustrated because I did something dumb.

Boot into recovery mode (root shell)

```
mv /etc/passwd /etc/passwd_oops
```

```
mv /etc/passwd.old /etc/passwd
```

---

### Post by xaxtree on 2009-10-12
> **nothingspecial said:**
> Boot into recovery mode (root shell)

```
mv /etc/passwd /etc/passwd_oops
```

```
mv /etc/passwd.old /etc/passwd
```

I don't know the root password, I don't think I ever activated root

---

### Post by Peter09 on 2009-10-12
recovery command line is root ant way - no password needed

---

### Post by sisco311 on 2009-10-12
> **xaxtree said:**
> I don't know the root password, I don't think I ever activated root

The sulogin program in Ubuntu is patched to handle the default case of a locked root password. You can boot in Recovery Mode without being asked for a password.

---

### Post by xaxtree on 2009-10-12
> **sisco311 said:**
> The sulogin program in Ubuntu is patched to handle the default case of a locked root password. You can boot in Recovery Mode without being asked for a password.

When I reboot, go into recovery, it has the option to prompt root shell, then asks for password.

---

### Post by blur xc on 2009-10-12
According to everythign I've read, you should not manually edit those files in a text editor for this very reason.  Use the user account commands, useradd, usermod, userdel, etc...  That way you won't break your system in the future-

Except be careful using usermod -G.  If you are using usermod to add yourself to a new group, you will need to use usermod -aG (a for append), otherwise, you will remove yourself from all other groups you belong to (including admin) and only belong to the one you were trying to add yourself to.  I heard somehwere you can user useradd or adduser (dunno) to add yourself to a group also, and I think it's safer, just haven't done it.

BM

---

### Post by sisco311 on 2009-10-12
> **xaxtree said:**
> When I reboot, go into recovery, it has the option to prompt root shell, then asks for password.

reboot

highlight the recovery mode line,

hit e for edit, highlight the line that begins kernel, 

hit e for edit, delete the ro single (splash quiet) options from the end of the line

type rw init=/bin/bash, hit Enter

and hit b to boot in a root shell.

restore the passwd file and press Ctrl+Alt+Del to reboot

---

### Post by xaxtree on 2009-10-12
> **sisco311 said:**
> reboot

highlight the recovery mode line,

hit e for edit, highlight the line that begins kernel, 

hit e for edit, delete the ro single (splash quiet) options from the end of the line

type rw init=/bin/bash, hit Enter

and hit b to boot in a root shell.

restore the passwd file and press Ctrl+Alt+Del to reboot

I tried that with 

```
mv /etc/passwd /etc/passwd_oops
mv /etc/passwd.old /etc/passwd
```

and it gave me back an error and when I un-did all that, there was no root name but is there any other way to change or edit the files in that root shell?


EDIT: SOLVED

I went into root, opened nano, edited and saved the files, thanks for all the help everyone :)

---

