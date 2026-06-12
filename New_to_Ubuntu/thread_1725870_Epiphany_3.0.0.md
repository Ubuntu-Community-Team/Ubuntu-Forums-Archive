---
title: "Epiphany 3.0.0"
date: 2011-04-10
forum: New to Ubuntu
---

### Post by Ahunt on 2011-04-10
I am running the Epiphany browser version 2.30.2 on Lubuntu 10.10 and noted that the source code for the newest version, 3.0.0, is available on [Gnome projects]("http://ftp.gnome.org/pub/GNOME/sources/epiphany/3.0/").

In checking [Launchpad]("https://launchpad.net/ubuntu/+source/epiphany-browser") there seems to be no plan to include this new version in the 10.10 repository or even in the 11.04 repository.

If I have Epiphany 2.30.2 and its dependencies all installed. Is it possible to install Epiphany 3.0.0 from the source code and if so what are the step-by-step commands to do this?

---

### Post by wojox on 2011-04-11
Don't know if this helps, but I've got this installed in Arch:

```
[wojox@wojox-desktop ~]$ sudo pacman -Qi epiphany
Name           : epiphany
Version        : 3.0.0-1
URL            : http://www.gnome.org/projects/epiphany/
Licenses       : GPL
Groups         : gnome
Provides       : None
Depends On     : libsoup-gnome  gsettings-desktop-schemas  libwebkit3  nss  iso-codes  dconf
                 gobject-introspection  desktop-file-utils  hicolor-icon-theme
Optional Deps  : None
Required By    : None
Conflicts With : None
Replaces       : None
Installed Size : 11732.00 K
Packager       : Jan "heftig" Steffens <jan.steffens@gmail.com>
Architecture   : x86_64
Build Date     : Tue 05 Apr 2011 01:35:29 AM CDT
Install Date   : Sun 10 Apr 2011 07:01:42 PM CDT
Install Reason : Explicitly installed
Install Script : Yes
Description    : A GNOME3 web browser based on the WebKit rendering engine.

```

---

### Post by jtarin on 2011-04-11
You could try adding [this ppa]("https://launchpad.net/~bilalakhtar/+archive/gnome-builds") to your sources.
Don't expect a drop-in....there might be dependencies you'll have to satisfy. It can be done.

---

### Post by andrewthomas on 2011-04-11
> **jtarin said:**
> You could try adding [this ppa]("https://launchpad.net/%7Ebilalakhtar/+archive/gnome-builds") to your sources.
Don't expect a drop-in....there might be dependencies you'll have to satisfy. It can be done.
That ppa only has two packages in it and they are for natty.  To run epiphany 3.0 you should be running gnome 3.0.  Your best bet is 

[https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3) 

although this is also only for natty.  

If you want to use gnome3 in maverick, you are going to have to build it yourself using jhbuid.

---

### Post by jtarin on 2011-04-12
> **andrewthomas said:**
> That ppa only has two packages in it and they are for natty.  To run epiphany 3.0 you should be running gnome 3.0.  Your best bet is 

[https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3) 

although this is also only for natty.  

If you want to use gnome3 in maverick, you are going to have to build it yourself using jhbuid.@andrewthomas ....Your right....my bad overlooking that.

[This ]("http://packages.debian.org/experimental/epiphany-browser")will give you an idea of what your up against when it comes to resolving dependencies....and this will only be the tip of the iceberg. You would be better off just upgrading your OS if you want the browser that bad. I would read the changelog and see if it something your really need.

---

### Post by Ahunt on 2011-04-12
Thank you everyone for your responses. I was hoping it would be just a matter of compiling and installing the source code from the command line, but looking at what you have indicated here and the refs provided it looks far too complex to do, especially since I am running Lubuntu, which doesn't use Gnome!

I am mostly curious to try out Epiphany 3.0.0 to see if they resolved any of the serious bugs in 2.30.2 and whether it works better than that version, but I think jtarin is right, it would be easier to try out a different distro, like Arch, that already has Gnome 3.0 rather than trying to make it work on Lubuntu! Right now it doesn't look like it will turn up in the regular Ubuntu channels before Oneiric Ocelot!

Thank you all again for all your help!

---

### Post by missmoondog on 2011-10-13
exactly what i just searched for and only SLIGHTLY old!!

has to make one wonder how you can call linux/ubuntu secure when all their browsers, except firefox (yuck!) are so out dated?

just went through mega changes trying to figure out how to get most current version of seamonkey installed, which turned out to be quite easy even though finding anything in these forums was next to impossible!

just installed epiphany and instantly saw how old it was. was wondering if running the apt command from the epiphany website would install most current version?  sudo apt-get install epiphany-browser  probably not, huh?

thanks

---

### Post by Ahunt on 2011-10-13
Actually if you install Ubuntu 11.10 (due out today) then the [repostories have]("https://launchpad.net/ubuntu/+source/epiphany-browser") the latest version of Epiphany, which is 3.0.4.

I am not sure why you would say all the browsers except Firefox are out of date. Even Ubuntu 11.04 now has [the current version]("https://launchpad.net/ubuntu/+source/chromium-browser") of Chromium which is 14.0.835.202.

---

### Post by missmoondog on 2011-10-26
upgrade the whole freaking os just to update a browser. no wonder linux isn't going anywhere and is basically nothing more than toy, for most people, myself included.

oh yeah, chromium. another yuck, fanboy browser!!

so much for choice, huh? ;)

---

