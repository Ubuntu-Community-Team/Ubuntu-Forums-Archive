---
title: "Changing Logon Admin password?"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by R@inm@n on 2009-07-05
How do I change my admin and log on password?

Thanks,

R.

---

### Post by Anxious Nut on 2009-07-05
you dont need to change your root(admin) password, cuz you can always use sudo instead

---

### Post by R@inm@n on 2009-07-05
Hmmm, sorry, bad phraseology from me.

How do I change my log in password please?  
When I first boot into Ubuntu there is a name and log in screen.  I wish to change that log in password.

Thanks 


R.

---

### Post by techstop on 2009-07-05
The first place I would look is Administration>Users and Groups.

Or run this in a terminal for further information;

```
man passwd
```

---

### Post by SunnyRabbiera on 2009-07-05
You change the admin password by changing your own in Ubuntu...

---

### Post by mhgsys on 2009-07-05
.If you already have the correct password
```

sudo passwd username

```

will do.


to recover or change password without having to use the old one, in case you forgot it...
bootup in recovery modes/

then
```


 cd /home/

```

```


ls -a

```
You'll find your username there.
then

```


passwd username

```
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully

reboot, log in with your username and passwd.

---

### Post by R@inm@n on 2009-07-05
Thank you, that worked fine.


R.

---

