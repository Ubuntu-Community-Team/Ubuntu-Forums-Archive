---
title: "log in to GUI"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by owairdhi on 2009-01-07
Dears,
would you tell me how to log in to GUI interface, Now i am in the command prompt and i do not know what to do.

---

### Post by 3rdalbum on 2009-01-07
Log into the command prompt if necessary, and type this:

```
sudo gdm start
```

Press your Enter key.

How did you arrive at a command-line only system?

---

### Post by mikewhatever on 2009-01-07
Did you install a server version?

---

### Post by owairdhi on 2009-01-07
Yes I did install the server version.

---

### Post by owairdhi on 2009-01-07
I got "gdm command is not found"

---

### Post by mikewhatever on 2009-01-07
> **owairdhi said:**
> Yes I did install the server version.

Well, there is no GUI in server, install a desktop version instead.

---

### Post by wizard10000 on 2009-01-07
> **mikewhatever said:**
> Well, there is no GUI in server, install a desktop version instead.

All you've gotta do is...

```
sudo apt-get install ubuntu-desktop
```

and when it's all finished just type

```
startx
```

The GUI will start - the next time you reboot the graphical login manager will come up and things will be golden.

---

### Post by owairdhi on 2009-01-07
Is Ubuntu differ from Red hat Advance Servers, Because in Red hat servers they have the GUI Interface, both KDE and GNOME.

---

### Post by hyper_ch on 2009-01-07
I doubt that linux servers have guis by default.

---

### Post by owairdhi on 2009-01-07
Dear Wizard,

this "ubuntu-desktop" package is not found.

---

### Post by owairdhi on 2009-01-07
how to get ubuntu-desktop package.

---

### Post by wizard10000 on 2009-01-07
> **owairdhi said:**
> Dear Wizard,

this "ubuntu-desktop" package is not found.

You sure?  I'm looking at it in synaptic right now  :)

Can you please post the contents of /etc/apt/sources.list?

thanks -

---

### Post by 3rdalbum on 2009-01-07
Are you connected to the internet via an Ethernet cable? If so, then you should be able to do this:

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

If you're not connected to the Internet via an Ethernet cable (if you're trying to do it through Wi-Fi or Mobile Broadband) then you will undoubtedly find it easier to just reinstall Ubuntu, but this time use a Desktop CD.

Red Hat servers do not come with a GUI, but their workstation version does. You can run a workstation or desktop distribution as a server; in fact, at the very moment this computer is running a Samba (file sharing) server, and my father's computer is running a print server.

---

### Post by owairdhi on 2009-01-07
Permission denied

---

### Post by 3rdalbum on 2009-01-07
> **owairdhi said:**
> Permission denied

Wizard, we're talking to someone who's never used a Linux command-line before. He or she doesn't know how to open a text file on the command-line. And the sources.list is rather too big to manually type into another computer :-)

Owairdhi, please use the two commands I said in my post, and tell us what happens.

---

### Post by wizard10000 on 2009-01-07
> **3rdalbum said:**
> Wizard, we're talking to someone who's never used a Linux command-line before. He or she doesn't know how to open a text file on the command-line. And the sources.list is rather too big to manually type into another computer :-)

True enough.  Guess I haven't had enough coffee yet  :)

---

### Post by owairdhi on 2009-01-07
Dear,

I am not connected to the internet.

---

### Post by Zack McCool on 2009-01-07
> **hyper_ch said:**
> I doubt that linux servers have guis by default.

Sure they do.  Redhat defaults to an install of GNOME, but it is completely selectable during installation.

To owairdhi, if you do not have an internet connection, it will be quite difficult to install the ubuntu-desktop package.  You may be better served by installing the Desktop version of Ubuntu.  It can still be used as a server, as there is not much of a substantial difference between the two.

---

### Post by hyper_ch on 2009-01-07
is that a server release you speak of?

---

### Post by owairdhi on 2009-01-07
Yes it is Ubuntu server 8.10

---

### Post by wizard10000 on 2009-01-07
> **owairdhi said:**
> Dear,

I am not connected to the internet.

If you're not connected to the internet you can't install a GUI since there isn't one on the CD  ;)

You're either gonna have to get connected or reinstall a desktop distribution, owairdhi  :)

---

### Post by owairdhi on 2009-01-07
Dears,

I already have the Desktop i need the server.

I will try to connect to the internet and then i'll update you.

best regards and thanks to you all.

---

### Post by wizard10000 on 2009-01-07
owairdhi -

The only difference between the desktop and server versions is the kernel itself.  All the rest of the packages are exactly the same - and you can install a server kernel on a desktop distribution.

---

### Post by zipperback on 2009-01-07
> **owairdhi said:**
> Is Ubuntu differ from Red hat Advance Servers, Because in Red hat servers they have the GUI Interface, both KDE and GNOME.


The server version of Ubuntu doesn't have a GUI installed by default.

---

### Post by mikewhatever on 2009-01-08
Don't think it's been posted, so here it is, more info to consider.
[https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)

---

### Post by Vantrax on 2009-01-08
With linux it is more the applications installed that define the difference between serve and desktop not the version you install. The server version is missing some applications and the GUI, but is the same other than that.

You would probably be better off installing the desktop version and running through a quick hardening guide.

---

