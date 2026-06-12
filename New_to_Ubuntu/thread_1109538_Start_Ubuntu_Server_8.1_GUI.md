---
title: "Start Ubuntu Server 8.1 GUI"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by philk949 on 2009-03-28
Hi all,

I have just installed Ubuntu Server 8.1 in VMWare Workstation 6.5.
I have set it up to be a Mail Server and entered the appropriate configuration info. When I power on, I log in OK but don't know how to proceed from the resulting command prompt to a Graphical User Interface. Is there in fact a GUI or am I too deeply mired in Windows thinking?
Appreciate any help. Thanks,
Phil

---

### Post by tombom62 on 2009-03-28
No gui.  But you can get one:
> sudo aptitude install x-window-system-core gnome-core gdm

that gives you gnome.

thanks,
tombom:popcorn:

---

### Post by HermanAB on 2009-03-28
There is common misconception of ex-Windows users that a special server version is needed in order to use network services.  A Linux server distribution has a few minor optimizations to make it work better for large computational loads, but essentially it is exactly the same as a desktop version of Linux.  There is no reason why you cannot just install a regular Ubuntu version and use that as a server.

If your 'server' is sitting on a desktop and has a screen and keyboard hooked up to it, then use regular Ubuntu.  If your 'server' is a headless machine lurking in a dank corner of a dark data centre, then use the Server version of Ubuntu.  The difference between the two is however minimal.

---

### Post by philk949 on 2009-03-29
Thanks tombom and all,
I've run the installation commands and am now back at the command prompt, my original starting point. How do I access the GUI from here please?
Thanks,
Phil

---

### Post by 3rdalbum on 2009-03-29
```
sudo gdm
```

Assuming the download and installation of those packages worked.

---

### Post by cariboo on 2009-03-29
Type:

```
startx
```

at the prompt if every thing installed right you should start up to a desktop.

Jim

---

### Post by philk949 on 2009-03-29
Thanks guys 

Installing packages through the GUI as we speak

Phil

---

### Post by hyper_ch on 2009-03-29
why do you want to install a gui on a mailserver?

---

### Post by philk949 on 2009-03-29
Because I can.

---

### Post by hyper_ch on 2009-03-29
and how does a gui help setting up a server?

---

### Post by philk949 on 2009-03-29
It doesn't, but what part of "because I can" don't you understand?

---

### Post by hyper_ch on 2009-03-29
> **philk949 said:**
> It doesn't,

q.e.d.

---

### Post by philk949 on 2009-03-29
Good then. We're agreed.

---

### Post by mlentink on 2009-03-29
No, we aren't.
Hyperswiss is (imho correctly) pointing towards the essential difference between an ubuntu server and a desktop version. Even thought the difference, as per HermanAB, might be minimal in principle, in practice running a gui on a server takes serious memory overhead that as a consequence is not available to running server-based apps. Whilst a server might deliver services to clients that need gui's, the server itself can do without it, and is in fact better off without it. If you're only 'serving' a few clients, be my guest and use the desktop version. You still won't be able to administer e.g. Postfix with a GUI. To change a config file nano works just as well as gedit.
For remote administration I use WebMin, within the LAN I use ssh.

suit yourself

---

### Post by MrWES on 2009-03-29
IMHO, running a server via command line is one of the best learning experiences you can get from Linux. Howerver, if you want some sort of 'GUI' environment, check out webmin to help you maintain your server with a graphical interface:

[http://webmin.com/]("http://webmin.com/")

As mletlink sugguested.

Bill

---

### Post by philk949 on 2009-03-29
Thank you. Humble opinions noted and appreciated.

Phil

---

