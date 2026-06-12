---
title: "Why no setup for administrative privilege password"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by nnuss on 2009-12-05
I know nothing about ubuntu or linux but would seriously like to give it a fair try since I always hear how great it is and I am fed up with windows.  I installed ubuntu 9.10 on my hard drive and was never asked to supply administrative password.  Now, any time I try to add plug-ins, etc. I get a window asking for my password which I don't have.  I haven't found any answers for this on forums but only see info about using sudo which I know nothing about.  What is the purpose of the administrative password screen coming up if you can't use it.
Thanks

---

### Post by LuisGMarine on 2009-12-05
Your default "admin" password is your username password that you entered when you created your initial account.  The password that you typed in when you were installing ubuntu.

The "admin" is also called "root" but ubuntu uses sudo, which gives you temp privileges to run as an "admin" without having to log out and in as the admin.

---

### Post by bodhi.zazen on 2009-12-05
See also : [RootSudo - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RootSudo")

---

### Post by nnuss on 2009-12-05
That's what I initially assumed but it won't accept my logon password as my admin password.  I am the only user on the system.

---

### Post by Ocxic on 2009-12-05
You may not have been added to the "/etc/suders" file, that controls sudo access.

follow these steps to check and correct the issue.

Restart your computer, and hit esc when grub loads. Select the recovery option.
then type:
"cat /etc/sudoers"
At the end you should see:
%admin=ALL(ALL) ALL
if you already see that add
username ALL=(ALL) ALL
replace username with your username. 
with "nano /etc/sudoers"  save and exit by pressing ctrl-x then enter.
then type exit, and you computer should continue booting. and you issue should be fixed.

---

### Post by The Cog on 2009-12-05
Be aware that it won't show your password as you are typing it in. That can cause confusion - just go ahead typing anyway. Also, because you can't see what you're typing, it's not obvious if you mis-type it, or if you have caps-lock on.

Once you are logged in, use the command **id** from a console, and make sure you are a member of the group **admin**. If not, then you can't launch admn apps - you need to boot into recovery mode and use the command **adduser nnuss admin** (replace nnuss with whatever your username is).

---

### Post by aysiu on 2009-12-05
> **nnuss said:**
> That's what I initially assumed but it won't accept my logon password as my admin password.  I am the only user on the system.
A few things to consider:

1. Make sure you are using Ubuntu as it's designed. If you go through the point-and-click menus, you should be prompted for your **user** password. There are a lot of Linux tutorials you may read that ask you to "su to root." That is not supported in Ubuntu by default (and there's no reason to enable it). If you are following such a tutorial, then use ```
sudo -i
``` in [the terminal](http://www.psychocats.net/ubuntu/terminal) instead of *su*. Then you will be prompted for your user password instead of the root password (which is non-existent in Ubuntu and should remain so).

If you are trying to follow a tutorial that asks you to use the *su* command, why don't you tell us what you're trying to do. Chances are there is a Ubuntu-focused tutorial... or one that doesn't require the terminal at all.

2. Make sure you don't have Caps Lock on. If it's definitely not on, maybe you forgot your password or thought you'd typed it as something but really it's slightly off. If that's the case, you can [reset your password](http://www.psychocats.net/ubuntu/resetpassword).

3. If you are using the terminal, your password won't show. Just type it anyway and hit Enter. Despite what some people will tell you, this is **not** for security reasons (but it used to be decades ago). Now Linux veterans are so used to it that they don't want to change it. More details here:
[http://www.psychocats.net/ubuntu/passwordinterminal](http://www.psychocats.net/ubuntu/passwordinterminal)

---

### Post by nnuss on 2009-12-05
> **Ocxic said:**
> You may not have been added to the "/etc/suders" file, that controls sudo access.

follow these steps to check and correct the issue.

Restart your computer, and hit esc when grub loads. Select the recovery option.
then type:
"cat /etc/sudoers"
At the end you should see:
%admin=ALL(ALL) ALL
if you already see that add
username ALL=(ALL) ALL
replace username with your username. 
with "nano /etc/sudoers"  save and exit by pressing ctrl-x then enter.
then type exit, and you computer should continue booting. and you issue should be fixed.
I was going to do this but alas - when I went to recovery mode I was advised a password was needed "for maintenance".  My logon password wasn't acceptable so I went to resume normal boot which continued in command mode.  I was asked to login and enter password and my normal login and password didn't work.  At that point I just had to shut down - oh well - maybe I will reinstall the whole ubuntu and start over.  Thanks - I'll keep you posted

---

### Post by lisati on 2009-12-05
Don't forget that "case" matters to Linux. "password" is not the same as "Password" or "passWord".

---

### Post by nnuss on 2009-12-05
> **aysiu said:**
> A few things to consider:

1. Make sure you are using Ubuntu as it's designed. If you go through the point-and-click menus, you should be prompted for your **user** password. There are a lot of Linux tutorials you may read that ask you to "su to root." That is not supported in Ubuntu by default (and there's no reason to enable it). If you are following such a tutorial, then use ```
sudo -i
``` in [the terminal](http://www.psychocats.net/ubuntu/terminal) instead of *su*. Then you will be prompted for your user password instead of the root password (which is non-existent in Ubuntu and should remain so).

If you are trying to follow a tutorial that asks you to use the *su* command, why don't you tell us what you're trying to do. Chances are there is a Ubuntu-focused tutorial... or one that doesn't require the terminal at all.

2. Make sure you don't have Caps Lock on. If it's definitely not on, maybe you forgot your password or thought you'd typed it as something but really it's slightly off. If that's the case, you can [reset your password](http://www.psychocats.net/ubuntu/resetpassword).

3. If you are using the terminal, your password won't show. Just type it anyway and hit Enter. Despite what some people will tell you, this is **not** for security reasons (but it used to be decades ago). Now Linux veterans are so used to it that they don't want to change it. More details here:
[http://www.psychocats.net/ubuntu/passwordinterminal](http://www.psychocats.net/ubuntu/passwordinterminal)
I'm trying to enter a password in the GUI.  Specifically, when I tried to install a required flash player I couldn't do so because the program wouldn't accept my login password as my admin password.  I have been told that my login password is not my admin password so how do I establish one when I keep getting asked for one in GUI boxes.  I may like this OS but I need to get past some frustrating issues to really know.  I may try to delete the partitons and reinstall of the cd and see if I have better luck the next time around - don't know yet.  Thanks

---

### Post by bodhi.zazen on 2009-12-05
> **nnuss said:**
> I was going to do this but alas - when I went to recovery mode I was advised a password was needed "for maintenance".  My logon password wasn't acceptable so I went to resume normal boot which continued in command mode.  I was asked to login and enter password and my normal login and password didn't work.  At that point I just had to shut down - oh well - maybe I will reinstall the whole ubuntu and start over.  Thanks - I'll keep you posted

You are only asked for a password when booting to recovery mode if a root password is set. This is not the default behaviour.

> **nnuss said:**
> I'm trying to enter a password in the GUI.  Specifically, when I tried to install a required flash player I couldn't do so because the program wouldn't accept my login password as my admin password.  I have been told that my login password is not my admin password so how do I establish one when I keep getting asked for one in GUI boxes.  I may like this OS but I need to get past some frustrating issues to really know.  I may try to delete the partitons and reinstall of the cd and see if I have better luck the next time around - don't know yet.  Thanks

See the link I gave you re sudo.

The default is that your login password is what is used with sudo or graphical applications or gksu.

It sounds as if your user is not in the admin group and a root password has been set. This is not the default behaviour ;)

---

### Post by nnuss on 2009-12-05
Problem is solved - I deleted ubuntu partition on my hard drive and did a new install from my cd - now everything works fine - my login password is accepted in the GUI of the system as my admin password when prompted for it and I have all admin privileges - go figure - must have been a quirk in my first install - thanks everyone for your assistance - now I can check out this system - am sure looking for a replacement for windows - Thanks again.

---

