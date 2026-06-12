---
title: "Unable to modify password length in common-password"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by ganjabob on 2009-12-02
The ubuntu 9.04 user guide says the min password length is 4 characters by default but when I got to add a user with a 5 character password the User Admin tool tells me the password is too short and must be 6 characters in length. 

I sudo'd and made the recommended modifications to /etc/pam.d/common-password adding the following line:

[FONT=Courier New][COLOR=Blue]password   required   pam_unix.so nullok obscure min=4 max=8 md5[/COLOR][/FONT]

Confirmed it saved and then rebooted the machine and still was unable to set a 5 character password for a new user. In the common-password file I did not see an entry setting the min to 6 as expected. 

Please do not respond with 'use a longer password'. My children log onto this machine and it only serves movies, and I'd like to restrict which movie folders they have access to. Thank you.

---

### Post by sisco311 on 2009-12-02
> **ganjabob said:**
> The ubuntu 9.04 user guide says the min password length is 4 characters by default but when I got to add a user with a 5 character password the User Admin tool tells me the password is too short and must be 6 characters in length. 

I sudo'd and made the recommended modifications to /etc/pam.d/common-password adding the following line:

[FONT=Courier New][COLOR=Blue]password   required   pam_unix.so nullok obscure min=4 max=8 md5[/COLOR][/FONT]

Confirmed it saved and then rebooted the machine and still was unable to set a 5 character password for a new user. In the common-password file I did not see an entry setting the min to 6 as expected. 

Please do not respond with 'use a longer password'. My children log onto this machine and it only serves movies, and I'd like to restrict which movie folders they have access to. Thank you.

Hi and welcome to the forums!

You don't have to add a new line, you must edit an existing one:
```
password        [success=1 default=ignore]      pam_unix.so obscure sha512
```

to:
```
password        [success=1 default=ignore]      pam_unix.so obscure min=4 sha512
```

The **obscure** option enables extra checks on password strength. You may have to remove it since most short passwords aren't strong enough.

But as root you can set a non-secure (short) password for a user without editing common-password:
```
sudo passwd username
```

Once your children figure out how to change they own password they will be forced to set a strong one. ;)

IMO, if they know how to change the password they are old enough to use a secure one. :evil:

---

### Post by erd02 on 2009-12-30
> **sisco311 said:**
> Hi and welcome to the forums!

You don't have to add a new line, you must edit an existing one:
```
password        [success=1 default=ignore]      pam_unix.so obscure sha512
```to:
```
password        [success=1 default=ignore]      pam_unix.so obscure min=4 sha512
```The **obscure** option enables extra checks on password strength. You may have to remove it since most short passwords are not strength enough.

But as root you can set a non-secure (short) password for a user without editing common-password:
```
sudo passwd username
```Once your children figure out how to change they own password they will be forced to set a strength one. ;)

IMO, if they know how to change the password they are old enough to use a secure one. :evil:


Hello,
I tried to do change the existing line to edit the minimum password requirement but it still doesn't work. This is what I did

password        [success=1 default=ignore]      pam_unix.so obscure min=4 sha512

I saved it and confirmed that the changes were made and restarted my computer. Still doesn't work. Still says that my password is too short. I been at this for a while now and I was wondering if there is another way I can change the password policies?

---

### Post by stevebu56 on 2010-01-11
erd02, where you ever able to modify the minimum password field.  I'm doing the same with a Jaunty installation and I'm not having any luck.  Is this a known bug by chance?  

Steve

---

### Post by Aerospaztic on 2010-08-16
FYI... I also tried to add a minimum value to the common-auth file.  That doesn't work either.

---

### Post by lee321987 on 2010-09-15
I just wanted to say that I did what sisco311 suggested and was able to use a short simple password.
What I did:

 ```
sudo gedit /etc/pam.d/common-password
```changed line:
```
password        [success=1 default=ignore]      pam_unix.so obscure sha512
```to
```
password        [success=1 default=ignore]      pam_unix.so min=4 sha512
```save and close gedit
```
passwd
```Then was able to set a new short password.

At first I left "obscure" in, but it said my password was too simple (or basic or something like that).

---

### Post by bindatype on 2010-10-03
I am trying to increase the password length to a minimum of 10 characters but I am not successful. I can decrease the number of characters as described in this thread but increasing seems not as straightforward. Any ideas?

---

### Post by McGrude on 2010-12-10
I'm having the same problem.   

in common-password it lists : 

password        [success=1 default=ignore]      pam_unix.so obscure sha512

if I change it to : 

password        [success=1 default=ignore]      pam_unix.so obscure sha512 min=12

I can still set an 8 character password (as a user).

Do I have to do something after editing common-password ???

---

### Post by andrej aka zag rulezzz on 2011-02-13
After editing common-password, type passwd in console mode. It doesn't work with GUI.

---

### Post by baranovich on 2011-06-06
I have spent several hours banging my head against the wall after encountering the problems described in this thread. Fortunately I've figured out a solution along with several other useful pieces of information along the way.  Here is what I figured out, hopefully it will spare someone some pain in the future:

Here is the (working!!!) contents of my /etc/pam.d/common-password file:
```

*# here are the per-package modules (the "Primary" block) *
[B]password        required        pam_cracklib.so difok=1 minlen=12 dcredit=-1 ucredit=-1 ocredit=-1 lcredit=0 
password        [success=1 default=ignore]      pam_unix.so use_authtok sha512 [/B]
*# here's the fallback if no module succeeds *
**password        requisite                       pam_deny.so **
[I]# prime the stack with a positive return value if there isn't one already; 
# this avoids us returning an error just because nothing sets a success code 
# since the modules above will each just jump around [/I]
**password        required                        pam_permit.so **
*# and here are more per-package modules (the "Additional" block) *
**password       optional        pam_gnome_keyring.so  **
*# end of pam-auth-update config *

```
[LIST]
[*]I attempted to use the pam_unix.so "min" option but could not get it to work at all. I set it to min=12 and was still able to set 8 character passwords. This seems like a rather serious bug or, at the very least, a major documentation problem.
[*]In order to use pam_cracklib.so you need to install libpam-cracklib and its dependencies.
[*]pam_cracklib.so's minlen option isn't entirely straightforward.  The option does let you set a minimum length but it also allows you to make a trade off between complexity and length, something that could be useful but it also confusing at first glanced.
[LIST]
[*]You can set the dcredit, ucredit, ocredit, lcredit (digit, uppercase, other, lowercase; respectively) parameters to positive values (>=0) to give a character of that class a "credit"  towards the value of minlen.  For instance setting dcredit=2 would mean that digits count as +2 towards the value of minlen, meaning that a password containing 6 digits would be accepted even if minlen=12.
[*]Fortunately setting the same parameters to negative values (as shown above) indicates the minimum number of characters of that class that must be present in the password (i.e. above 1 digit, 1 uppercase letter, and 1 other character are required) and each character still counts as +1 towards the minlen value.
[/LIST]
 
[*]You must add "use_authtok" to the existing pam_unix.so line in order to tell pam_unix.so to use the password information from the previous entry in the "password stack" instead of requesting that the user type in a new password.
[*]**NOTE:** The root user is _***NOT***_ subjected to the password length and complexity rules that normal system users are. Both ```
sudo adduser bob
``` and ```
sudo passwd bob
``` will complain if the entered password does not meet the length and complexity requirements, but will happily let an admin user set whatever password they wish. I personally disagree with this approach but the general consensus seems to be that since an root/admin user can arbitrarily change the PAM rules there is no reason to enforce them for such users.
[/LIST]

---

### Post by frank.bommeli on 2011-11-10
Thank you sisco311

I used your root tip, it worked fine for me

```
sudo passwd username
```:D

---

### Post by rubo77 on 2012-05-10
> **baranovich said:**
> ...
use pam_cracklib.so 
..
install libpam-cracklib and its dependencies.
...
**NOTE:** The root user is _***NOT***_ subjected to the password length and complexity rules that normal system users are.

is there a way to make the root user obey the rules too?

---

### Post by oldos2er on 2012-05-10
Closed. Please don't bump old threads.

---

