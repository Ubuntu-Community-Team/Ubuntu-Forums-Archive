---
title: "windows network sharing"
date: 2007-04-01
forum: Networking &amp; Wireless
---

### Post by ThumbBumpkins on 2007-04-01
i am running ubuntu at my school, which runs a primarily windows network. when i ran windows, i shared a number of my folders over the network, and they could be accessed anywhere else in the school simply by knowing my computer name, no login name or password was necessary. i have tried to do the same thing on ubuntu, however no matter what i try it still asks for a username and password whenever i try to access my folders from anywhere else on the network, and i dont even know what the correct username or password is. can anyone help?

---

### Post by spd106 on 2007-04-02
This is a good thing, it means you have some security.

Assuming you have installed samba, you need to add yourself as a samba user. On the machine you want to access type this command, then enter the password you want to use, it can be same as your usually login, but if you change one it won't synchronise automatically (that can be setup in the smb.conf).
```
sudo smbpasswd -a *username*
```

You should now be able to access the samba shares from remote PCs.

---

### Post by dr slizer on 2007-04-03
Isn't there any graphical tool for this? I know several people who has problems with sharing files in ubuntu just because there isn't a tool for setting the Samba password in the GUI. The need for droping back to the terminal for this quite easy thing is bad, really bad, for an OS which is about usability for the novice user.

---

### Post by dmizer on 2007-04-03
yes ... you can do it by gui.

but, since you never indicated if you were using gnome, kde, xfce4, blackbox, fluxbox ... or any other of the multitude of guis available, it's impossible to give you directions for gui, especially when you consider that the gui can be custom configured to be in just about any configuration you wish.

further.  gui directions for doing what spd106 told you how to do would be about a page of directions and would have taken 20 to 30 minutes to type up well.

we give directions in cli terms because it's an extreme hassle for us to try to give gui directions, not because there is no gui way of doing things.

---

### Post by dr slizer on 2007-04-03
> **dmizer said:**
> yes ... you can do it by gui.

but, since you never indicated if you were using gnome, kde, xfce4, blackbox, fluxbox ... or any other of the multitude of guis available, it's impossible to give you directions for gui, especially when you consider that the gui can be custom configured to be in just about any configuration you wish.

further.  gui directions for doing what spd106 told you how to do would be about a page of directions and would have taken 20 to 30 minutes to type up well.

we give directions in cli terms because it's an extreme hassle for us to try to give gui directions, not because there is no gui way of doing things.

Yeah, yeah, you're correct. The GUI I had in my mind was a Ubuntu default installation, with Gnome. I'm sure KDE has the options needed (is there any options which isn't available in KDE? ;)). The Gnome GUI provided for sharing folders in Ubuntu doesn't have any options to set Samba passwords for different users, which is bad. I haven't found the options anywhere else either (note, in a default Ubuntu installation), which is even worse.

You shouldn't need to use the terminal or do any manual installation of packages to get this to work 2007. AFAIK you can't get working file sharing using SMB in a defualt Ubuntu install, without using a CLI.

---

