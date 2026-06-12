---
title: "whats the difference between all these 'butu's'"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by insanity99 on 2009-01-19
like ubuntu and kubuntu. i currenty use Ubuntu. and i love it. i find myself using windows for gaming only now. though i was wondering if ubuntu is the best option or not.

thanks

---

### Post by compiledkernel on 2009-01-19
I game regularly on my Ubuntu machine. 

So for me, its the only choice.

---

### Post by BDNiner on 2009-01-19
Underneath it all they are all the same. The different prefixs determine what packages(software) come preinstalled. for example ubuntu uses gnome desktop environment, kubuntu uses kde as its desktop and xubuntu uses xfce as its desktop.

---

### Post by insanity99 on 2009-01-19
> **compiledkernel said:**
> I game regularly on my Ubuntu machine. 

So for me, its the only choice.

yea but Windows is better for gaming. with big name games that is. wine has problems running many games, so i hear anyway

> **BDNiner said:**
> Underneath it all they are all the same. The different prefixs determine what packages(software) come preinstalled. for example ubuntu uses gnome desktop environment, kubuntu uses kde as its desktop and xubuntu uses xfce as its desktop.

oh so like the location of menu's and stuff?

---

### Post by compiledkernel on 2009-01-19
[quote=insanity99]yea but Windows is better for gaming. with big name games that is. wine has problems running many games, so i hear anyway[/quote]

Thats a popular misconception, but then it would depend on which games you play. I havent any any problems for any windows title Ive played in the past.

---

### Post by Terl on 2009-01-19
If you are mostly into gaming and are doing "heavy" games in terms of processing and graphices, like many newer games, you may want to keep a windows installation.  There is no shame in dual booting.  Yes, while WINE and Cedega work for many games they don't work for all though they do work for many.  You may need some patience to get a game running.

---

### Post by jakupl on 2009-01-19
> **insanity99 said:**
> 
oh so like the location of menu's and stuff?

Well... yeah kind of, but also the overall appearance and... actually a lot of stuff. But it's really all the same. You can convert Ubuntu to Kubuntu in a single command if you like.

---

### Post by insanity99 on 2009-01-19
> **jakupl said:**
> Well... yeah kind of, but also the overall appearance and... actually a lot of stuff. But it's really all the same. You can convert Ubuntu to Kubuntu in a single command if you like.

really? cool how do i do this? is there a risk of losing data or compatibility? 

> **Terl said:**
> If you are mostly into gaming and are doing "heavy" games in terms of processing and graphices, like many newer games, you may want to keep a windows installation.  There is no shame in dual booting.  Yes, while WINE and Cedega work for many games they don't work for all though they do work for many.  You may need some patience to get a game running.

yea i have a Wubi install. i use vista for gaming and Photoshop CS4(which according to wineHQ works badly on linux)

---

### Post by DariusS on 2009-01-19
The different desktop managers mostly change what the 'skin' of the operating system looks like. All derivatives of Ubuntu are based on debian linux, but some prefer KDE, some Gnome and other XFCE as their desktop managers. All software for one will work in any other, so you can still use KDE apps in ubuntu (using gnome) (some libs and whatnot will be installed to allow for this and some say there is a performance drop using non-native software in this way) so software packages should not limit your choice of desktops. I myself prefer Gnome, mostly because it is what I learned on and it is very easy to customize, but the others have their advantages/'pros'. Best advice I can give is get a live cd of each and try 'em out. Which one seems more intuitive in it's use for you? this will most likely be the one you'll stick with.

Although as an end note, there are people who have multiple linux distros installed on one machine (multi-booting) and others who install ubuntu and then install the other desktop managers, which can be done. You'd have to chose which to use at the login screen under 'sessions'. And keep in mind that there are other desktop managers out there besides these, and some of them are real gems.

Hope this helps!

KDE:
[]("http://upload.wikimedia.org/wikipedia/commons/5/54/KDE_4.png")[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/5/54/KDE_4.png/250px-KDE_4.png[/IMG]

XFCE:
[[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/7/71/Xfce-4.4.png/250px-Xfce-4.4.png[/IMG]]("http://upload.wikimedia.org/wikipedia/commons/7/71/Xfce-4.4.png")

---

### Post by insanity99 on 2009-01-19
so if i type in the terminal ```
apt-get install kubuntu-desktop
``` i can choose at login which one to choose? 

and this is safe?

---

### Post by cmay on 2009-01-19
i use both lxde and openbox and jwm on one machine. i use gnome and openbox on anohter. i never use kde anymore but in the start when i was using linux i logged into both gnome kde and fluxbox sessions. i think i did it back then to learn what desktop i liked best. i found i am a gnome user and i like to use older computers i fix so lxde and openbox i use when gnome is too heavy. i still sometimes install gnome to have it for the sake of haing a gnome enviroment i can use for the administrave account i have.very often  i use more than one login and user account for my self. with different desktops as i use the account. one for mail and internet and one for writing and the admin accont.

---

### Post by fooman on 2009-01-19
> **insanity99 said:**
> so if i type in the terminal ```
apt-get install kubuntu-desktop
``` i can choose at login which one to choose? 

and this is safe?

yeah.  its safe...and yes,  you can choose which desktop to boot into when you get to the login screen.  just realize that "kubuntu-desktop" will install a ton of apps that will all be listed in your menus.  a lot of folks don't like having thier menus so clogged up (doesn't bother me)...so if you like,  you could just install "kde-core" for a more condensed installation.

---

### Post by insanity99 on 2009-01-19
getting KDE now, lengthy download :D didn't know it would be this big. i will probably end up sticking with GNOME as KDE looks a tad like windows...

EDIT: if i decide i dont want it how do i uninstall it and all apps it installed? with synaptic package manager?

---

### Post by DariusS on 2009-01-19
little note of caution: 
```
sud apt-get install kde-desktop
```
will install the desktop manager, but will also install the kubuntu package programs, clogging up your menu in both kde and gnome.

```
sudo apt-get install kde-core
```
I believe this is the code to install just the desktop manager and needed libraries.

---

### Post by DariusS on 2009-01-19
> if i decide i dont want it how do i uninstall it and all apps it installed? with synaptic package manager?

I believe you can just do 
```
sudo apt-get autoremove kde-desktop
```
and it will remove what you installed and any leftover, un-needed libraries.

---

### Post by insanity99 on 2009-01-19
> **DariusS said:**
> little note of caution: 
```
sud apt-get install kde-desktop
```
will install the desktop manager, but will also install the kubuntu package programs, clogging up your menu in both kde and gnome.

```
sudo apt-get install kde-core
```
I believe this is the code to install just the desktop manager and needed libraries.

yeah thanks and how do i uninstall kubuntu and it's apps? not that i want to right now

and and the install seems to be hanging, been saying'Processing triggers for python-support ...' for ages. how do i know it's still working?

EDIT:
> **DariusS said:**
> I believe you can just do 
```
sudo apt-get autoremove kde-desktop
```
and it will remove what you installed and any leftover, un-needed libraries.

 ah thanks :D

---

### Post by fooman on 2009-01-19
> **insanity99 said:**
> 

EDIT: if i decide i dont want it how do i uninstall it and all apps it installed? with synaptic package manager?

see here:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by egalvan on 2009-01-19
> **insanity99 said:**
> getting KDE now, **lengthy download** :D didn't know it would be this big. i will probably end up sticking with GNOME **as KDE looks a tad like windows...**

EDIT: if i decide i dont want it how do i uninstall it and all apps it installed? with synaptic package manager?

Yes, it's a big download...

As for "looking like windows", well, that is the beauty of Linux.

Not only do Gnome and KDE have a different "look and feel" to them,
but you can change the "look and feel" of KDE (or Gnome, or many others).

Don't like the Window style? Or color? Change it. :)

Having said all that, there are also philosophical differences between Gnome and KDE. Don't just go by the pretty face.

---

### Post by insanity99 on 2009-01-19
yeah thanks. it worked. KDE is deffinitly more graphical, a little less simple imo. i will try it out, thanks for all the help guys

---

### Post by BDNiner on 2009-01-19
KDE takes some getting used to. Especially if you find Gnome simple and easy. Try it out, there are quite a few desktop environments that you can try besides kde and gnome.

---

### Post by insanity99 on 2009-01-19
yeah Xbuntu seems pretty good.

---

### Post by DariusS on 2009-01-19
like with KDE, try:
```
sudo apt-get install xfce-core
```
I believe that is the right syntax...

---

### Post by insanity99 on 2009-01-19
ah thanks are the cores small in size? i dont want my hard drive filled

---

### Post by snova on 2009-01-19
Yes, that's the point. Small*er*, at least, than the entirety of whatever you're installing.

---

### Post by DariusS on 2009-01-19
> are the cores small in size?

It's hard to tell right off how much space all the dependencies will take up, but I'd imagine it can't be more than the desktop manager itself, as they are typically just libraries. The kde-core file is listed in synaptic as 41k for reference, and I think xfce would be smaller. So the files themselves are not large, but I believe this is rather compressed. Still, 41k compressed can't uncompress to anything overtly large.

---

### Post by insanity99 on 2009-01-19
ok thanks

---

### Post by snova on 2009-01-19
> **DariusS said:**
> It's hard to tell right off how much space all the dependencies will take up, but I'd imagine it can't be more than the desktop manager itself, as they are typically just libraries. The kde-core file is listed in synaptic as 41k for reference, and I think xfce would be smaller. So the files themselves are not large, but I believe this is rather compressed. Still, 41k compressed can't uncompress to anything overtly large.

True, but kde-core doesn't contain anything! It's a metapackage- its sole purpose is to depend on a bunch of other packages.

Downloading it with all of its dependencies, it'll be a *lot* bigger.

---

