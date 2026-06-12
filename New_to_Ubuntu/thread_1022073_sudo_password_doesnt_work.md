---
title: "sudo password doesnt work"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by libihero on 2008-12-26
For some reason my sudo password doesn't work. The password it asks me for every other administrative task works. For example when I type gksudo nautulus and it the window comes up for a password, my password works. Is there a different password that I need?

---

### Post by candtalan on 2008-12-26
If you have only the one (usual) account, then the password will be the same, and only, one.

Are you being told that the password is actually incorrect, or is it just ignoring you?

---

### Post by sayems on 2008-12-26
If you forgot you password for your ubuntu system you can recover using the following steps

Turn your computer on.

Press ESC at the grub prompt.

Press e for edit.

Highlight the line that begins kernel ………, press e

Go to the very end of the line, **add rw init=/bin/bash**

press enter, then press b to boot your system.

Your system will boot up to a passwordless root shell.

Type in passwd username

Set your password.

Type in reboot

---

### Post by enoughsaid05 on 2008-12-26
do you mean that you can't use sudo in the terminal or is it that you simply want to log in as root?

---

### Post by taurus on 2008-12-26
Or maybe when you type in your password from a terminal, the cursor doesn't move and you think it doesn't except your password?  It's normal not to see anything display (not even a dot) on the screen when you type in your password from a terminal with sudo.

---

### Post by LowSky on 2008-12-26
> **libihero said:**
> For some reason my sudo password doesn't work. The password it asks me for every other administrative task works. For example when I type gksudo nautulus and it the window comes up for a password, my password works. Is there a different password that I need?

gksudo is sudo with a grphical front end, so your issue makes no sense? sudo should work if the gksudo command works

---

### Post by libihero on 2008-12-27
thanks for the instructions to change password :)
but when i try to do it, it only lets me type in one character, without pressing enter, before it asks me to retype my password.
how can i allow it to let me type a full secure password?

---

### Post by mkvnmtr on 2008-12-27
Before you go changing your password tell us exactly what happened when sudo didn't respond to your pass word. You see we don't believe that it faild to respond. We think you don't understand how to use it.

---

### Post by libihero on 2008-12-29
i changed it and it does work now, i just want to know why when i changed it, it only allowed me to put in one character before it asks me to "re-enter password".
is there any way i can make it so sudo stops asking me for a password, or to stop ubuntu from asking me for an authorization password when i want to change something?

---

### Post by Michael.Godawski on 2008-12-29
There are ways to disable the sudo password but this procedure is against the forums policy:

[LIST]
[*][http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)
[/LIST]

It is indeed very strange that you can type only one character and are prompted to retype at once.

Try once again to reset your sudo password and create a new one:

[LIST]
[*][http://godawski.oxyhost.com/resetpassword.html](http://godawski.oxyhost.com/resetpassword.html)
[/LIST]

---

### Post by scorp123 on 2008-12-29
> **Michael.Godawski said:**
>  It is indeed very strange that you can type only one character and are prompted to retype at once. I had that once with a defective PS/2 keyboard .... what happened is that certain keys would produce "keycode + ENTER" instead of just producing the appropriate keycode. This was especially annoying when I had to type in a password as the code for the "ENTER" keystroke would be transmitted way too early before I had actually finished typing the password .... 

Maybe it's something similar here? Time to buy a new keyboard maybe?

---

### Post by Swiekvor on 2009-01-02
it's easier than that. 
ubuntu help:

You can restrict and enable administrative access (sudo) to users with the Users and Groups application:

1. Click system > Administration > Users and Groups
2. Click Unlock and enter your password
3. Select the user who is to be given administrative access and press Properties
4. Select the User Privileges tab
5. Check the box next to Administer the system and press OK

worked with me.

---

### Post by woody1979 on 2010-09-09
> **Swiekvor said:**
> it's easier than that. 
ubuntu help:

You can restrict and enable administrative access (sudo) to users with the Users and Groups application:

1. Click system > Administration > Users and Groups
2. Click Unlock and enter your password
3. Select the user who is to be given administrative access and press Properties
4. Select the User Privileges tab
5. Check the box next to Administer the system and press OK

worked with me.


Thanks Swiekvor worked for me too!

---

