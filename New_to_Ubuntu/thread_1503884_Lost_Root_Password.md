---
title: "Lost Root Password"
date: 2010-06-07
forum: New to Ubuntu
---

### Post by davec51 on 2010-06-07
I just installed 10.04. I can log on with my user name, but for some functions I need to be root. When I try to log on, either in graphic mode or through the terminal, the password I thought I supplied returns "authentication failed."
How can I get out of this box short of reinstalling the whole OS?

---

### Post by Breambutt on 2010-06-07
The root account is disabled by default in Ubuntu and rookies shouldn't (need to) use it. Use the *sudo* command in front of commands that require root privileges, it will give temporary root access with your regular user name and password.

---

### Post by mbzn on 2010-06-07
Did you enable the root account?
For default Ubuntu the root account is disabled, you can do "sudo (command)" from the terminal and run "gksu (command)" for graphical.

ie. 'sudo rm /home/user/folder'
or for gui 'gksu gedit /etc/fstab'

---

### Post by sandyd on 2010-06-07
a) its kind of against the forum rules to tell people how to enable root. b) just add "sudo" in front of the command you want to run as root.

---

### Post by philinux on 2010-06-07
> **davec51 said:**
> I just installed 10.04. I can log on with my user name, but for some functions I need to be root. When I try to log on, either in graphic mode or through the terminal, the password I thought I supplied returns "authentication failed."
How can I get out of this box short of reinstalling the whole OS?

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by Breambutt on 2010-06-07
> **carlee said:**
> a) its kind of against the forum rules to tell people how to enable root.
They should tell that every time I log in with a few dozen blinking pop-up windows. ;(

I suppose I read the rules 3 years ago, just didn't start posting until now.

---

### Post by Elfy on 2010-06-07
> **carlee said:**
> a) its kind of against the forum rules to tell people how to enable root. b) just add "sudo" in front of the command you want to run as root.

It's not so much against forum rules - more that we'd rather people gave users more information.

> 
Thus the intent of the policy is we prefer if people educate new users re: permissions, etc, etc, rather then simply instruct them to set a root pw.

Specifically 

[B]The goal is to educate new users.

Our "line in the sand" is with tutorials or posts that show people how to LOG IN to a graphical desktop (gnome, KDE, etc) as root. This is completely inappropriate and unnecessary.[/B]

[http://ubuntuforums.org/showpost.php?p=9315838&postcount=1](http://ubuntuforums.org/showpost.php?p=9315838&postcount=1)

---

### Post by sandyd on 2010-06-07
> **forestpiskie said:**
> It's not so much against forum rules - more that we'd rather people gave users more information.



Specifically 

[B]The goal is to educate new users.

Our "line in the sand" is with tutorials or posts that show people how to LOG IN to a graphical desktop (gnome, KDE, etc) as root. This is completely inappropriate and unnecessary.[/B]

[http://ubuntuforums.org/showpost.php?p=9315838&postcount=1](http://ubuntuforums.org/showpost.php?p=9315838&postcount=1)
ah, thanks for clarifying that

---

### Post by Elfy on 2010-06-07
> **carlee said:**
> ah, thanks for clarifying that

welcome :)

---

### Post by Contra75 on 2010-06-07
I think davec' problem is that he forgot his password, and now can't use any of root powers. 

Since you just installed 10.04 you will not loose anything if you merely Reinstall.

---

### Post by IAmAnarch on 2010-06-07
> **davec51 said:**
> I just installed 10.04. I can log on with my user name, but for some functions I need to be root. When I try to log on, either in graphic mode or through the terminal, the password I thought I supplied returns "authentication failed."
How can I get out of this box short of reinstalling the whole OS?
Even though I'm new to Linux, I still think that enabling root would be one of the dumbest things you can do. That's just asking to have your entire system compromised. Sudo and Gksudo are much more secure alternatives to logging in as root.

If you understand the great security risks, here's how to "fix" the "problem" (I know I'll probably get flamed for telling you how to do this, but here you go):

[LIST=1]
[*]Log in as the user you created when you installed Ubuntu and open up a terminal.
[*]```
sudo passwd root
```
[*]Enter *your* user password to continue.
[*]By default, the root password is blank. Assign it a *very strong* new password.
[*]Now it has a password, but the password is locked. Unlock it with ```
sudo passwd -u root
```
[*]Log out and log in as root.
[/LIST]
Just remember that while you're logged in as root, you'll have ultimate power over the system. Graphical applications won't prompt you for a password when doing something dangerous, and you won't have to use Sudo in the terminal. Be *very* careful.

---

### Post by davec51 on 2010-06-07
Thanks all who replied. I followed the advice here are got to edit my menu.lst file on another partition (which boots Ubuntu as well as other Linux OS's) with the "sudo command from the terminal. I still think it's a nuisance to operate this way, since most of the world's computer users have access to their own computers without such paternalistic obstacles.

---

