---
title: "How to see what was just done on my computer?"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by trying2learnitall on 2010-01-21
Hi I share a computer with my spouse and I have my own laptop. my laptop runs vista and the desktop is the latest ubuntu. I am not familiar at all with Ubuntu and I think my spouse is taking advantage of that and doing things to the computer. I tried to look in the history to see what our kids were on yesterday and all the history was erased. Also I was told there is some kind of sudo /pseudo password on the system that I can;t see things? Does anybody know how I can see what was just done on the system or if there is a secret user on there that I can't log in as? under users I only found 2- 1 called "root" and then the one that I use with him. is "root" a different user? Thank you and I'm sorry but I just don't get ubuntu. Even when I tried to do net session it wouldn't come up -asked for a password and i put in the one I know and it didn't work then I did net user and a few others and couldn't get anything. My clock is wrong on the comp and I went in and was making it the right time, then i clicked to set it and it told me I don't have authority to do that. 

So i was thinking the reason it says i can;t change the clock is because there is another hidden user that is the administrator. This all makes me uncomfortable. it said something about "gnome" too. oh and there was somethign in a hidden file (just did the ctrl H thing) that was "sudo_as_admin_successful" or something like that. Thank you for your help

---

### Post by steveneddy on 2010-01-21
Why don't you simply ask your spouse to tell what they are doing on the computer?

And if you aren't the administrator you will not know the "root" password.

When you say, "What was done on the computer", do you mean what websites the spouse is looking at, or do you mean what functions, applications and data the spouse is using and storing on the computer?

If you aren't logged into the regular user account with root, or in Windows terminology, the admin password, you probably won't be able to see what any of the other users are doing on any computer.

There are ways to look at web history, but only if the web browser wasn't in "stealth" mode, where one can surf without saving anything in History.

Maybe you should simply discuss this with your spouse without having to be so sneaky and spying on the person that you should trust.

You should install Ubuntu on a virtual machine like VirtualBox so you also can be proficient on Ubuntu also.

**Just to be nosy, what to you believe your spouse is doing on the computer?**

---

### Post by achase79 on 2010-01-21
sudo is a program that gives the user "super-user" status. And the password is your normal user password.

Root is a separate user on any linux system like Ubuntu (much like Windows administrator account). It is a super-user and is relatively disabled in Ubuntu to increase security.  You have to take extra steps to be able to use root at all.

gnome is the window manager, like explorer was for Windows.  There are other window managers for ubuntu like KDE, XFCE, LXDE, OpenBox, etc.  They just give you a different way to visually represent your system.

Ubuntu uses lots of "hidden" files to store program and system settings.  These are usually placed directly in the user directory.

---

### Post by bodhi.zazen on 2010-01-21
I see two issues here, the first learning how to use Ubuntu, the second is a marital issue.

In terms of learning Ubuntu, and admin access see this page:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

In terms of trusting your spouse and family members, that is beyond these forums.

In terms of monitoring the computer use of others, this is a grey area and although there can be valid reasons to do so, there are invalid reasons as well, and these tools can be abused.

I suggest if you can not trust a person who has physical access you are in trouble as physical access == root access.

---

