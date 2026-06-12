---
title: "su: Authentication Failure"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by Recon20k on 2010-05-10
Im trying to install mathematica on my pc and am having trouble using the ./file.sh command


Anyway,

when i type su in the terminal, i enter my password and it says "su: Authentication Failure"

Any idea what the problem is??

I've installed ubuntu quite recently and im the only user.

---

### Post by Sealbhach on 2010-05-10
Try

```
sudo su
```

.

---

### Post by sisco311 on 2010-05-10
> **Recon20k said:**
> Im trying to install mathematica on my pc and am having trouble using the ./file.sh command


Anyway,

when i type su in the terminal, i enter my password and it says "su: Authentication Failure"

Any idea what the problem is??

I've installed ubuntu quite recently and im the only user.

By default, the root account password is locked. Use sudo to run applications as root:
```
sudo ./file.sh
```

[uhelp]community/RootSudo[/uhelp]

---

### Post by Major Newb on 2010-07-22
I ran into the same problem. The problem is that the "su" alias for "sudo" seems to have been changed. Instead of using "su", I have to type out "sudo", and it behaves normally...

---

### Post by RiceMonster on 2010-07-22
> **Major Newb said:**
> I ran into the same problem. The problem is that the "su" alias for "sudo" seems to have been changed. Instead of using "su", I have to type out "sudo", and it behaves normally...

su is not an alias for sudo. su means "substitute user", which is how you switch to another account on the command line. The root account is just the default option. sudo, on the other hand, allows you to run a command with root access. The root account is locked on Ubuntu, and instead it is configured to use sudo.

If you want to get a root shell, type "sudo -i", or you can just run a specific command with sudo. I would not reccomend running "sudo su".

---

### Post by Gerard08 on 2011-04-04
I just came across the same error message. Rice Monster's suggestion " sudo -i" changed the directory to "root@". I then cd'd to the program directory and ran the requested string, which was su -c "make install"

The files appear to be properly installed.

Ger

---

### Post by sisco311 on 2011-04-04
> **Gerard08 said:**
> I just came across the same error message. Rice Monster's suggestion " sudo -i" changed the directory to "root@". I then cd'd to the program directory and ran the requested string, which was su -c "make install"

The files appear to be properly installed.

Ger

Check out the community documentation:
[uhelp]community/RootSudo[/uhelp]

You don't have to start a root shell, you could simply run:
```
sudo make install
```

Or even better, instead of *make install* you could use checkinstall:
```
sudo checkinstall
```

See:
[uhelp]community/CheckInstall[/uhelp]

---

