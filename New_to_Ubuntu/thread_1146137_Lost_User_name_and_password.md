---
title: "Lost User name and password"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by Torn Welly on 2009-05-02
I have forgotten my user name and password for logging in to Ubuntu. How do I proceed to rectify this??

---

### Post by drs305 on 2009-05-02
If you can't get into ubuntu at all, reboot and enter the recovery mode. If you don't see the grub menu during boot, press ESC during the boot sequence and it should appear as one of the options.

Select the "Drop to root shell" option. At the prompt, type:
```
ls /home
```
That will show you the home's listed on the machine. Hopefully you will recognize your home's name and password.

If you still don't remember your password, again at the prompt, using a name from the /home list:
```
 passwd -a *username*
```
You will be prompted to enter a new password.
Once you have done this, reboot.

---

### Post by taurus on 2009-05-02
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

