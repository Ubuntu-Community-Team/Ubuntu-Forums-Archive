---
title: "how do you get root privileges in ubuntu 7.04"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by Yash Pal on 2010-01-18
I am unable to work as root or equivalent in Ubuntu 7.04. su or sudo has no effect on the system.
It just says something like you have to be root after I type my password during setup.
I have added a 2nd user and I cannot switch to the other user in the terminal. 

Even in GUI, the password set up originally does not give me any power to modify.


I give below failure with su, unfortunately, I did not copy the computer's reply with 'sudo' and 'sudo su'. 

Could anyone tell me what mistake I am making?

                                                [SIZE=1][COLOR=Blue][FONT=Bitstream Vera Sans, sans-serif]yashpal@yashpal-desktop:~$ su[/FONT][/COLOR][/SIZE]
 [SIZE=1][COLOR=Blue]
[/COLOR][/SIZE] 
 [SIZE=1][COLOR=Blue][FONT=Bitstream Vera Sans, sans-serif]Password: ([/FONT][/COLOR][/SIZE][SIZE=1][COLOR=Blue][FONT=Courier 10 Pitch]typed – password of 2[/FONT][/COLOR][/SIZE][SIZE=1][COLOR=Blue][FONT=Courier 10 Pitch]nd[/FONT][/COLOR][/SIZE][SIZE=1][COLOR=Blue][FONT=Courier 10 Pitch] user[/FONT][/COLOR][/SIZE][SIZE=1][COLOR=Blue][FONT=Bitstream Vera Sans, sans-serif])[/FONT][/COLOR][/SIZE]
 [SIZE=1][COLOR=Blue][FONT=Bitstream Vera Sans, sans-serif]su: Authentication failure[/FONT][/COLOR][/SIZE]
 [SIZE=1][COLOR=Blue]
[/COLOR][/SIZE] 
 [SIZE=1][COLOR=Blue][FONT=Bitstream Vera Sans, sans-serif]Sorry.[/FONT][/COLOR][/SIZE]
 [SIZE=1][COLOR=Blue]
[/COLOR][/SIZE] 
 [SIZE=1][COLOR=Blue][FONT=Bitstream Vera Sans, sans-serif]yashpal@yashpal-desktop:~$ su[/FONT][/COLOR][/SIZE]
 [SIZE=1][COLOR=Blue]
[/COLOR][/SIZE] 
 [SIZE=1][COLOR=Blue][FONT=Bitstream Vera Sans, sans-serif]Password: [/FONT][/COLOR][/SIZE][SIZE=1][COLOR=Blue]([/COLOR][/SIZE][SIZE=1][COLOR=Blue][FONT=Courier 10 Pitch]typed[/FONT][/COLOR][/SIZE][SIZE=1][COLOR=Blue][FONT=Bitstream Vera Sans, sans-serif]-[/FONT][/COLOR][/SIZE][SIZE=1][COLOR=Blue][FONT=Courier 10 Pitch]password of 2[/FONT][/COLOR][/SIZE][SIZE=1][COLOR=Blue][FONT=Courier 10 Pitch]nd[/FONT][/COLOR][/SIZE][SIZE=1][COLOR=Blue][FONT=Courier 10 Pitch] user[/FONT][/COLOR][/SIZE][SIZE=1][COLOR=Blue][FONT=Bitstream Vera Sans, sans-serif])[/FONT][/COLOR][/SIZE]
 [SIZE=1][COLOR=Blue][FONT=Bitstream Vera Sans, sans-serif]su: Authentication failure[/FONT][/COLOR][/SIZE]
 [SIZE=2][COLOR=Blue]
[/COLOR][/SIZE] 
 [SIZE=1][COLOR=Blue][FONT=Bitstream Vera Sans, sans-serif]Sorry.[/FONT][/COLOR][/SIZE]
 [SIZE=1][COLOR=Blue]
[/COLOR][/SIZE] 
 [SIZE=2][COLOR=Blue][FONT=Bitstream Vera Sans, sans-serif][SIZE=1]yashpal@yashpal-desktop:~$[/SIZE] [/FONT][/COLOR][/SIZE] 
 [SIZE=2][COLOR=Blue]
[/COLOR][/SIZE] 
 I am posting this question after checking the forums if a similar question has been posted.

---

### Post by MelDJ on 2010-01-18
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)
sorry mate..

---

### Post by wojox on 2010-01-18
Be careful: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by anaconda on 2010-01-18
su works like this:

```
sudo su
```

to get a root terminal. And the password is your sudo password.. eg. your password.

you could alse enable the 
System/System tools/root terminal
sfrom the startup menu.
right-click on the menu and select edit menus...

---

### Post by oldos2er on 2010-01-18
Ubuntu disables the root account by default, it uses 'sudo' to temporarily elevate your user privileges to root/admin, so 'sudo' + your user's password should work for you as long as your user is in the /etc/sudoers file. Use 'sudo -i' if you need to run two or more admin commands.

Incidentally, 7.04 is no longer supported. You might want to install 8.04 or newer.

---

### Post by Yash Pal on 2010-01-21
Thanks for all the help; I *will *try out everyone of the suggestions. My processor is a P3 and nothing higher than 7.04 is supported. Thanks once again to everyone.

---

### Post by Soul-Sing on 2010-01-21
7.04 isn't supported anymore by updates/security updates
(that is the desktop environment)
- for security reasons upgrade your system, or install a newer/the newest version of ubuntu. because otherwise the discussion bout security (su/sudo) is rather academic.
> 
My processor is a P3 and nothing higher than 7.04 is supported.

Do you have the "alternative" ubuntu repositories enabled, so you get your updates?

---

### Post by snowpine on 2010-01-21
> **Yash Pal said:**
> Thanks for all the help; I *will *try out everyone of the suggestions. My processor is a P3 and nothing higher than 7.04 is supported. Thanks once again to everyone.

If by "P3" you mean "Pentium 3" then all versions of Ubuntu will support it (including the current 9.10).

7.04 is no longer receiving any bug fixes or security patches.

---

