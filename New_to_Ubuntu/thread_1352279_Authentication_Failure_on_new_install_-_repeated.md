---
title: "Authentication Failure on new install - repeated"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by creeping_lemur on 2009-12-11
the first time this happened, i believed that i had made some typo in defining my user/password combination, but i installed a second time, and did this part with great care. 
i'm stuck at login with the same result: "Authentication failure."

i'm on a ppc g4 ibook. i've tried using the on screen keyboard, and also switching from
'usa' to 'usa-macintosh' on they keyboard type.

any advice?
thanks...

*edit* for information: using the latest ubuntu 9.10 ppc iso.

---

### Post by LowSky on 2009-12-11
you have a bad disc, I suggest to you redownload it and burn it at the slowest speed you possibly can

---

### Post by joes7 on 2009-12-11
> **LowSky said:**
> you have a bad disc, I suggest to you redownload it and burn it at the slowest speed you possibly can

No, simply log in as "root" (the password is the one you chose). It should work.

---

### Post by creeping_lemur on 2009-12-11
the login prompt doesn't accept either root+mypass or me+mypass.

---

### Post by jacobs444 on 2009-12-11
Press tab when grub loads. 
Select recovery mode. 
when it boots as root at the prompt type: passwd username
then it will ask for the password to be entered twice. 
after typing in, reboot.

---

### Post by jacobs444 on 2009-12-12
obviously replace username with your username in the above, let me know if it doesn't work.

---

### Post by creeping_lemur on 2009-12-12
i'm not sure i have the grub bootloader, is it a default install from ub9.1ppc...?
my install is on a full partition.

during box startup i just get a boot prompt from yaboot,
which repsonds to 'recovery' with:
/ci@f4000000/ata-6@d/disk@0:3, \\recovery: No such file or directory

cd yaboot responds with:
Please wait, loading kernel...
recovery:2,/vmlinux: Unable to open file, Invalid device

no other responses to tab key during boot

---

