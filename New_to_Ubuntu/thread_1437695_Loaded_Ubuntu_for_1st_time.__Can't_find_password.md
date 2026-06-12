---
title: "Loaded Ubuntu for 1st time.  Can't find password"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by clinquist on 2010-03-24
I loaded the latest version of Ubuntu last night.  Now, when I want to change anything, it asks me for a password. I have looked around the net, but can't find out for sure if there even is a default. I'm an old DOS and Windows user.

From reading some posts, I got a little information, but nothing works yet.

So far -

At  :~$  I typed in "sudo sh<CR>Password:sh -3.1#

That didn't work.

I also tried 

sudo passwd<CR>
(my desired password)<CR>
(my desired password)

That didn't work either.

How do I get into this machine!???

---

### Post by patchwork on 2010-03-24
Assuming you installed Ubuntu with your user name (not added the user name later), your login password is your superuser password.

If you added a new user and are trying to get superuser rights, you must add the user to the adm group, and check the user privileges.

---

### Post by mastablasta on 2010-03-24
> **clinquist said:**
> Now, when I want to change anything, it asks me for a password.
 
 
Man what have you been doing? did you read the manual? Anyway, Ubuntu will ask for your username passowrd everytime you want to run something that affects other users and system. So just type in the same password as you do on start when you log in and it will work.

---

### Post by _h_ on 2010-03-24
> **clinquist said:**
> Now, when I want to change anything, it asks me for a password.

This is a security feature in Linux distros. It helps stop you and other people from making changes that aren't supposed to be made by a normal user, so you don't wreck your system. :P

---

### Post by clinquist on 2010-03-24
No, I didn't read the manual. If I can't even "start" something, I don't want to pursue it further.  Someone else was around when the install was taking place.  Maybe they entered something, but I don't think so.

I'll get the manual and read it. It isn't like I'm not familiar with computers. Currently, I design microcontroller-based data collectors (and program them too!). What I really dislike is when people berate me for being a novice. As soon as I can log in, I can start looking around.  If I can't even get that far without looking it up or being slammed by members of a user group, then I'll just go back to Windows, which (apparently) suits many of you just fine.

---

### Post by Kenny_Larsen on 2010-03-24
Ignore the nonsense above (well the unhelpful bits...)

Can I confirm you're at the login prompt? Essentially when you install Ubuntu you have to create a username and password, this password should work then for all the other times you need to enter a password for administration tasks. What exactly are you doing when it asks for the password?

Kenny

---

### Post by djackn on 2010-03-24
> **clinquist said:**
> No, I didn't read the manual. If I can't even "start" something, I don't want to pursue it further. Someone else was around when the install was taking place. Maybe they entered something, but I don't think so.
 
I'll get the manual and read it. It isn't like I'm not familiar with computers. Currently, I design microcontroller-based data collectors (and program them too!). What I really dislike is when people berate me for being a novice. As soon as I can log in, I can start looking around. If I can't even get that far without looking it up or being slammed by members of a user group, then I'll just go back to Windows, which (apparently) suits many of you just fine.
 
If someone installed ubuntu for you they will need to give you the password. If no one knows the password you may need to reinstall. Take a look at [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

---

### Post by coffeecat on 2010-03-24
> **clinquist said:**
> Maybe they entered something, but I don't think so.

Let's be clear on one thing. You cannot install Ubuntu without choosing a password. The first created user (at the installation stage) is the administrator of the system and the administrative password is the same as the login password.

Is the system set to autologin? Then, if so, the autologin option is chosen at the same stage of the installer as when the password is set. Someone must have chosen a password.

If you know your username, then you can reset a "forgotten" password with this guide:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by doas777 on 2010-03-24
here is the best place to start with sudo:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Merk42 on 2010-03-24
During the install, it asks you to come up with a username and password. The password is used to log in and (if you're the default user) to make changes to the system like installing new software.

If someone else installed Ubuntu for you, you'll have to ask them what they made your password to be.

---

### Post by coffeecat on 2010-03-24
Just to add - to refresh you or your friend's memory - if you were doing a Wubi install, you are asked to choose a password as in screenshot #2 of this link:

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

If you were doing a conventional install, this is where you choose your password and username:

---

### Post by sisco311 on 2010-03-24
[I]When you enter your password in the terminal, the terminal doesn't seem to "accept" your password because it doesn't offer any visual feedback for the characters you enter.

Your password is being accepted in the terminal. You just aren't getting any visual feedback. Go ahead and type your password and hit Enter afterwards. If you typed your password correctly, there should be no problems.[/I]

[http://www.psychocats.net/ubuntu/passwordinterminal](http://www.psychocats.net/ubuntu/passwordinterminal)


When sudo/gksu/policykit asks for a password, it needs YOUR USER password, the one you entered during the installation.

[uhelp]community/RootSudo[/uhelp]

If you have forget your password, then boot in recovery mode & reset it:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Don1500 on 2010-03-24
Try this:
```
Your_User_Name@desktop:~$ sudo update-grub
[sudo] password for Your_User_Name: <[COLOR="Red"]Enter your password[/COLOR]> <CR>
```

You will not see anything as you are typing your password, but the machine is accepting what you type.


NOTE: I used "update-grub" just to get to the sudo password prompt.

There are two passwords: 
1. Your_User_Name password, this was setup at installation and if you are prompted for your password at login, and you get in , you used it. This is the password you use every time you are prompted for a password. You can do everything, just one step at a time.

2. The "Root" user password, if you don't know how to set this up, you don't need it. This is a super-user that will allow access to everything, but also open your machine to everyone on the net. Read the security notes about logging on to ROOT. Link: [http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

