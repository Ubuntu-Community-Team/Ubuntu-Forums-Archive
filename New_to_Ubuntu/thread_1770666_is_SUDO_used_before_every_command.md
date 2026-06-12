---
title: "is SUDO used before every command?"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by TAspr on 2011-05-29
I was just curios, is SUDO used under just about any command?  Is it a prerequesite to install, uninstall, or change files?
It seems that that command as much as the D-Click in windows.
What are the most common sudo commands?

---

### Post by jerrrys on 2011-05-29
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=common+sudo+cli+commands&as_qdr=all&sa=Google+Search&lang=en#926](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=common+sudo+cli+commands&as_qdr=all&sa=Google+Search&lang=en#926)

---

### Post by dFlyer on 2011-05-29
> **TAspr said:**
> I was just curios, is SUDO used under just about any command?  Is it a prerequesite to install, uninstall, or change files?
It seems that that command as much as the D-Click in windows.
What are the most common sudo commands?

sudo is only required for root access commands. It can be used for any command, but thats not very wise.

---

### Post by dcsoldschool53 on 2011-05-29
> **TAspr said:**
> I was just curios, is SUDO used under just about any command?  Is it a prerequesite to install, uninstall, or change files?
It seems that that command as much as the D-Click in windows.
What are the most common sudo commands?

With sudo, you can do a lot of things using this command, but not every thing. To run an  applications, you will use the gksu\gksudo command. For example, to run Seamonkey with user privileges and not as the root user to get updates, I have to type this command in a terminal.```
gksu /usr/local/seamonkey/seamonkey
```It will open Seamonkey, so that I can check for any new update for the program. 

Take a look at this web site. [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo) It may help you to understand  when you can use the sudo or gksu\gksudo command.

---

### Post by TAspr on 2011-05-29
> **dFlyer said:**
> sudo is only required for root access commands. It can be used for any command, but thats not very wise.

Man alive, I wish this was not so difficult.  So are you telling me that I should not have run these as a root user?  Are the following posts then, the 
gksu /usr/local/seamonkey/seamonkey
The way to install a program not as root then?

---

### Post by wolfen69 on 2011-05-29
> **TAspr said:**
> Man alive, I wish this was not so difficult.  So are you telling me that I should not have run these as a root user?  Are the following posts then, the 
gksu /usr/local/seamonkey/seamonkey
The way to install a program not as root then?

You can't install an app as non-root. Why do you need to do this when most apps are in the software center?

---

### Post by durand on 2011-05-29
If you want a program, look in Applications > Ubuntu Software Center. If it isn't there, then you'd need to follow the instructions on the program website. There should be a .deb file which is the next best way to install it. "sudo" basically just makes you the admin temporarily so you can install a program. If you're doing it graphically, there is an equivalent thing that comes up asking for your password.

---

### Post by TAspr on 2011-05-29
> **wolfen69 said:**
> You can't install an app as non-root. Why do you need to do this when most apps are in the software center?

Recommendation I guess to not install the software under a "root" user.

---

### Post by TAspr on 2011-05-29
> **durand said:**
> If you want a program, look in Applications > Ubuntu Software Center. If it isn't there, then you'd need to follow the instructions on the program website. There should be a .deb file which is the next best way to install it. "sudo" basically just makes you the admin temporarily so you can install a program. If you're doing it graphically, there is an equivalent thing that comes up asking for your password.

Got it, so are you talking about the graphical box that asks for your password, is that what you mean?

---

### Post by dFlyer on 2011-05-29
> **TAspr said:**
> Man alive, I wish this was not so difficult.  So are you telling me that I should not have run these as a root user?  Are the following posts then, the 
gksu /usr/local/seamonkey/seamonkey
The way to install a program not as root then?

sudo is required to install a program, usually not required to run the program. The only time you don't need to use sudo to install a program is if your installing it in your home folder from a tar or compressed file. My advice is to open a terminal and enter this:

man sudo

---

### Post by Vaphell on 2011-05-29
Yes. Sudo and that little box asking for password do the same thing - temporarily elevate rights. If a program is used to do some administration stuff (like Synaptic package manager or Software Center) it's configured in menus to run automatically with sudo/gksudo and password box pops up. If you want to run a program manually from terminal and grant it temprorary admin rights to allow it to modify files outside your home directory, you use sudo explicitly. Most programs dont need admin rights 99% of the time so default approach is 'without sudo unless really necessary'

---

### Post by Thewhistlingwind on 2011-05-29
Understand, Unix was made for large multiuser environments. (Or at least it evolved to become this.)

You can't have everyone changing the system in a large, multiuser environment. So you have the root account which only the sysadmin gets to use.

Because your a single user, from your perspective it's tedious. But in reality it's a long standing protection to stop unauthorized users from destroying the system.

Anything that would affect all users will need the root password.

---

### Post by galacticaboy on 2011-05-29
Pretty Much...

---

### Post by TAspr on 2011-05-29
Ahh... Understand..

So as Dflyer said above, 

[I][B]My advice is to open a terminal and enter this:

man sudo[/B]

[/I]What does this command do?

---

### Post by Thewhistlingwind on 2011-05-29
> **TAspr said:**
> Ahh... Understand..

So as Dflyer said above, 

[I][B]My advice is to open a terminal and enter this:

man sudo[/B]

[/I]What does this command do?

It gives the manual page for sudo, AKA documentation.

man will give you the documentation for most commands.
If not try info, or help.

Use less or cat to read text documents, less can scroll, cat can't. (Plus using cat is considered bad form.)

---

### Post by jerrrys on 2011-05-29
man is the terminal command for manuals.  may be better to start with 'man man"

---

