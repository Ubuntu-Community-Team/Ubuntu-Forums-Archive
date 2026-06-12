---
title: "How can I get Firestarter to load automatically when I log in as a regular user?"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by Noo 2 Ubuntoo on 2009-03-09
Hi, First of all as my username suggests I am new to Ubuntu and am really just a user struggling with this command line stuff so please bear with me. 

I've downloaded Firestarter and am trying to get it to load when I log in as a user (instead of administrator where it appears in the system tray).

I've been following this advice: ([http://www.fs-security.com/docs/faq.php#trayicon](http://www.fs-security.com/docs/faq.php#trayicon)) by making the following entry in the terminal:

sudo /etc/username ALL= NOPASSWD: /usr/bin/firestarter

where I substitute my username on my computer for"username" above, but I just get the message "unknown command". Any one know what the exact command line is that I should be typing?

Grateful for any advice:confused:

---

### Post by DownTown22 on 2009-03-09
By taking a quick look at that article, I think you're referring to this part:

> Giving the user permission to launch Firestarter without the root password

In order for a regular user to be able to launch Firestarter, the user must be given additional privileges. Edit your /etc/sudoers file in your favorite text editor and add the following line at the end:
username ALL= NOPASSWD: /usr/bin/firestarter

Note: Debian users should replace /usr/bin/firestarter with /usr/sbin/firestarter in the above line.

Simply replace username with whatever your login is. The specified user is now able to launch Firestarter without being prompted for a password using the command sudo firestarter. 

In that text it says you need to edit your */etc/sudoers* file, so you'd have to type (in a terminal)

> sudo gedit /etc/sudoers
Where 'gedit' is the text editor.

That should open the proper file and at the end of the file, you'd add:

> username ALL= NOPASSWD: /usr/bin/firestarter

The next step after that, "Launching Firestarter minimized to the tray on login", should be fairly straightforward if you follow that section on that webpage.

I don't have my Ubuntu laptop with me, so I can't do a quick check on all that, but if you have anymore problems, just ask!

---

### Post by Chemical Imbalance on 2009-03-09
Just so you know, firestarter is actually loaded--you just want the GUI frontend to load.  You are still protected without the icon in the tray.  Firestarter is just a GUI for Ubuntu's built-in firewall, ufw.

An easier firewall to set up I think is gufw.

You can install gufw with:
```
sudo apt-get install gufw
```
Then look in System, Administration, Firewall configuration.  Then just tick "enable" after opening it.

Firestarter is nice in that it shows you what it is blocking and some other cool features that gufw doesn't have.  They will both protect you fairly well though.

Again, do not worry that the gui isn't starting up, your firewall is still "running".

---

### Post by Noo 2 Ubuntoo on 2009-03-10
Thanks for advice Chemical Imbalance, I didn't know Firestarter operates in background even when you can't see the graphic, but I would like to see what it's doing when I'm online as a user. I followed your advice DownTown22 and after doing the "Gedit" command, I got this, in a read only file:

# /etc/sudoers 
# 
# This file MUST be edited with the 'visudo' command as root. 
# 
# See the man page for details on how to write a sudoers file. 
# 

Defaults	env_reset 

# Host alias specification 

# User alias specification 

# Cmnd alias specification 

# User privilege specification 
root	ALL=(ALL) ALL 

# Uncomment to allow members of group sudo to not need a password 
# (Note that later entries override this, so you might need to move 
# it further down) 
# %sudo ALL=NOPASSWD: ALL 

# Members of the admin group may gain root privileges 
%admin ALL=(ALL) ALL

It looks like a help file but I don't understand it, maybe I'm supposed to add the     "username ALL= NOPASSWD: /usr/sbin/firestarter" command at the end of all the text like you say & then copy it all into the terminal but I'm scared to in case I mess up the system. Can you/someone confirm what I do next please?

---

### Post by dinw3 on 2010-03-26
I encounter the same problem , unable to load Firestarter tray when the desktop appear first time . I did change sudoers file by using:

[PHP]sudo nano /etc/sudoers [/PHP]

---

### Post by Paqman on 2010-03-26
> **dinw3 said:**
> unable to load Firestarter tray when the desktop appear first time

Why do you need it running all the time? 

Firestarter isn't a firewall. It's a tool to make changes to the firewall. You only need to run it to make actual changes.

---

### Post by philinux on 2010-03-26
> **dinw3 said:**
> I encounter the same problem , unable to load Firestarter tray when the desktop appear first time . I did change sudoers file by using:

[PHP]sudo nano /etc/sudoers [/PHP]

You might need this then in case you borked sudo with the edit.

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by philinux on 2010-03-26
> **Paqman said:**
> Why do you need it running all the time? 

Firestarter isn't a firewall. It's a tool to make changes to the firewall. You only need to run it to make actual changes.

+1.

iptables is the firewall and it's default setup is pretty spot on. Firestarter as said is just a gui for editing iptables.

UFW =The Uncomplicated FireWall is a front-end for iptables, to make managing a
Netfilter firewall easier. It provides a command line interface with syntax
similar to OpenBSD's Packet Filter. It is particularly well-suited as a
host-based firewall.

GUFW=graphical user interface for ufw

gufw is an easy and intuitive way to manage your Linux firewall. It supports
common tasks such as allowing or blocking pre-configured, common p2p, or
individual port(s), and many others!

---

### Post by 3rdalbum on 2010-03-26
> **Noo 2 Ubuntoo said:**
> Thanks for advice Chemical Imbalance, I didn't know Firestarter operates in background even when you can't see the graphic, but I would like to see what it's doing when I'm online as a user.

Firestarter is only a tool to configure the built-in Linux firewall. gUFW is another tool to configure the built-in firewall. So it's not that "Firestarter works in the background", it's that "Firestarter configures the firewall, and the firewall runs on startup".

I'm quite surprised that you "would like to see what it's doing". A firewall doesn't do anything especially interesting. If there's an attempted incoming connection, it pretends your computer isn't there. If there's another attempted incoming connection, it pretends the computer isn't there. That's all a firewall does.

We often find that the logging capability of Firestarter makes some new users paranoid - they see all these (perfectly normal) incoming connections that are getting blocked, and they get worried that the Russian Mafia is hacking their box.

Also, follow this checklist:

1. Do you have an ADSL/cable modem-router? If yes, then you've already got a firewall and you don't need another one. End.
2. Have you got any servers running on your computer? Ubuntu by default will not listen to incoming connections anyway, unless you install something that will listen. If you haven't got any servers running, then you don't need a firewall. End.
3. If you DO have servers running: If you want those servers to be accessible from outside your computer, then you either need to configure your firewall to allow access, or just don't run a firewall at all. End.

---

