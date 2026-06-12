---
title: "WHY? Regarding Servers w/no GUI!"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by Kellemora on 2010-04-29
Hi Gang

My thinking may be way OFF on this, BUT:

#1 Known factor; Most real world servers are run without a GUI.
#2 Don't ALL programs have a Stop, Start and Restart feature?

So my comment is; Noob's learning Server (LAMP) can get up and running easier and faster using a GUI, then they can learn the Terminal method later after they understand the system better!

So my questions are:
Can a GUI be turned on and off, (stopped or started)?
WHY isn't a GUI available on Server platforms?
What harm is there of having a GUI on a Server anyhow?

I just installed LAMP (for local use) in order to test my html/css/JavaScript/and php lessons to see what's happening.
I have the DEFAULT install of Ubuntu Server and have NO IDEA YET how to get to any of the settings or configurations.  For all I know, since the server is on a LAN, I could be exposing my entire companies host of computers on that same LAN to the Entire WORLD.
I WILL be studying up on Server Management later, but right now, my programming lessons take precedence, and the default install serves my needs.

As an aside, html/css that looks great on 5 normal computers with normal monitors, sure takes a lot of work to even get close to right when viewed on LCD monitors running the exact same browsers, eg: Firefox!  I know about the many IE issues and avoid them or use workarounds, which in turn messes up Chrome5, so we gotta keep Chrome happy too if getting around all the IE bugs!

FWIW:  I'm learning all this on my own, simply from web based tutorials, as I have NO locals I can ask for help since moving to East Podunk!

TTUL
Gary

---

### Post by r-senior on 2010-04-29
There's nothing to stop you installing the desktop packages on a server. They just use up a lot of space for what should be relatively infrequent use. You won't find it helps with configuring things like Apache though, apart from a GUI editor for the config files.

Maybe have a look at Webmin? I use this to manage my web/application/file/dns server and, although I am pretty well versed with the command line, I find it very useful.

[http://www.webmin.com/]("http://www.webmin.com/")

It's in the repos BTW, so you can install with:

$ sudo apt-get install webmin

If you choose to do this on an important server, do consider the security implications of someone breaking into your webmin service.

---

### Post by psusi on 2010-04-29
> **Kellemora said:**
> 
So my questions are:
Can a GUI be turned on and off, (stopped or started)?
WHY isn't a GUI available on Server platforms?
What harm is there of having a GUI on a Server anyhow?

Yes, it can, there is, and it's a waste of resources, especially if the server has no monitor attached.  Some don't even have video cards.

If you want to start/stop the gui then just run sudo start/stop gdm.

---

### Post by OffAxis on 2010-04-29
> I have the DEFAULT install of Ubuntu Server and have NO IDEA YET how to get to any of the settings or configurations. 
which settings? apache?
The settings and configuration files follow the same philosophy as other programs on the system (for the most part).

/etc --> houses program configuration files
/var --> houses variable data

Apache server settings are here by default:
/etc/apache2/

Apache web pages are here by default:
/var/www/

> For all I know, since the server is on a LAN, I could be exposing my entire companies host of computers on that same LAN to the Entire WORLD.
If your LAN is properly firewalled there's no 'accidental' way of exposing your web server to the Internet (think of it this way; it's not routable since it has a private IP address; someone would have to explicitly do something to change that). It's totally reachable from anywhere inside the LAN, though.

> As an aside, html/css that looks great on 5 normal computers with normal monitors, sure takes a lot of work to even get close to right when viewed on LCD monitors running the exact same browsers, eg: Firefox! 
There's a setting in Firefox to fix that, if I recall. It's because IE has 'ClearType' turned on by default but Firefox doesn't.

> I know about the many IE issues and avoid them or use workarounds, which in turn messes up Chrome5, so we gotta keep Chrome happy too if getting around all the IE bugs!
It used to be worse; IE has never played well with others.
Good luck in your learning; there's a lot of quality sites out there with some very helpful tutorials.
Don't forget about the Server forum here, either.

---

### Post by chowder on 2010-04-29
I installed my LAMP server on ubuntu desktop.  Plus you can install GNOME desktop on ubuntu server.  I think server is more for production, but for home/test servers, I like having a desktop

---

### Post by arrrghhh on 2010-04-29
For my home server, no need for a GUI.  Only power & network are hooked up to it anyways, so it would be pointless to have a GUI at all.

Most server OSes (Win2k3, 2k8 Server doesn't really count, M$ likes the overhead - just means you have to upgrade your servers with every new release.) take this approach - it's probably just sitting in a data center with just power and network, so why install the unnecessary overhead of a GUI?  They just add another layer of complication and bloat.

---

### Post by bodhi.zazen on 2010-04-29
On a server, most of the management is either running a command or editing a text file, neither of which require a "graphical interface". In this context, graphical interface == X applications such as Gnome, KDE, XFCE, *box, etc.

About the only tool that can be helpful with a graphical interface would be copy-paste of commands or config files , but this can be achieved over ssh ...

Such (X) graphical interfaces do not add much, if anything.

In addition, in general, the more applications one has installed on a server the less secure the server will be as there are more potential points of attack or vulnerabilities.

Last, many servers are managed remotely, so again, a desktop graphical interface, such as Gnome, does very little. Piping a desktop over VPN is slow, insecure, and ill advised.

If one wishes a graphical interface, most people use webmin, phpmyadmin, cpanel, etc. Certainly these tools are popular. Many such tools exist

[http://www.apache-gui.com/apacheconf/index.html](http://www.apache-gui.com/apacheconf/index.html)
[http://base.secureideas.net/screens.php](http://base.secureideas.net/screens.php)
[http://www.cpanel.net/](http://www.cpanel.net/)
[http://pve.proxmox.com/wiki/Central_Web-based_Management](http://pve.proxmox.com/wiki/Central_Web-based_Management)
[http://www.ipcop.org/index-pn.php?module=pnWikka&tag=IPCopScreenshots](http://www.ipcop.org/index-pn.php?module=pnWikka&tag=IPCopScreenshots)
[http://www.engardelinux.org/modules/index/screenshots.cgi](http://www.engardelinux.org/modules/index/screenshots.cgi)


The list goes on and on ...

You will find many web based graphical interfaces, just be sure to secure them (I suggest https + password Auth at a minimum).

---

### Post by Kellemora on 2010-04-29
Thanks for ALL of your wonderful replies gang!

I recently installed Apache (LAMP) in order to SEE if my lessons were done accurately.  Don't know ANYTHING about Servers YET!

Currently (after the new kernel update this morning) it's BROKE, but that is under another Topic I just posted.

I'm trying to understand this stuff, but most of it goes right over my head!
And there are NO local groups to join like we had back home.

Thanks also for all the LINKS, it will make use of them in my studies.

TTUL
Gary

---

