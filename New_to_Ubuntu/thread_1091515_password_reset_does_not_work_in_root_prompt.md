---
title: "password reset does not work in root prompt"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by Offworlder on 2009-03-09
Rev 8.10
I do not get past the following: 

foo@bar:~# passwd <username>

I get the following:

bash: syntax error near unexpected token 'newline'
root@user-laptop:~#


-------------------------------------------
I understand this would be the next string:
-------------------------------------------
Follow the prompts to set a new password. Finally, reboot the computer with the following command:

foo@bar:~# reboot


Many thanks, just born

---

### Post by Nxion on 2009-03-09
Who's password are you trying to change? IS it roots or yours?

---

### Post by LowSky on 2009-03-09
> **Offworlder said:**
> Rev 8.10
I do not get past the following: 

foo@bar:~# passwd <username>

I get the following:

bash: syntax error near unexpected token 'newline'
root@user-laptop:~#



you need to be root to change a password of another user
for commands

 
 your own
**passwd   **Change your own password.

need root
**passwd sleepy **  Change sleepy's password.

**passwd -d sleepy **  Delete sleepy's password.

---

### Post by Offworlder on 2009-03-09
Hi -

Changing mine.  Initially when I installed, I only had a pw with no user name but then added my user name.  I did not forget either however, they will not work (know it's case sensitive)

Thanks

---

### Post by t0p on 2009-03-09
> **Offworlder said:**
> 
Changing mine.  Initially when I installed, I only had a pw with no user name but then added my user name.  I did not forget either however, they will not work (know it's case sensitive)


I'm a little confused.  If your username/password don't work, how are you logging in to get to the command line?

I also don't understand what you mean when you say you started off without a username but added it later?

---

### Post by Offworlder on 2009-03-09
I got in by hitting the esc key at boot which allowed me to get to I guess what would be safe mode on a pc.  From there there was a list of of options however, I may have solved it by booting with the install disc which brought me to the desktop, perhaps from there I can disable whatever I did with the user name & pw

Actually I had it backwards, when I installed the first time it asked for a pw, for example: admin however, I skipped adding a user name which I added later this is when I had the problem at reboot

Tks

---

