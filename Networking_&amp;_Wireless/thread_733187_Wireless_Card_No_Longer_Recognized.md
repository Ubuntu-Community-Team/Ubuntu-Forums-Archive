---
title: "Wireless Card No Longer Recognized?"
date: 2008-03-23
forum: Networking &amp; Wireless
---

### Post by porterusaf on 2008-03-23
Ok so I restarted Ubuntu 7.10 with a perfectly working wireless card & connection, and now nothing. Not to sure how it happened. Any ideas? I know that's pretty vague, but it's exactly what happened and I'm new to Ubuntu.... (ifconfig no longer even lists the interface)

Little background: Not a *nix newb, been using OpenSuse for a while and made the switch. I've got the Dell XPS M1530.

PS. How do you setup so root can login by himself? The login manager doesn't seem to want to allow it.... Thanks!

-Porter

---

### Post by nixscripter on 2008-03-23
If ifconfig doesn't list the interface, I would start at the bottom.

1. Is there any indication the card has power?
2. Is the device being detected? The output of **lspci** should contain an entry for a wireless card (if it's a PCI one).
3. Is the driver being loaded? The output of **lsmod** should have the driver in it, or at least should have loaded the ieee modules to support it.

---

### Post by porterusaf on 2008-03-23
Sorry should have added that... But yes it has power, yes the device and driver were loaded.

---

### Post by nixscripter on 2008-03-24
> ifconfig no longer even lists the interface

Just checking, that's **ifconfig -a**, right? Otherwise, it will only show connected interfaces.

Assuming yes, is there anything odd in /var/log/messages, like link ups and downs, or messages from the driver?

---

### Post by alphacrux on 2008-03-24
In your first post you asked how to log in with root. In ubuntu its taboo to log into root for security reasons. Instead you use an administrator account for most things and when you need root privileges you go to the command line and type "sudo" before the command (or gksudo if your running the command from some graphical application). If you don't want to have to type sudo over and over then enter "sudo -i" first then do your commands. Next the terminal will ask for the password of the administrative account you're already logged into (non-admin accounts can't use sudo) and from then on all commands act as if they have a sudo in front of them. 

If you want to open an application, just find the command that runs it from one of the bin folders and then type sudo in front of its name on the command line to use it with root privileges. Also Alt+F2 opens up the run application window, you can then find the command name to many known apps by clicking their name below and reading the text up top. From this window just add gksudo in front of it to open it with root privileges.

If you just HAVE to log into root then follow these instructions: press Alt+F2, then enter "gksudo users-admin", click on the root account and go into properties. Now set root's password so you can log into it

One advantage of this is that you can log into root in an account that's not administrative without having to log out first. Go to the command line and type "su" and it will ask for your root password. From then on everything you do will have root privledges much like "sudo -i". I personally never set the password so I won't be tempted to log into it. This way I make sure I use ubuntu like how its meant to be used.

EDIT: I just realized in your post that login manager was the problem, I remember in fiesty you could allow root login from the login manager but they changed that in gutsy so you'll have to do some digging to find out how its done now (that is if you're still adamant about logging in as root.) Sorry I couldn't be of more help :(

---

### Post by alphacrux on 2008-03-24
For your main question, it would be helpful to know the name of your wireless card and the driver that you're using. In most of these cases two drivers are fighting for the same card and one has to be blacklisted in /etc/modprobe.d/blacklist

Also look in /etc/log/syslog to see whats going on with your card when you boot up.

You can see which modules are currently running by typing "lsmod" into the terminal. Use "modprobe modulename" to load a module and "modprobe -r modulename" to stop one that is currently running. Using modprobe -r wont keep it from booting the next time however, so it is just a temporary fix. To get a quick look at syslog from the terminal type "dmesg". This is useful for when you've just loaded a new module and want to check for any errors that are occuring. Plus its just easier than "nano /var/log/syslog".

Also "iwconfig" is the "ifconfig" for wireless networking. I would use it while debugging your wireless connection.

---

