---
title: "Cannot log in"
date: 2011-04-18
forum: New to Ubuntu
---

### Post by saffer05 on 2011-04-18
I'm running the latest version of Kubuntu and yesterday I installed Root (by accident, I was trying to access control of my fan speeds as root) and I installed Wine. These two actions seemed to have little to no effect, as I didn't try to run anything using Wine and I didn't know what the program called Root was so I just left it. 

Now today I can't log in. I switch my PC on and I get some log in screen that recognises my main account name, titled Terry, and it has the - MS - 2345 or whatever the numbers are above the two text boxes where it's asking for a username and password. If I try using my normal username of Terry (tried lowercase as well) and my normal password it doesn't do anything. Tells me it's wrong. I tried signing in with the console and that didn't work either. Wondering if anyone can shed some light onto what has brought up this log in screen (I presume that Root thing I installed yesterday...?), how I can get rid of it and most of all, how do I get my PC back?

Any help would be greatly appreciated.

---

### Post by spikoley on 2011-04-23
This is worth a shot.  Go into recovery mode.  When the Grub screen shows up at the start of the boot process select Recovery Mode.  Once you are in update the password for your account.

```
passwd <username>
```

Then reboot and log in normally.

```
reboot
```

---

### Post by varunendra on 2011-04-23
> **spikoley said:**
> This is worth a shot.  Go into recovery mode.  When the Grub screen shows up at the start of the boot process select Recovery Mode.  Once you are in update the password for your account.

```
passwd <username>
```Then reboot and log in normally.

```
reboot
```

+1,
just a bit elaboration - if the advanced grub menu doesn't appear by default (the menu with list of installed operating systems to choose from), just press and hold "shift" key while booting to bring it up. Choose "recovery mode" there. You'll need to select "**root - Drop to root shell prompt**" option in recovery console, where you can use the above trick to reset the password for any user, for example,
```
passwd terry
```

then enter / re-enter the new password on the prompt. You may already know that the password characters won't appear while typing. Just type them correctly and enter :).

If you want to confirm the username and its case, this command will show you all the available usernames in their exact letters/case:
```
ls /home
```

---

