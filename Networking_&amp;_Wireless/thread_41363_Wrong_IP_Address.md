---
title: "Wrong IP Address"
date: 2005-06-13
forum: Networking &amp; Wireless
---

### Post by sfwasabi on 2005-06-13
I'm very new to Linux and have a Powermac G4. I wanted to set it up as a file server to start, and eventually a web and database server, to replace the expensive Windows and SQL servers I am running now.

I tested the LIVE cd, and everything worked perfectly, I was able to use Firefox, connect to my network server, use remote desktop, etc. It found all of my hardware and everything worked, so I decided to do the install.

So I did a server install, and was quite surprised to find that it booted me into a shell. I don't know Linux commands, so this took me aback, but through googling I found that 'startx' should start the gui, which it didn't. Through more googling I found that gnome isnt installed by default in a server install, but sudo apt-get update and sudo apt-get install should install gnome. Instead I received a list of items that the computer told me that it did not install because it could find a network connection.

Through further googling I came across a command to tell me my network card settings, and the settings are wrong. I can't remember what they were, but I know that the ip address that eth0 had was not on my network. I think it was a 169. number and I'm on a 10. network.

I want to get Gnome installed so I can configure the server, but it seems I need the network card to be configured to run apt-get update, but I can't find any documentation on how to configure my ethernet card from a command prompt. 

Can anyone point me on how to either start up Gnome from a fresh server install of configure my network card so I can perform an apt-get update?

Thanks!

---

### Post by kamstrup on 2005-06-13
If you're not comfortable with the command line, I'd suggest doing an ordinary installation, and installing the various services you need afterwards. As far as I know there's no difference in the basic configuration of the server and the ordinary install, except from the installed packages, but this is easy to setup later.

It sounds like you pretty much want an ordinary desktop with server components running in the background, right? Reinstalling is gonna save you tons of trouble setting everything up.

Good luck!

---

### Post by tonym on 2005-06-13
Few points that may help.

To update the network details manually,  edit the file /etc/network/interfaces.  man interfaces for details.

To stop apt going to the network edit /etc/apt/sources.list and comment out the http:// or ftp:// lines and just leave the CD line there.  That would let you install packages off the CD only.

If you want to add the full Ubuntu desktop to your existing system use

apt-get install ubuntu-desktop

Regards

Tony

---

### Post by daenney on 2005-06-13
The command to apt the desktop is
sudo apt-get install ubuntu-desktop or sudo apt-get install kubuntu-desktop depending if you want GNOME or KDE (KDE is more like Windows).

Since you're so unfamiliar with Linux I'd do what kamstrup suggested. Boot the Ubuntu cd and do a normal desktop install.
After that you can set up the right network connection settings easily, then update the whole system and then apt-get everything you need, such as samba, mysql, etc. and install it.
I'd certainly advise you to use apt and not go for compile from source because that is a real pain, certainly for new users.

So yeah, just do the normal Ubuntu install and then get the extra things you need for you server. You can always switch from GNOME to commandline by using the Ctrl+Alt+F# commands

---

