---
title: "how do i know the password for root ?"
date: 2011-05-16
forum: New to Ubuntu
---

### Post by neil_1 on 2011-05-16
how do i get the password for root ?
i have a user account named "neil" with password 1234
is it not the same ?

---

### Post by zealibib slaughter on 2011-05-16
In ubuntu the root account is disabled by default and there is not a root password.  The first account set up during install acts as the Sudoers account, allowing you to work as root when needed, and any accounts set up as administrator gets added to the Sudoers list.

---

### Post by jre6 on 2011-05-16
password for root != password for another user

You usually should not require the password for root. To execute any command that requires running as root/supersuser do this:
```
sudoer@computer:~sudo foobar
```Where foobar is the name of the program you want to run. You will be asked for your password. Type it, but note that it is not visible even in the form of "*" or something like that.

Note that all users can't do this. The first user that is set up is a sudoer (the user can execute sudo). Then, depending on the configuration with which other user accounts are set, they may be sudoers or non-sudoers (cannot execute sudo). If a non-sudoer executes sudo, then this will occur:

```

nonsudoer@computer:~$ sudo foobar 
We assume you have received the usual lecture from the local System Administrator. It usually boils down to these three things: 
#1) Respect the privacy of others.
#2) Think before you type.
#3) With great power comes great responsibility. 
Password: snorri is not in the sudoers file. This incident will be reported.
```

---

### Post by neil_1 on 2011-05-16
to set up a game server , the tutorial mentioned i needed to use root for a few things :/

---

### Post by coffeecat on 2011-05-16
Perhaps the tutorial mentioned needing a root terminal which is a bit different from having a root password. Have a look here for the Ubuntu root model and how to get a root terminal:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by 3rdalbum on 2011-05-16
> **neil_1 said:**
> to set up a game server , the tutorial mentioned i needed to use root for a few things :/

Well no, you don't use root, you use sudo. This gives you root, temporarily.

Any commands that need to be performed as root should instead have "sudo" before them, for instance:

```
sudo command
```

If you haven't used sudo in the last fifteen minutes, it will ask you for your password. YOUR password, not a root password. Type it in (there won't be any indications that it's accepting input as you're typing) and press Enter.

---

### Post by skypuppy on 2011-05-16
And without root, when you're setting the system up the first time, or doing daily maintenance, you have to CONTINUALLY enter the "sudoer" password over and over and over and over and over and, well, you get the picture.  There are also some programs you can't run from the GUI because they must be run by root.

---

### Post by Avidanborisov on 2011-05-16
I think you can also use
```
sudo su
```
to actually login as root.

---

### Post by coffeecat on 2011-05-16
> **skypuppy said:**
> There are also some programs you can't run from the GUI because they must be run by root.

Can't run? Gksu/gksudo works for me.

---

### Post by Lateralis on 2011-05-16
> **Avidanborisov said:**
> I think you can also use
```
sudo su
```
to actually login as root.

If you do login as root, remember to log out of the root shell the second you are finished doing whatever you are doing.  Of course, I could never recommend logging in as root as you almost never need to do that.  Just use *sudo*.

---

### Post by neil_1 on 2011-05-17
[http://www.urbanterror.info/docs/texts/123/](http://www.urbanterror.info/docs/texts/123/)

says 
> 2. Login as root and perform the following command:

---

### Post by jtarin on 2011-05-17
Not on my machine at home, but if you'll look in the Main Menu there is a "root" terminal there.

---

### Post by yetiman64 on 2011-05-17
> **neil_1 said:**
> [http://www.urbanterror.info/docs/texts/123/](http://www.urbanterror.info/docs/texts/123/)

says

Those instructions are for Linux in general. Some distros have a root account, Ubuntu's is locked by default. Read the link in post 5 by coffeecat or Link #4 in my sig about Rootsudo, it explains all you need to know.

For the commands listed in your link above, put **sudo** before them and enter your **user **password. You will likely only have to enter it once as sudo remembers you have entered your password for a five minute period.

If you ever have to do a lot of work as root (and it will likely extend past the five minute sudo timestamp), you can use a root shell with sudo -i. See the table at the bottom of [[COLOR=Blue]--THIS LINK--[/COLOR]]("http://ubuntuforums.org/showpost.php?p=6188826&postcount=4") for why to use "sudo -i" and not "sudo su".> The bottom line, is "sudo -i" is the proper command to run when you want  a root shell that is untainted by the user's environment.If you need to run graphical applications as root use "gksu" or "gksudo" with them, not "sudo". The "Graphical Sudo" section of the [[COLOR=Blue]--Rootsudo Community Documentation--[/COLOR]]("https://help.ubuntu.com/community/RootSudo"), will explain why.

Take great care when running any command or application as root.

Good luck & regards, yetiman64

---

### Post by forestG on 2011-07-16
The first time you enter Ubuntu there is no root password. You can define in terminal by typing the following commands:

su
passwd

now you can set root password.

then type "exit" to get back to "normal mode" and try "su root". If you try to put the password you set in the previous step logically it is going to work

---

### Post by wep940 on 2011-07-16
> **forestG said:**
> The first time you enter Ubuntu there is no root password. You can define in terminal by typing the following commands:

su
passwd

now you can set root password.

then type "exit" to get back to "normal mode" and try "su root". If you try to put the password you set in the previous step logically it is going to work

Actually, while there are plenty of links explaining how to do this, we refrain from giving this information out normally because this is the beginners forum and most have no idea how badly they can mess up their system using the root account.

This is why Ubuntu has chosen and prefers the sudo method.  Please refrain from posting the information you have posted here for the sake of other beginners.

---

### Post by Elfy on 2011-07-16
Please see

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://ubuntuforums.org/showpost.php?p=9315838&postcount=1](http://ubuntuforums.org/showpost.php?p=9315838&postcount=1)

---

