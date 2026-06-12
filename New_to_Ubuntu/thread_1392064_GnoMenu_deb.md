---
title: "GnoMenu deb?"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by steigerjb on 2010-01-27
I can't seem to be able to find the GnoMenu deb I had used before. Can someone help me?

---

### Post by Psumi on 2010-01-27
These deb files?

[https://launchpad.net/~gnomenu-team/+archive/ppa/+packages](https://launchpad.net/~gnomenu-team/+archive/ppa/+packages)

click on the name of the package to see a list of files you can download.

---

### Post by steigerjb on 2010-01-27
> **Psumi said:**
> These deb files?

[https://launchpad.net/~gnomenu-team/+archive/ppa/+packages](https://launchpad.net/~gnomenu-team/+archive/ppa/+packages)

click on the name of the package to see a list of files you can download.

ran the deb, right click>add to panel>GnoMenu> (see attached)

uh oh :|

---

### Post by steigerjb on 2010-01-29
> **steigerjb said:**
> ran the deb, right click>add to panel>GnoMenu> (see attached)

uh oh :|

[http://ubuntuforums.org/showthread.php?t=1189071]("http://ubuntuforums.org/showthread.php?t=1189071")

huh? do what? I am lost?

---

### Post by Atzu on 2010-01-29
The people on that thread are telling you to do this: Open terminal (Applications >> Accessories >> Terminal) and type: 
```
gedit .gnomenu_start.sh
```

then copy: 
[PHP]#!/bin/sh
# Trying a GnoMenu startup to clear OAFIID

case "$1" in
'start')
GnoMenu.py
;;
'stop')
;;
*)
echo "Usage: $0 { start | stop }"
;;
esac
exit 0[/PHP]

that into the gedit notepad... 
after that you need to make it executable by running (on terminal): 
```
chmod a+x .gnomenu_start.sh
```

then you need to add it to startup applications to do that you need to: go System >> Preferences and the open Startup Applications then click the button named "Add" ...

In Name put anything you want...
In command put: /home/username/.gnomenu_start.sh (Change username for your current username)
And comment... you can leave it empty.

Hope that helps!

---

### Post by steigerjb on 2010-01-29
> **Atzu said:**
> 

Hope that helps!

nope, same error :confused:

---

### Post by Psumi on 2010-01-29
> **steigerjb said:**
> nope, same error :confused:

Then prepare to bump your thread for the next 6 months before you give up. ;)

Don't bother going on the mailing list or submitting bugs either, you'll get one of the following responses:

1. I'm sorry, I cannot reproduce, can you give me the steps to do so?
1b. Sorry, I still cannot reproduce. Would it be tied to error X instead?

2. We can't fix that as there doesn't seem to be any bad code, etc.

3. Please follow the instructions again.

Or you won't get a response at all.

---

### Post by steigerjb on 2010-01-29
> **Psumi said:**
> Then prepare to bump your thread for the next 6 months before you give up. ;)

Don't bother going on the mailing list or submitting bugs either, you'll get one of the following responses:

1. I'm sorry, I cannot reproduce, can you give me the steps to do so?
1b. Sorry, I still cannot reproduce. Would it be tied to error X instead?

2. We can't fix that as there doesn't seem to be any bad code, etc.

3. Please follow the instructions again.

Or you won't get a response at all.

yeah, I know really. they never like my bug reports. they say i don't give enough info.

I wanted to make a video changing the ubuntu look to windows look. can't do it w/o gnomenu :(

---

### Post by Atzu on 2010-01-29
I dunno what gnomenu do but I'll try to help :p where did u get this .deb from?

Nvm... I see where... lol hmm have you tried installing an older version? i see that there are a karmic and another for jaunty have u tried removing the current install and installing the jaunty one?

or maybe try to download and install from here: [http://www.gtk-apps.org/content/show.php/GnoMenu+-+consolidated+menu+for+gnome?content=93056](http://www.gtk-apps.org/content/show.php/GnoMenu+-+consolidated+menu+for+gnome?content=93056)

---

### Post by Atzu on 2010-01-29
Sorry for double post... 

I downloaded from here: [https://launchpad.net/gnomenu/](https://launchpad.net/gnomenu/) and it worked... 

**If you going to try this then make sure u remove the other install :p**

There's a .tar.gz... if you want to try install it from there then you need to download that to your home folder... extract it .. then open terminal and do this (one command at a time):

```
cp gnomenu
sudo make
sudo make install
```

and it should be installed...

---

### Post by steigerjb on 2010-01-29
> **Atzu said:**
> Sorry for double post... 

I downloaded from here: [https://launchpad.net/gnomenu/](https://launchpad.net/gnomenu/) and it worked... 

**If you going to try this then make sure u remove the other install :p**

There's a .tar.gz... if you want to try install it from there then you need to download that to your home folder... extract it .. then open terminal and do this (one command at a time):

```
cp gnomenu
sudo make
sudo make install
```

and it should be installed...

you mean cd gnomenu

but anyway, didn't work. what did i do wrong?:
```
joe@joe-laptop:~$ cd gnomenu
joe@joe-laptop:~/gnomenu$ make
Makefile: Available actions: install, uninstall,
Makefile: Available variables: PREFIX, DESTDIR, AWNPREFIX, CAIRODOCKPREFIX
joe@joe-laptop:~/gnomenu$ make install
install -d /etc/gnomenu /usr/bin/ /usr/lib \
	/usr/share /usr/lib/bonobo/servers /usr/share/cairo-dock/plug-ins/Dbus/third-party/GnoMenu
install: cannot change permissions of `/etc/gnomenu': No such file or directory
install: cannot create directory `/usr/share/cairo-dock/plug-ins/Dbus/third-party': Permission denied
make: [install] Error 1 (ignored)
/bin/sh: cannot create /etc/gnomenu/prefix: Directory nonexistent
make: *** [install] Error 2
joe@joe-laptop:~/gnomenu$ 

```

---

### Post by Atzu on 2010-01-29
Yeah sorry for the cp thing :p i see that you missed the "sudo" in the commands i believe

---

### Post by steigerjb on 2010-01-30
> **Atzu said:**
> Yeah sorry for the cp thing :p i see that you missed the "sudo" in the commands i believe

ok, it installed. but i got the same error when trying to add GnoMenu to the panel

---

### Post by HomoGleek on 2010-01-30
I installed it from GetDeb [http://www.getdeb.net/software/GnoMenu](http://www.getdeb.net/software/GnoMenu) and it worked fine ... perhaps give it a try?

---

### Post by Atzu on 2010-01-30
Yeah... maybe it works... else i saw some people having errors while loading OAFIID ([http://ubuntuforums.org/archive/index.php/t-25259.html](http://ubuntuforums.org/archive/index.php/t-25259.html)) ... but not with gnomenu... what they did was reinstalling "gnome-applets" (via synaptics i guess...) try that too if that doesn't work... System >> Administration >> Synaptic package manager >> search for gnome-applets and reinstall it... or remove and install again...

---

### Post by steigerjb on 2010-01-30
> **DarrenTod said:**
> I installed it from GetDeb [http://www.getdeb.net/software/GnoMenu](http://www.getdeb.net/software/GnoMenu) and it worked fine ... perhaps give it a try?

nope, didn't work

---

### Post by steigerjb on 2010-01-30
> **Atzu said:**
> Yeah... maybe it works... else i saw some people having errors while loading OAFIID ([http://ubuntuforums.org/archive/index.php/t-25259.html](http://ubuntuforums.org/archive/index.php/t-25259.html)) ... but not with gnomenu... what they did was reinstalling "gnome-applets" (via synaptics i guess...) try that too if that doesn't work... System >> Administration >> Synaptic package manager >> search for gnome-applets and reinstall it... or remove and install again...


nope, didn't work. I am tempted to reinstall Karmic Koala. Maybe something is messed up with mine. Problem is, there is so much stuff I would have to backup, programs to reinstall,...

---

### Post by steigerjb on 2010-01-30
> **steigerjb said:**
> I am tempted to reinstall Karmic Koala. Maybe something is messed up with mine. Problem is, there is o much stuff I would have to backup, programs to reinstall,...

ugh, i just tried to install and run it with the Karmic Koala i have in virtualbox. well, it works there so like I said, there must be something wrong with my karmic koala. do i wanna reinstall? :sad::-s:? :cry:

---

### Post by HomoGleek on 2010-01-30
> **steigerjb said:**
> ugh, i just tried to install and run it with the Karmic Koala i have in virtualbox. well, it works there so like I said, there must be something wrong with my karmic koala. do i wanna reinstall? :sad::-s:? :cry:

Give it 24 hours, give the experts a chance to see this thread?

I had the error once, a simple restart helped, but thats no always the case :/

---

### Post by Atzu on 2010-01-30
> **steigerjb said:**
> ugh, i just tried to install and run it with the Karmic Koala i have in virtualbox. well, it works there so like I said, there must be something wrong with my karmic koala. do i wanna reinstall? :sad::-s:? :cry:

Yeah... Did you try restarting after trying installs? lol.. reinstalling is well... not that good :/ 

Good luck with this :p if reinstalling works well... i dunno what it could be ...

---

### Post by steigerjb on 2010-01-31
> **Atzu said:**
> Yeah... Did you try restarting after trying installs? lol.. reinstalling is well... not that good :/ 

Good luck with this :p if reinstalling works well... i dunno what it could be ...

no, i haven't reinstalled Karmic Koala. I tried upgrading to Lucid Lynx. GnoMenu still don't work :cry:

---

### Post by Psumi on 2010-01-31
> **steigerjb said:**
> no, i haven't reinstalled Karmic Koala. I tried upgrading to Lucid Lynx. GnoMenu still don't work :cry:

Installing karmic debs on lucid is not a smart thing to do. Similarly, do not install lucid debs on karmic, and even similarly still, do not install jaunty debs on karmic. it's not smart, it can save you some trouble at times, but it's not smart.

---

### Post by steigerjb on 2010-01-31
> **Psumi said:**
> Installing karmic debs on lucid is not a smart thing to do. Similarly, do not install lucid debs on karmic, and even similarly still, do not install jaunty debs on karmic. it's not smart, it can save you some trouble at times, but it's not smart.

i installed the karmic deb on karmic, then tried upgrading to lucid to maybe fix gnomenu

---

### Post by steigerjb on 2010-01-31
ok, yeah I went ahead and did do a fresh install of karmic koala. GnoMenu works now. I figured i would probably do it eventually anyway, And I figured I better go do it now cuz I got school starting back up tomorrow.

---

### Post by Atzu on 2010-01-31
> **steigerjb said:**
> ok, yeah I went ahead and did do a fresh install of karmic koala. GnoMenu works now. I figured i would probably do it eventually anyway, And I figured I better go do it now cuz I got school starting back up tomorrow.

Nice! :p good to see that it worked!

---

### Post by steigerjb on 2010-02-02
> **Atzu said:**
> Nice! :p good to see that it worked!

phew, that was close. I had backed up all my files, themes, icons,...but I couldn't find them on my portable hard drive. Then I realized...duh, the folders are .icons and .themes , there are hidden. I thought I had lost my beautiful attached themes I made...my Baltimore Ravens theme I made for me and my Legend of Zelda theme I made for my bro.

---

