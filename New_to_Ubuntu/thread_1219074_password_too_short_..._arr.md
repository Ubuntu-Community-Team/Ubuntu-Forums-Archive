---
title: "password too short ... arr"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by crowhill on 2009-07-21
hi there

i just installed ubuntu 9.04. the first thing i wanted to do is to change the password using

```
passwd
```

however, when i typed in my preferred, short password it said

> password too short

is there a way around this annoying issue? is there a way to TELL MY MACHINE WHAT I (WITH EMPHASIS ON I) WANT TO DO?

some help would be very much appreciated.

thanks a lot in advance,
cheers,

crowhill.

---

### Post by philinux on 2009-07-21
[https://help.ubuntu.com/8.04/serverguide/C/user-management.html](https://help.ubuntu.com/8.04/serverguide/C/user-management.html)
> 
Minimum Password Length

By default, Ubuntu requires a minimum password length of 4 characters, as well as some basic entropy checks. These values are controlled in the file /etc/pam.d/common-password, which is outlined below.

password   required   pam_unix.so nullok obscure min=4 max=8 md5

If you would like to adjust the minimum length to 6 characters, change the appropriate variable to min=6. The modification is outlined below.

password   required   pam_unix.so nullok obscure min=6 max=8 md5

[Note] 	

The max=8 variable does not represent the maximum length of a password. It only means that complexity requirements will not be checked on passwords over 8 characters. You may want to look at the libpam-cracklib package for additional password entropy assistance. 

---

### Post by Revolutionary101 on 2009-07-21
I don't think there is a way around this. I suggest making your password longer and more secure. longer=better

---

### Post by crowhill on 2009-07-21
here is what my /etc/pam.d/common-password file contains (opened it as root):

> #
# /etc/pam.d/common-password - password-related modules common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of modules that define the services to be
# used to change user passwords.  The default is pam_unix.

# Explanation of pam_unix options:
#
# The "sha512" option enables salted SHA512 passwords.  Without this option,
# the default is Unix crypt.  Prior releases used the option "md5".
#
# The "obscure" option replaces the old `OBSCURE_CHECKS_ENAB' option in
# login.defs.
#
# See the pam_unix manpage for other options.

# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

# here are the per-package modules (the "Primary" block)
password        [success=1 default=ignore]      pam_unix.so obscure sha512
# here's the fallback if no module succeeds
password        requisite                       pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
password        required                        pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config

i can't see the option to change the length ...

by the way, my machine is in my room, at home. there are no security issues. therefore, "longer" = "more annoying".

thanks a lot for the help :)

---

### Post by devildoc5 on 2009-07-21
just to pose an idea since you say it is in your room at home.....  Why not just set it up to autologin on boot?  Then the only time you would have to enter your "longer, more annoying, better and more securing" password is when performing administrative tasks.

Even with autologin turned on you can "lock" the computer just like in other OSes to make it "even more secure" if you need to for whatever reason while it is not in use.

Although this will not protect you from bots and other hacking attempts....

---

### Post by jimsheep on 2009-07-21
also, if you're on the interwebs, it's good to have passwords!

---

### Post by crowhill on 2009-07-21
thanks for that :) i'll go with the autologin.

gone are the days where you could do with ubuntu whatever you want. bye bye freedom :)

cheers,
crowhill.

---

### Post by Cypher on 2009-07-21
> **crowhill said:**
> thanks for that :) i'll go with the autologin.

gone are the days where you could do with ubuntu whatever you want. bye bye freedom :)

cheers,
crowhill.

It is sometimes required for Linux to protect one from oneself..:) If things were free reign and bad things happened, people would complain that Linux didn't do enough to protect them..so....;)

---

### Post by jimsheep on 2009-07-21
> **Cypher said:**
> It is sometimes required for Linux to protect one from oneself..:) If things were free reign and bad things happened, people would complain that Linux didn't do enough to protect them..so....;)
+1.  everything is a trade-off.

---

### Post by Grenage on 2009-07-21
The option is there to change the password parameters; that's good enough.

---

### Post by llamabr on 2009-07-21
> **crowhill said:**
> thanks for that :) i'll go with the autologin.

gone are the days where you could do with ubuntu whatever you want. bye bye freedom :)

cheers,
crowhill.

Of course you can still do what you want.  download the source, edit it, compile, and you've got what you want.

It's not a matter if it not doing what you want, since what you want is a secure machine.  All of these applications are infinitely configurable.  This one was just written to do a particular job well.  If you want it to do a different job, write a different one.

---

### Post by sisco311 on 2009-07-21
> **crowhill said:**
> here is what my /etc/pam.d/common-password file contains (opened it as root):



i can't see the option to change the length ...

by the way, my machine is in my room, at home. there are no security issues. therefore, "longer" = "more annoying".

thanks a lot for the help :)

> [noparse]
...
# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

# here are the per-package modules (the "Primary" block)[/noparse]
# [B]password [success=1 default=ignore] pam_unix.so obscure sha512
[COLOR="Red"]password        [success=1 default=ignore]      pam_unix.so min=6 sha512[/COLOR][/B]

...


but if you have admin rights, then, as root, you can set a short password:
```
sudo passwd username
```

---

### Post by Sef on 2009-07-21
>  by the way, my machine is in my room, at home. there are no security issues. therefore, "longer" = "more annoying".

Hacking is a security issue.   There are GNU/Linux botnets.

---

### Post by raymondh on 2009-07-21
> **crowhill said:**
> thanks for that :) i'll go with the autologin.
.

And when you set up auto-login, you *may* have to deal with the keyring ... just in case you're using wireless to connect to the internet.

---

### Post by apjjr on 2009-11-18
> **crowhill said:**
> here is what my /etc/pam.d/common-password file contains (opened it as root):
...
password [success=1 default=ignore] pam_unix.so obscure sha512
...
i can't see the option to change the length ...

by the way, my machine is in my room, at home. there are no security issues. therefore, "longer" = "more annoying".

thanks a lot for the help :)

If you want to bork the security on your system so you can enter shorter, less secure passwords, change that line.
FROM: password [success=1 default=ignore] pam_unix.so obscure sha512
TO: password [success=1 default=ignore] pam_unix.so min=4 sha512
Viola!  No more pesky long complicated passwords.
Do like they said, make a backup copy of common-password first and keep a root login going.  But you could always boot the recovery mode, too.
You can now enter passwords like 1234, abcd, aaaa, 9999, ...
As simple as you like.  Read the man page for pam_unix.
Good luck,
Alex

---

### Post by rubo77 on 2012-05-10
> **apjjr said:**
> If you want to bork the security on your system so you can enter shorter, less secure passwords, change that line.
FROM: password [success=1 default=ignore] pam_unix.so obscure sha512
TO: password [success=1 default=ignore] pam_unix.so min=4 sha512
Viola!  No more pesky long complicated passwords.
Do like they said, make a backup copy of common-password first and keep a root login going.  But you could always boot the recovery mode, too.
You can now enter passwords like 1234, abcd, aaaa, 9999, ...
As simple as you like.  Read the man page for pam_unix.
Good luck,
Alex

this seems to have changed: it is now minlen=4 instead of min=4 

in Ubuntu 11.10 it is like this:
If you want to bork the security on your system so you can enter shorter, **less secure passwords**,
open as root:
```
/etc/pam.d/common-password
```

change the line From
```
password        [success=1 default=ignore]      pam_unix.so obscure sha512
```
to
```
password        [success=1 default=ignore]      pam_unix.so minlen=4 sha512
```

on the other Hand,
if you want to have **more secure paswords**, you should keep the *obscure* option and change the line to
```
password        [success=1 default=ignore]      pam_unix.so minlen=10 sha512 obscure
```

---

### Post by rubo77 on 2012-05-10
> **sisco311 said:**
> as root, you can set a short password:
```
sudo passwd username
```
so it is still possible as root to give out insecure short passwords.

if you want to make it more secure, 
> **baranovich said:**
> use pam_cracklib.so
you need to install libpam-cracklib and its dependencies....

as root:
```
apt-get install libpam-cracklib
```

change the **one line** in **/etc/pam.d/common-password** From:
```
password        [success=1 default=ignore]      pam_unix.so obscure sha512
```
into these **two lines:**
```
password        required        pam_cracklib.so difok=1 minlen=12 dcredit=-1 ucredit=-1 ocredit=-1 lcredit=0 
password        [success=1 default=ignore]      pam_unix.so use_authtok sha512 
```

add these comments if you wish:
```
# pam_cracklib.so's minlen option isn't entirely straightforward.  The option does let you set a minimum length but it
# also allows you to make a trade off between complexity and length
# You can set the dcredit, ucredit, ocredit, lcredit (digit, uppercase, other, lowercase; respectively) parameters to positive 
# values (>=0) to give a character of that class a "credit" towards the value of minlen. For instance setting dcredit=2 would 
# mean that digits count as +2 towards the value of minlen, meaning that a password containing 6 digits would be accepted even 
# if minlen=12.
# setting the same parameters to negative values (as shown above) indicates the minimum number of characters of that class that
# must be present in the password (i.e. above 1 digit, 1 uppercase letter, and 1 other character are required) and each character
# still counts as +1 towards the minlen value.
```


> **baranovich said:**
> 
[LIST]
[*]**NOTE:** The root user is _***NOT***_ subjected to the password length and complexity rules that normal system users are. Both ```
sudo adduser bob
``` and ```
sudo passwd bob
``` will complain if the entered password does not meet the length and complexity requirements, but will happily let an admin user set whatever password they wish. I personally disagree with this approach but the general consensus seems to be that since an root/admin user can arbitrarily change the PAM rules there is no reason to enforce them for such users.
[/LIST]

so all this just adds a warning even to the root user, that the password is too short/not complex enough...

does someone know, how to disallow this to even root?

---

### Post by oldos2er on 2012-05-10
I've closed this three year old thread. If you have a question or problem, please start a new thread.

---

