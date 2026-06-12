---
title: "Barebones Ubuntu install"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by hellomoto on 2008-12-19
Heya, im really interested in installing a minimal ubuntu 8.10 install. 

After installing a minimal install I would like to know what packages you recommend to get going. 

I was thinking: 
xorg
xterm
gdm 
nautilus 
gnome (is this the full name of the package for the WM?)


is there any other packages I need to make a barebones install? Also is it possible to have these packages pre-downloaded if you don't have access to a wired internet connection?

---

### Post by Kareeser on 2008-12-19
The closest you can get to a barebones install (for my liking, anyway) would probably be Ubuntu Server Edition.

It's so barebones, it doesn't even have an X server, so you'd have to download GNOME... or xfce... or what have you.

---

### Post by donkyhotay on 2008-12-19
Ubuntu tends to avoid the minimalism and focuses more on being easy for inexperienced users to use (which usually means having lots of pre-installed apps). The closest thing to it is the server edition but if you really want minimalist I would use another distro which comes with a real minimal install.

---

### Post by hellomoto on 2008-12-19
I intend to set up a minimal install via the minimal .iso that ubuntu provides. 

I intend to do it this way because ubuntu is bundled with a lot of packages that i don't use and its easier to build up a ubuntu system from barebones rather than remove all the packages that i don't use.

[http://www.psychocats.net/ubuntu/minimal]("http://www.psychocats.net/ubuntu/minimal")


My question was what are the minimum packages that you would recommend from a barebones install.

after research I think its:
metacity
nautilus
synaptic
xorg
xterm
gdm
gnome-terminal

---

### Post by hellomoto on 2008-12-19
> **donkyhotay said:**
> Ubuntu tends to avoid the minimalism and focuses more on being easy for inexperienced users to use (which usually means having lots of pre-installed apps). The closest thing to it is the server edition but if you really want minimalist I would use another distro which comes with a real minimal install.


I am aware that Ubuntu is for inexperienced users but it is also for advanced users (which I would like to add im not!). 

moving to another distro isn't as beneficial for me because Ubuntu is the #1 linux desktop distro with the largest community. Moving to another distro and losing that, in my opinion would be a mistake.

---

### Post by donkyhotay on 2008-12-19
I don't consider myself a beginning user either and use ubuntu because it's the most convenient for my needs. I didn't know that ubuntu had a minimal .iso available. Must be hidden because it's not on the main download page. If you can post a link to it I might check that out next time I'm reinstalling ubuntu on my system.

---

### Post by linux_tech on 2008-12-19
Here is a download link to a <10MB Ubuntu download for a minimal install-
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by donkyhotay on 2008-12-19
Thanks!

---

### Post by linux_tech on 2008-12-19
No problem and have fun! Here is some a link to some documentation
as well- [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by mkvnmtr on 2008-12-19
I am thinking I should do a minimal install next time also. There is lots of stuff that I don't need. There is also a lot of programs that I use that are not Gnome. I found a couple of tutorials that will get me started but I haven't made a list of what I want yet. The first thing is a package manager I guess. Please keep us informed of your progress. I may get started around Christmas when I don't need the machine to work.

---

### Post by bodhi.zazen on 2008-12-19
I was going to link the minimal install link myself.

the advantage is it's small size and it is a net install, this means no DL of a 700 mb Server or alternate CD just to then have to update most of the system ...

You keep asking what to install next ? That is the advantage of a minimal install you get to decide ;)

fluxbox, openbox, icewm, minimal gnome, minimal KDE, XFCE ?

apps - Abiword, mousepad, or OOO ?

Only you can decide and I advise you explore the vast repos for light weight apps ;)

---

### Post by rsambuca on 2008-12-19
You can also follow the wiki for a [minimal installation]("https://help.ubuntu.com/community/Installation/LowMemorySystems") - It says for low memory systems, but it obviously applies to any system in general.  There are also suggestions as to what other programs you will need to get a desktop with GUI, etc.

Keep in mind that prior to upgrading to the next version of Ubuntu, you will have to install the meta-package called ubuntu-desktop, and then remove the excess stuff again.  I am also of the opinion that if you want to go the route of customizing your setup to this extent, you may as well use another distro.  There is certainly no harm in that.

---

### Post by laceration on 2008-12-19
That is an interesting strategy, all the bloat bothers me too. I would like to hear how this works out for you.  
I think to install gnome would be something like ubuntu-desktop.  I believe this would include nautilus and all the other gnome apps--this might defeat your purpose.
You might look into arch-linux where instead of installing a ready made packaged swiss army knife one size fits all you install basic functionality and then pick out what you want a la carte.

---

### Post by rsambuca on 2008-12-19
> **laceration said:**
> That is an interesting strategy, all the bloat bothers me too. I would like to hear how this works out for you.  
**I think to install gnome would be something like ubuntu-desktop**.  I believe this would include nautilus and all the other gnome apps--this might defeat your purpose.
You might look into arch-linux where instead of installing a ready made packaged swiss army knife one size fits all you install basic functionality and then pick out what you want a la carte.

No, if you install the ubuntu-desktop meta-package, then you have just installed full blown Ubuntu.  You will want to install the [gnome-core]("http://packages.ubuntu.com/intrepid/gnome-core") package instead.

---

### Post by Sorivenul on 2008-12-19
A minimal install is the only type of Ubuntu installation I do, anymore. For myself, I do one of two things:
1.) Simple command-line only setup with tools from [this thread]("http://ubuntuforums.org/showthread.php?t=977091") and elsewhere.
2.) Fluxbox, GDM, Synaptic, emelfm2, Midori, Leafpad, feh.

Do what you want, though, IMO, adding too much defeats the purpose of the minimal install.

Good luck!

---

### Post by laceration on 2008-12-19
> You will want to install the gnome-core package
Well at least I got the this might defeat your purpose part right;)
This has got me to thinking, I want to do this too, but there are so many packages, how can you avoid missing some that you need?  Unless you want to do a cli minimalist type of setup this would be quite a task to pull off.

---

### Post by rsambuca on 2008-12-19
> **laceration said:**
> Well at least I got the this might defeat your purpose part right;)
This has got me to thinking, I want to do this too, but there are so many packages, how can you avoid missing some that you need?  Unless you want to do a cli minimalist type of setup this would be quite a task to pull off.

It is not difficult at all if you follow the guide.  Anyways, apt-get will handle any dependency issues, so after installing xorg and a Desktop Environment and/or Window Manager, then everything is handled by the package manager.  For instance, if you install Firefox, the package manager will automatically install all of the packages that Firefox needs to run.

---

### Post by hellomoto on 2008-12-21
Just to let you know, i am about to attempt my minimal install over the next couple of days. I will let you all know how it goes!

---

### Post by mkvnmtr on 2008-12-21
Well we should have several reports I am about to do it also. I have resized my partitions and backed up what I think I might need. Looked int Gnome in the package manager and there are three meta packages. Desktop gnome, standard gnome and a minimal gnome. The desktop brings everything that I don't want with it. The standard brings too much of what I don't need maybe the minimal will give me Gnome looks without all the things I don't need.I am not doing it from lack of resources I just don't need a lot of stuff I don't use. I also think I might learn a little about how it all fits together.

---

### Post by hellomoto on 2008-12-21
> **mkvnmtr said:**
> Well we should have several reports I am about to do it also. I have resized my partitions and backed up what I think I might need. Looked int Gnome in the package manager and there are three meta packages. Desktop gnome, standard gnome and a minimal gnome. The desktop brings everything that I don't want with it. The standard brings too much of what I don't need maybe the minimal will give me Gnome looks without all the things I don't need.I am not doing it from lack of resources I just don't need a lot of stuff I don't use. I also think I might learn a little about how it all fits together.

i can't find any package named minimal gnome in synaptic. what is the exact name of the package and what does it consist of?

---

### Post by mkvnmtr on 2008-12-21
I  didn't not remember the name correctly. It is Ubuntu minimal. It is in meta- packages. When you look at it's dependencies I don't see anything I don't think I need. When I go to Ubuntu-standard I see a lot that I don't use. I like the Gnome look to the desktop and I think I can get it with the Ubuntu minimal.

---

### Post by hellomoto on 2008-12-21
i was thinking about installing gnome-core which is the minimum to make a gnome desktop environment. 

this includes a window manager, file manager, terminal emulator. 

I do think the window manager is an important choice, the default window manager is metacity for gnome. But i was wondering if I could use compiz-fusion without install metacity too.

does anyone know the answer to this?

Obviously the main difference is:
Metacity is a X window manager
Compiz-fusion is a compositing window manager

---

### Post by Sorivenul on 2008-12-21
> **hellomoto said:**
> i can't find any package named minimal gnome in synaptic. what is the exact name of the package and what does it consist of?
The package everyone is probably looking for is [gnome-core]("http://packages.ubuntu.com/hardy/gnome-core"). Click the link, read the package description. The link is for Hardy, but a link is at the top of the page for Intrepid users as well.

---

### Post by mkvnmtr on 2008-12-21
Yes I think Gnome core is the start but when I look at Ubuntu Minimal I see a good bit that would add to the functionality of the whole. I wonder if I should install those things one by one. I think every thing in Gnome core I should have but I am not so sure about the package Ubuntu minimal.

---

### Post by Sorivenul on 2008-12-21
> **mkvnmtr said:**
> Yes I think Gnome core is the start but when I look at Ubuntu Minimal I see a good bit that would add to the functionality of the whole. I wonder if I should install those things one by one. I think every thing in Gnome core I should have but I am not so sure about the package Ubuntu minimal.
The "ubuntu-minimal" metapackage should be automatically installed with the default CLI install from the minimal ISO.  You don't have to install it yourself.

As a second note, "ubuntu-standard" is installed automatically as well, AFAIK.  If you are going for a minimal system you will probably want most of the items these metapackages bring with them, even if you don't use them frequently.  

IMO, installing a minimal system and building should be a learning experience beyond simply, "I installed a CLI system and used apt-get to install GNOME and Firefox." If one approaches it that way, odds are that they will wind up with a system not much more minimal than the default Ubuntu install. Just my two cents there.

---

### Post by hellomoto on 2008-12-22
> **Sorivenul said:**
>   
IMO, installing a minimal system and building should be a learning experience beyond simply, "I installed a CLI system and used apt-get to install GNOME and Firefox." If one approaches it that way, odds are that they will wind up with a system not much more minimal than the default Ubuntu install. Just my two cents there.


I couldn't agree more, I am hoping whilst doing a CLI install to learn what exactly makes up my desktop and in doing so customizing it to my specific needs. 

I think there are many components of the gnome desktop environment that I don't use. Also its interesting how we are all assuming that we need the gnome bundled core components such as metacity WM, gnome terminal emulator, nautilus file manager.

Looking into this further I am toying with a possible solution. I have been thinking about running a dual boot system on my machine. Both start with a ubuntu cli install.

The first OS would be a super light, fast booting OS - that would be concerned with speed but the expense of some functionality.

The second OS would be a similar to a full gnome desktop but still installed via a Cli install to avoid unwanted bulk. 

What you think?

---

### Post by laceration on 2008-12-22
> assuming that we need the gnome bundled core components such as metacity
It says metacity or compiz-gnome for gnome-core.  I always wondered about that.  
What makes this doable is the beautifully organized [http://packages.ubuntu.com](http://packages.ubuntu.com).  Follow the breadcrumbs:P  I hope you have a lot of time if you take this on.  As I look through my packages there is stuff like support for palm pilot installed, wtf!  That is why I am interested in this approach as well as getting rid of the most unwanted Evolution.  There are so many packages though where I'd ask myself, what is this? do I want this?  That's why I'll let you guys do it first.;)

---

### Post by rsambuca on 2008-12-22
> **hellomoto said:**
> I couldn't agree more, I am hoping whilst doing a CLI install to learn what exactly makes up my desktop and in doing so customizing it to my specific needs. 

I think there are many components of the gnome desktop environment that I don't use. Also its interesting how we are all assuming that we need the gnome bundled core components such as metacity WM, gnome terminal emulator, nautilus file manager.

Looking into this further I am toying with a possible solution. I have been thinking about running a dual boot system on my machine. Both start with a ubuntu cli install.

The first OS would be a super light, fast booting OS - that would be concerned with speed but the expense of some functionality.

The second OS would be a similar to a full gnome desktop but still installed via a Cli install to avoid unwanted bulk. 

What you think?

If you are going to dual-boot, and want to learn more about the inner workings of your setup, then I strongly suggest something like Ubuntu and Arch.  Arch has a great installation wiki, but you still have to do it yourself and can learn as you go.

---

### Post by fistfullofroses on 2008-12-22
If you seriously want a minimal install you ought to start thinking of other distributions. Debian based systems are NOT minimal in anyway. There isn't much of a way to get them to be extremely minimal either.

However, GNU/Linux is GNU/Linux. Period. If you learn one well enough, the others become fairly simple. There are only two exceptions: Slackware, GoboLinux. Slackware is very BSD-esque, while GoboLinux is very Darwin-esque. For minimalistic systems you would want to look at any distribution that allows you to either install nothing but a basic toolchain and packages manager, or one that allows you to select each individual package by itself.

The absolute smallest system I think you can get is similar to tinycore linux. A kernel, busybox, uclibc, some scripts, and some basic apps to make things a little easier to deal with like: lynx, wireless-tools, package manager, and so on.

---

### Post by mkvnmtr on 2008-12-22
Well I have done it this morning. I reinstalled my Mac in a 5 Gb partition and used a live 8.04 disk to give me one big   space. Into this I installed a minimal cli system. I now have Firefox installed so I can study what I want to do. I should I don't want or need to wind up with a minimal system. I just want a system that has what I want and not a bunch of stuff I never use. I also figure I might learn something.It wasn't hard to do but it was not faster than installing full Ubuntu from a disk.

---

### Post by hellomoto on 2008-12-23
> **mkvnmtr said:**
> Well I have done it this morning. I reinstalled my Mac in a 5 Gb partition and used a live 8.04 disk to give me one big   space. Into this I installed a minimal cli system. I now have Firefox installed so I can study what I want to do. I should I don't want or need to wind up with a minimal system. I just want a system that has what I want and not a bunch of stuff I never use. I also figure I might learn something.It wasn't hard to do but it was not faster than installing full Ubuntu from a disk.

I am also going to do this today, did it go ok? What packages did you install?

---

