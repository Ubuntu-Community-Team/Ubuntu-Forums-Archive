---
title: "dont know my username or password"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by DHKA on 2010-04-15
Hi 
I have installed Ubuntu 8.10 onto my mac using parallels, it all starts up ok thn asks me my username.
I dont know my username or password and therefore cannot move on.

I have checked the forums and started ubuntu in recovery mode and then used arrows to drop to root shell prompt.
I press return and get the following

Give root password for maintenance
or type Control-D to continue) :

if i press ctrl D on my mac it goes back to the options to Drop to root shell prompt

If i try to enter anything my keyboard does not allow me to enter anything although the return button works and i get this again

Give root password for maintenance
or type Control-D to continue) :

I hope you can help

thanks

---

### Post by undecim on 2010-04-15
Assuming this is the first time you are trying to start Ubuntu, it would probably be easiest to just reinstall Ubuntu and make sure you remember your username/password this time.

---

### Post by mikewhatever on 2010-04-15
You were supposed to type a username and password during the installation. Try writing that info down on a piece of paper to have a reference.

---

### Post by snowpine on 2010-04-15
Good tutorial here: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Also keep in mind that support for 8.10 will be ending in 2 weeks. You might be better off installing the current Ubuntu release (9.10, with 10.04 coming out soon).

Good luck! :)

---

### Post by sisco311 on 2010-04-15
Hi and welcome to the forums.

Highlight the recovery mode & press e for edit,

highlight the kernel line & press e again,

remove the **ro single** boot options & type **rw init=/bin/bash**,

press Enter, then b to boot.


Reset your password, then press Ctrl+Alt+Del to reboot.

---

### Post by cguy on 2010-04-15
> **DHKA said:**
> Hi 
I have installed Ubuntu 8.10 onto my mac using parallels, it all starts up ok thn asks me my username.
I dont know my username or password and therefore cannot move on.

I have checked the forums and started ubuntu in recovery mode and then used arrows to drop to root shell prompt.
I press return and get the following

Give root password for maintenance
or type Control-D to continue) :

if i press ctrl D on my mac it goes back to the options to Drop to root shell prompt
[B]
If i try to enter anything my keyboard does not allow me to enter anything although the return button works and i get this again[/B]

Give root password for maintenance
or type Control-D to continue) :

I hope you can help

thanks
When typing passwords in the terminal you won't get any visual feedback. (NO stars,etc)

---

### Post by DHKA on 2010-04-15
thank you for the instructions.
everything worked ok apart from I dont know my user name.
I have previously installed  ubuntu and cannot ever remember setting a user name.
i did try leaving a blank after the "passwd" which was accepted then i set a new password, it looked like all was going well but after i did ctrl alt del it seemed to let me go past the username as blank but not accept the new password.
Almost there , !!!

---

### Post by DHKA on 2010-04-15
thank you for the instructions.
everything worked ok apart from I dont know my user name.
I have previously installed ubuntu and cannot ever remember setting a user name.
i did try leaving a blank after the "passwd" which was accepted then i set a new password, it looked like all was going well but after i did ctrl alt del it seemed to let me go past the username as blank but not accept the new password.
Almost there , !!!

---

### Post by sisco311 on 2010-04-15
> **DHKA said:**
> thank you for the instructions.
everything worked ok apart from I dont know my user name.
I have previously installed  ubuntu and cannot ever remember setting a user name.
i did try leaving a blank after the "passwd" which was accepted then i set a new password, it looked like all was going well but after i did ctrl alt del it seemed to let me go past the username as blank but not accept the new password.
Almost there , !!!

Run:
```
ls /home
```to list the home directories. Usually, the name of the home directory is the same as the username. 

Or try something like:
```
awk -F: '$3>999{print $1}' /etc/passwd
```

In the recovery shell, you are logged in as root, so 
```
passwd
```resets the root password. Once it's reseted you should be able to boot in recovery mode & use the new root password to log in.  

If you have an account with full sudo privileges, you can lock the root account password. By locking it, you will be able to boot in recovery mode without being prompted for a password.

See:
[uhelp]community/RootSudo[/uhelp]

---

### Post by snowpine on 2010-04-15
> **DHKA said:**
> thank you for the instructions.
everything worked ok apart from I dont know my user name.
I have previously installed  ubuntu and cannot ever remember setting a user name.
i did try leaving a blank after the "passwd" which was accepted then i set a new password, it looked like all was going well but after i did ctrl alt del it seemed to let me go past the username as blank but not accept the new password.
Almost there , !!!

Did you read the tutorial I linked to in post #4?

> Once you're at the root shell prompt, if you have forgotten your username as well, type
ls /home
That's a lowercase L, by the way, not a capital i, in ls. You should then see a list of the users on your Ubuntu installation. 

---

