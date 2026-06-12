---
title: "installing ubuntu server"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by bdeklerk on 2009-01-07
Can anyone tell me how i can have a connection when i boot from the cd to install ubuntu server.  

I have no connection and after the login on the command line i cant get to the desktop.

is there a GUI on ubuntu server?

steps to connect without connection will be appreciated

thanks

---

### Post by Titan8990 on 2009-01-07
> is there a GUI on ubuntu server?


There is no GUI on **any** Linux server. Why should there be? Otherwise its basically a desktop running server apps.

---

### Post by egalvan on 2009-01-07
> **Titan8990 said:**
> There is no GUI on **any** Linux server. Why should there be? Otherwise its basically a desktop running server apps.

Yes, no regular Linux Server has a DeskTop Environment.

But adding one does no make it a "desktop running server apps".

It would make it a SERVER running Xsystem/GUI apps.

Different orientation.

Xsystem/GUI apps  bloat the server, steal resources, and introduce possible security problems.


but having said that, I must add that it also depends on WHAT or HOW you will be using your server set-up for...

A server for home use, that will not be accessed by the Internet, and that will not see heavy loads...
Yes, loading a DE should not be a problem.

---

### Post by Iowan on 2009-01-07
> **bdeklerk said:**
> steps to connect without connection will be appreciated I must be missing the intent of the question...
A full desktop installation includes applications like media players, office suites, games, etc.  You can install only a "GUI" (window manager?) without all the extra frills... but I (or you) will have to search the forum to find what to install.

---

### Post by Indian_Guy101 on 2009-01-07
If you want just the window manager:

sudo apt-get install gnome-desktop-environment

If you want the full Ubuntu desktop:

sudo apt-get install ubuntu-desktop

hope that helps!

---

### Post by Sorivenul on 2009-01-07
I run Ubuntu Server 8.04 for my home server, with ion2 as my window manager and a small collection of applications (conkeror, irssi, vim, moc, roxterm, and a few others). My resource usage is still low, even though this particular server is only being accessed by myself or my wife.

---

### Post by albinootje on 2009-01-07
> **bdeklerk said:**
> Can anyone tell me how i can have a connection when i boot from the cd to install ubuntu server.  

I don't remember whether the Ubuntu Server cdrom tries to get an internet connection automatically during the installation or asks questions about it.
With the Debian GNU/Linux installer it certainly does.

Do you also have no internet connection after the installation from the Ubuntu Server cdrom ?
You can try this command :
```

sudo dhclient

```
And see whether you get an ip-address or not.

And concerning a GUI, maybe it's a good idea for you to install with the desktop installation cdrom, and then start with working on your server setup.
After a while when you feel more comfortable on the command line, then you could do without a GUI.
Or if you want to stick with the GUI on your server, try a few GUI applications for the services that you want to run.
There's GUI applications for configuring Samba, FTP and more.

---

### Post by -kg- on 2009-01-07
> **albinootje said:**
> I don't remember whether the Ubuntu Server cdrom tries to get an internet connection automatically during the installation or asks questions about it.
With the Debian GNU/Linux installer it certainly does.

Do you also have no internet connection after the installation from the Ubuntu Server cdrom ?
You can try this command :
```

sudo dhclient

```
And see whether you get an ip-address or not.

And concerning a GUI, maybe it's a good idea for you to install with the desktop installation cdrom, and then start with working on your server setup.
After a while when you feel more comfortable on the command line, then you could do without a GUI.
Or if you want to stick with the GUI on your server, try a few GUI applications for the services that you want to run.
There's GUI applications for configuring Samba, FTP and more.

Or leave the GUI installed to do maintenance work on it, then once it's set up (or reconfigured, or whatever work you needed to do) then log out and log in without the GUI environment to run as a normal server.

Then, as albinootje said, when you get comfortable you can switch to Command line only, or leave the minimal GUI installed and only use it when you need to.

---

