---
title: "Ubuntu Server 11.04 /etc/apt/sources.list Persmission Denied"
date: 2011-08-04
forum: New to Ubuntu
---

### Post by pmorrone on 2011-08-04
Hello,
 
Obvious from the subthread, but I am new to Ubuntu and trying to setup a GUI under Ubunto server 11.04. I wanted to setup gnome3, however, from what I read I need to first enable universe and mulitverse repositories.
 
I accessesd the root admin rights but when I type /etc/apt/sources.list I get the following error.
 
bash: /etc/apt/sources.list: Permission denied.
 
How do I access the sources.list and enable universe/multiverse.
 
Thanks for the help:confused:

---

### Post by Basher101 on 2011-08-04
Hello,
Multiverse/Universe are repositories. You add them with: sudo apt-add-repository (your repository)

For accessing the list press Alt+F2 and type gksudo gedit /etc/apt/sources.list

---

### Post by bodhi.zazen on 2011-08-05
> **pmorrone said:**
> Hello,
 
Obvious from the subthread, but I am new to Ubuntu and trying to setup a GUI under Ubunto server 11.04. I wanted to setup gnome3, however, from what I read I need to first enable universe and mulitverse repositories.
 
I accessesd the root admin rights but when I type /etc/apt/sources.list I get the following error.
 
bash: /etc/apt/sources.list: Permission denied.
 
How do I access the sources.list and enable universe/multiverse.
 
Thanks for the help:confused:

You do not need a gui, let alone gnome, on a server.

Use nano (or vim) to edit files.

```
sudo -e /etc/apt/sources.list
```

If you need a graphical interface I highly suggest tools such as webmin or phpmyadmin, depending on what you need.

---

### Post by pmorrone on 2011-08-06
> **Basher101 said:**
> Hello,
Multiverse/Universe are repositories. You add them with: sudo apt-add-repository (your repository)
 
For accessing the list press Alt+F2 and type gksudo gedit /etc/apt/sources.list
 
Thanks for your response. 
 
When I type gksudo gedit /etc/apt/sources.list I get hte following message
 
(gksudo:1683): Gtk-WARNING **: cannot open display:
 
What do I need to do to fix this.

Thanks for the help

---

### Post by 3rdalbum on 2011-08-06
> **pmorrone said:**
> Thanks for your response. 
 
When I type gksudo gedit /etc/apt/sources.list I get hte following message
 
(gksudo:1683): Gtk-WARNING **: cannot open display:
 
What do I need to do to fix this.

Thanks for the help

That poster assumed you were using a GUI. If you're on Ubuntu Server you normally won't have one, so you can't use GUI programs like gedit (or gksudo).

Instead, use this:

```
sudo nano /etc/apt/sources.list
```

This opens a terminal text editor ("nano") as root ("sudo").

When opening a file on the command line, you need to put the name of the program you want to open it in, before you put the name of the file.

---

### Post by bodhi.zazen on 2011-08-06
> **3rdalbum said:**
> Instead, use this:

```
sudo nano /etc/apt/sources.list
```

This opens a terminal text editor ("nano") as root ("sudo").


Or use the -e option

```
sudo -e /etc/apt/sources.list
```

---

### Post by pmorrone on 2011-08-06
> **3rdalbum said:**
> That poster assumed you were using a GUI. If you're on Ubuntu Server you normally won't have one, so you can't use GUI programs like gedit (or gksudo).

Instead, use this:

```
sudo nano /etc/apt/sources.list
```This opens a terminal text editor ("nano") as root ("sudo").

When opening a file on the command line, you need to put the name of the program you want to open it in, before you put the name of the file.

Thanks for the help.  I was able to get the GUI up and running and have been working on the server settings.  I do have a follow-up question though, I am trying to work with the software center and when I look to work in the "software sources" ubuntu asks me for an administrator password, however, when I type the same password I setup on installation it tells me it is the wrong password.  Is there a default software center administrator password?

---

### Post by bodhi.zazen on 2011-08-07
> **pmorrone said:**
> Thanks for the help.  I was able to get the GUI up and running and have been working on the server settings.  I do have a follow-up question though, I am trying to work with the software center and when I look to work in the "software sources" ubuntu asks me for an administrator password, however, when I type the same password I setup on installation it tells me it is the wrong password.  Is there a default software center administrator password?

Should be your login password. Is your user in the admin group ?

---

### Post by pmorrone on 2011-08-07
> **bodhi.zazen said:**
> Should be your login password. Is your user in the admin group ?

I checked the settings under users and groups and placed my user in the admin group but still have the same problem.  It will not accept my login password as the password for software sources under the software center.

---

### Post by haqking on 2011-08-07
> **pmorrone said:**
> I do not know.  How can I check to see if my user is in the admin group?


grep <username> /etc/group

make sure you are listed in the admin group

---

### Post by pmorrone on 2011-08-07
> **haqking said:**
> grep <username> /etc/group

make sure you are listed in the admin group

Thanks for the help.  I reconfirmed that I am in the admin group, however, the problem persists. If I try and access the "software sources" under the edit tab in the Software Center the system requests my administrative password.  I enter the same password from my login but it does not accept this.

---

### Post by haqking on 2011-08-07
> **pmorrone said:**
> Thanks for the help.  I reconfirmed that I am in the admin group, however, the problem persists. If I try and access the "software sources" under the edit tab in the Software Center the system requests my administrative password.  I enter the same password from my login but it does not accept this.


would you mind showing us a screen dump of both it asking you for a password and the group membership.

feel free to erase any personal data

---

### Post by pmorrone on 2011-08-07
> **haqking said:**
> would you mind showing us a screen dump of both it asking you for a password and the group membership.

feel free to erase any personal data

Uses

---

### Post by pmorrone on 2011-08-07
> **haqking said:**
> would you mind showing us a screen dump of both it asking you for a password and the group membership.

feel free to erase any personal data

My apologies but it won't let me take a screenshot of the system requesting the password.  I took a screenshot of where  I went to access the software sources while in the "Software Center'.  It is under the edit tab.  Last item, software sources.  When I click on that it requests an administrative password.

---

### Post by haqking on 2011-08-07
> **pmorrone said:**
> My apologies but it won't let me take a screenshot of the system requesting the password.  I took a screenshot of where  I went to access the software sources while in the "Software Center'.  It is under the edit tab.  Last item, software sources.  When I click on that it requests an administrative password.

ok so now you are in GUI.

Go to terminal:

gksudo gedit /etc/apt/sources.list

does it still not accept your password ?

---

### Post by pmorrone on 2011-08-07
> **haqking said:**
> ok so now you are in GUI.

Go to terminal:

gksudo gedit /etc/apt/sources.list

does it still not accept your password ?

I went into the terminal and tried to enter the sources.list as told above.  It does ask me for the password but then nothing happens.  It leaves me back at the command prompt.

Screenshot below.

---

### Post by pmorrone on 2011-08-07
I came across the following suggestion from a similar forum and don't know if my problem is identical to this users.  

[B][I]"I installed Ubuntu Server 11.04 32-bit on my computer, and then I  installed xubuntu-desktop ontop of that, and once I had a nice XFCE  desktop to play with I discovered that most programs I attempted to run  from the System->Administration menu, such as the Synaptic Package  Manager, they would pop up asking me for my administrator password.

And no matter how carefully I typed the password, it was always wrong.[/I] [I]

After examining the launcher, I discovered that it was using "gksu" to  authenticate, and gksu didn't work even though gksudo worked just fine.  Following your instructions I ran gksu-properties and indeed the  authentication mode was "su". Changed to to "sudo" and voila! No more  problem!"[/I]  [/B]

Unfortunately, as  new user, I don't know how to access or edit the launcher.

---

### Post by haqking on 2011-08-07
> **pmorrone said:**
> I went into the terminal and tried to enter the sources.list as told above.  It does ask me for the password but then nothing happens.  It leaves me back at the command prompt.

Screenshot below.


bad syntax.

add a space after word gedit.

gksudo gedit /etc/apt.sources.list

---

### Post by pmorrone on 2011-08-07
> **haqking said:**
> bad syntax.

add a spoace after word gedit.

gksudo gedit /etc/apt.sources.list

You are correct sir.  Thank you for your help.

---

### Post by pmorrone on 2011-08-07
> **haqking said:**
> bad syntax.

add a spoace after word gedit.

gksudo gedit /etc/apt.sources.list

Haqking, thanks again for the help.  I also followed the instructions from the quote I posted above from another user and entered gksu-properties from the terminal.  I switched from su to sudo and now can access the software sources from the GUI with no password errors.  

Thanks for your time and help.  Very much appreciated.

---

### Post by haqking on 2011-08-07
> **pmorrone said:**
> Haqking, thanks again for the help.  I also followed the instructions from the quote I posted above from another user and entered gksu-properties from the terminal.  I switched from su to sudo and now can access the software sources from the GUI with no password errors.  

Thanks for your time and help.  Very much appreciated.


No problem, glad we could help

---

