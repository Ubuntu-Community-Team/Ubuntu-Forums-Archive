---
title: "passwords and recovery mode"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by skubachick on 2009-03-02
Hoping someone can help.
I have a Dell Mini 9, with Ubuntu installed,from work. I didn't set it up, a colleague did, and as far as he can remember he was not asked to enter a password. When it boots up I am not asked for a password. However I need to install updates and it asks for a password!
I have searched the forums and tried changing the root password (in the terminal) but it doesn't work - typed in sudo root passwd, tried typing a password but it says that it is not the right password.
I've also read about changing passwords in recovery mode, but can't get to recovery mode - I don't get a GRUB menu (which is what I think I'm looking for) - I've tried pressing ESC when I see the word GRUB but no luck.
I can get into the setup when it boots but that doens't give me an option for recovery mode.

---

### Post by Bölvaður on 2009-03-02
From terminal or alt+F2: type
```
gedit /boot/grub/menu.lst
```

or browse to the menu.lst file and double click.


you can add at the bottom of this file something like

```

title		This is just a temp. test thing to let me see GRUB
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=cc8a4d6d-acb4-4012-955b-d2175046322c ro quiet 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot
```

when booting do not select this new option.. just go straight for the recovery, do your thing and then delete this text by:
```
gksudo gedit /boot/grub/menu.lst
```


note that this may only allow you (perhaps it will not work) to get into recovery. you will have to follow the other guides and type passwd (or what ever it was)...


to make the grub countdown longer add this line somewhere in grub, preferably before the boot options (title....ubuntu....)
(having it at top of the file is actually quite good and will be quick to find again)
```
timeout		10
```

I would assume recovery mode is the second option for you (you can verify it by checking menu.lst and make sure the second title is "recovery mode"). This is the code to add to the top also. It makes grub boot into the second option (note that grub begins to count from 0 so the first boot option is 0 and the second is 1)
```
default		1
```

---

### Post by skubachick on 2009-03-02
Thanks for suggestion - managed to open the menu.1st file. Recovery mode wasn't listed. Tried changing the timeout but it wouldn't let me save the file (assumed I had to do that before booting). Tried changing the default boot to option 1 and again couldn't save the file.
Any other suggestions?

---

### Post by Ben Crisford on 2009-03-02
If you cannot enter recovery mode then something is wrong anyway...

Have you reported this as a bug?  If not then do so, it will save over people this problem if it is an ubuntu fault.  When you post a bug report though remember to make it complete, because I am in the bugsquad, and there is thousands of new reports every day which need triaging, and thats *alot* of work.  If the report is already valid then it saves alot of time.

These are the guidelines given to the bugsquad and bug-management team:

*_**To be considered complete most bug reports must contain:**_*
[I]The version of Ubuntu that the reporter is running
The version of the package the reporter is using
The actions taken to produce the problem
Whether or not it is possible for the reporter to reproduce the bug
The expected result of these actions
The actual result of these actions[/I]

---

### Post by Bölvaður on 2009-03-02
> **skubachick said:**
> Tried changing the timeout but it wouldn't let me save the file (assumed I had to do that before booting).

You are correct. You will need to run it as super user (the guy that can do what ever he wants) like this:
```

gksudo gedit /etc/boot/menu.lst
```

or if you want to browse to it: ```
gksudo nautilus
```

Make sure it is the menu.lst (not .1st as this is a menu "list" not menu "first" :P)

I actually wrote it on my other post but because it was long I wasnt expecting you to notice the difference with the gksudo in front of the command.

Please copy and paste the contents of this file onto here so we may check if something is up.
Im pretty sure this isn't a bug Ben.

---

### Post by egalvan on 2009-03-02
> **Bölvaður said:**
>  You will need to run it as super-user like this:
```

gksudo gedit /etc/boot/menu.lst
```

or if you want to browse to it: ```
gksudo nautilus
```


Problem, he needs the password to run as superuser,
but he does not have the password.

Try these links

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

[http://www.howtogeek.com/howto/linux/reset-your-ubuntu-password-easily-from-the-live-cd/](http://www.howtogeek.com/howto/linux/reset-your-ubuntu-password-easily-from-the-live-cd/)

[http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/](http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/)

---

### Post by Bölvaður on 2009-03-03
He already tried the things in link #1, as pressing ESC didnt work.
And because of that the third option does not work.

The second link is actually quite brilliant: chroot and then reset it is really good thinking :)

---

