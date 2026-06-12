---
title: "Kubuntu and Ubuntu"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by yangt299 on 2009-05-02
WikiPedia on Kubuntu ([http://en.wikipedia.org/wiki/Kubuntu](http://en.wikipedia.org/wiki/Kubuntu)) 
> Kubuntu is an official derivative of the Ubuntu operating system using the KDE graphical environment instead of GNOME. It is part of the Ubuntu project and uses the same underlying system. It is possible to run both the KDE desktop (kubuntu-desktop) as well as the Gnome desktop (ubuntu-desktop) interchangeably on the same machine. Every package in Kubuntu shares the same repositories as Ubuntu. 

The Wikipedia article says that it is "possible to run both the KDE desktop (kubuntu-desktop) as well as the Gnome desktop (ubuntu-desktop) interchangeably on the same machine". Can anyone give more information on this topic, and does anyone know how to run both on the same computer? Thanks a lot!

---

### Post by taurus on 2009-05-02
If you install Ubuntu (Gnome), you can install KDE with kubuntu-desktop package.  At the GUI login screen, you just pick which desktop environment you want to use from the Options.  But if you are thinking about running Gnome & KDE at the same time, I don't think that is possible.  However KDE apps should be running just fine in Gnome or vice versa.

---

### Post by MontelEdwards on 2009-05-02
I have done it before.
It is annoying because you have all of your KDE and Gnome apps all cluttered together.
I would just chose the desktop environment that you want and stay with it.
Now you can install KDE applications without installing the KDE desktop environment.
All of that will be done automatically when install an application that runs off KDE.

But if you are running ubuntu and want to install KDE, open a terminal
[applications>accessories>terminal>]
and paste this into it ```
 sudo apt-get install kubuntu-desktop 
```Then if you want to use the KDE environment, when you log in, click sessions and select KDE.

And do the same to switch back to Gnome.
But note that the boot splash screen will turn to Kubuntu.








If you are running Kubuntu and want to install Ubuntu [Gnome]
do 
```
 sudo apt-get install ubuntu-desktop
```

---

### Post by yangt299 on 2009-05-02
> **monteledwards said:**
> 
It is annoying because you have all of your KDE and Gnome apps all cluttered together.


What do you mean by "cluttered together"? Does this mean that all the apps will be displayed together, rather than seperately when u switch sessions? 

> **monteledwards said:**
> 
But note that the boot splash screen will turn to Kubuntu.


This is probably going to sound really stupid, but what is the splash screen? :confused: 

Thanks, this has helped a great deal :):):):):)

---

### Post by bgs100 on 2009-05-02
> **yangt299 said:**
> What do you mean by "cluttered together"? Does this mean that all the apps will be displayed together, rather than seperately when u switch sessions? 



This is probably going to sound really stupid, but what is the splash screen? :confused: 

Thanks, this has helped a great deal ):):):):):)

1st Question: Yes, they will be displayed together. KDE apps in Gnome menu and vice versa

2nd Question: The Splash Screen is the loading screen you see while booting up. (The screen with the ubuntu logo and a loading bar right under it)

---

### Post by MontelEdwards on 2009-05-02
> **yangt299 said:**
> What do you mean by "cluttered together"? Does this mean that all the apps will be displayed together, rather than seperately when u switch sessions? 



This is probably going to sound really stupid, but what is the splash screen? :confused: 

Thanks, this has helped a great deal :):):):):)
1. I mean that you  will have a ******** of both KDE and GNOME apps in the menu.

2. Splash screen is the screen that says Ubuntu when loading and has the progress bar.

---

### Post by candtalan on 2009-05-02
> **yangt299 said:**
> What do you mean by "cluttered together"? Does this mean that all the apps will be displayed together, rather than seperately when u switch sessions? 

I have kubuntu-desktop installed  after I first installed ordinary Ubuntu. In Applications, I now see most of the kubuntu apps in addition to the normal Ubuntu apps. It does not worry me because I have used kubuntu a lot, although less lately, and I like and use some of the kde stuff even when I am in ubuntu. The small complication is say when I want only to use 'text editor' it would be way down a longer list, but it is still there.

> This is probably going to sound really stupid, but what is the splash screen? :confused: 
Thanks, this has helped a great deal ):):):):):)
when th emachine starts, a left- right bouncing progress bar is shown  associated with startup, this will become kubuntu, also th elogin screen becomes kubuntu  type, which can be an advantge if you prefer your user  name to be already inserted for you. I think these can be removed, I do not recall how.

Note:  when installing kubuntu-desktop I saw approximately 200 packages download, no problem ther though. However, if I wanted to remove this kubuntu-desktop, I would find that only one package went, all the others remain, and would have to be removed by a terminal entry. Not very elegant I am sorry to say. And not particularly easy nor satisfying.

---

### Post by SuperSonic4 on 2009-05-02
> **candtalan said:**
> I have kubuntu-desktop installed  after I first installed ordinary Ubuntu. In Applications, I now see most of the kubuntu apps in addition to the normal Ubuntu apps. It does not worry me because I have used kubuntu a lot, although less lately, and I like and use some of the kde stuff even when I am in ubuntu. The small complication is say when I want only to use 'text editor' it would be way down a longer list, but it is still there.


when th emachine starts, a left- right bouncing progress bar is shown  associated with startup, this will become kubuntu, also th elogin screen becomes kubuntu  type, which can be an advantge if you prefer your user  name to be already inserted for you. I think these can be removed, I do not recall how.

Note:  when installing kubuntu-desktop I saw approximately 200 packages download, no problem ther though. However, if I wanted to remove this kubuntu-desktop, I would find that only one package went, all the others remain, and would have to be removed by a terminal entry. Not very elegant I am sorry to say. And not particularly easy nor satisfying.

Luckily psychocats got there before :p

[http://psychocats.net/ubuntu/puregnome](http://psychocats.net/ubuntu/puregnome)

---

### Post by blueridgedog on 2009-05-02
> **yangt299 said:**
> does anyone know how to run both on the same computer?

Your core question has been answered, but I suggest that you try each for six months or so to really get to know them and then decide on what works for you.  Bouncing back and forth is not going to do it (IMHO).

---

### Post by yangt299 on 2009-05-02
Thanks guys. Additionally, it is also possible to install Edubuntu on the same computer and switch sessions with Ubuntu and Kubuntu? Just wondering...

Thanks again!

---

### Post by yangt299 on 2009-05-02
and xubuntu and gubuntu and mythbuntu? lol 

Thanks again!

---

### Post by balloooza on 2009-05-02
Yes, all environments will work on one computer.

The real matter is what your preference is.

Do not think of kubuntu as somthing diferent than ubuntu, same with edubuntu x... myth... et cetera.
In fact, you can install any window manager, I am big on running enlightenment on low power machines.
There is nothing diferent about the applications either, you nac run amarok (notice the "K" in amaroK) on gnome, and on xfce (xubuntu/mythbuntu)
And edebuntu is gnome (with red colors, and the letters "e" and "d")

They are all what we call packages, a kind of exe, but entirelely different.
Int the dark ages, everything had to be built from source (./configure, make, make install) this also has more drawbacks besides not being lazy. With packages, you can install just about anything, and it will be maintained be the package manager.
Once you know this it is clear that kde is no more than 500MiB of gloosyness and applications, still running the same system (ubuntu, and the same package manager too)

I encourage you to try all environments, and chose the one for yourself, but having booth installed can make complications, (for those wondering what I mean, gconf will run at startup of kde, overriding ALT-^ functions, and slowing the system by running the gnome system tray icons)
But each, being used as the only one is just fine. Keep in mind having kde and gnome is just reduced PERFONMANCE, not features.

HTH, kind of off topic too.
mark

---

### Post by MontelEdwards on 2009-05-02
> **yangt299 said:**
> and xubuntu and gubuntu and mythbuntu? lol 

Thanks again!
YES YES No.
Gobuntu is mostly for developers,

---

### Post by ibuclaw on 2009-05-02
> **monteledwards said:**
> YES YES No.
Gobuntu is mostly for developers,

No, GoUbuntu is an OS that is **100%** free from proprietary/restricted applications, if memory serves correctly...


edit:
> 
Gobuntu is a GNU/Linux operating system, derived from Ubuntu, that endeavors to adhere to the Free Software Foundation's four freedoms and intends to provide a base for other free software platforms to build upon with minimal modification required. It does this by only including open-source non-restricted software. This means there will be no firmware, drivers, applications, or content included in Gobuntu that does not include the full source or whose license does not provide the right to use, study, modify, and redistribute the body of work.

Gobuntu shares the same system requirements as Ubuntu. At present, this means Gobuntu is available for 32-bit and 64-Bit PC architectures and the install requires at least 4 GB of disk space.
If you were to install the GoUbuntu package on Ubuntu (if that is possible), looks like all you'll be getting is a few extra custom themes...

Regards
Iain

---

### Post by MontelEdwards on 2009-05-02
> **tinivole said:**
> No, GoUbuntu is an OS that is **100%** free from proprietary/restricted applications, if memory serves correctly...


edit:
Oh really?
That dose kind of make sense.

---

### Post by yangt299 on 2009-05-02
Thanks guys. However, is there a more efficient way to switch without going to the main menu, then clicking on session and then KDE or whatever? Is it possible to switch sessions without logging out of your original session? Thanks again!

---

### Post by MontelEdwards on 2009-05-02
> **yangt299 said:**
> Thanks guys. However, is there a more efficient way to switch without going to the main menu, then clicking on session and then KDE or whatever? Is it possible to switch sessions without logging out of your original session? Thanks again!
No, that is the only way.
I think that X Server has to be restarted with the new environment, and cant be switched like that.
[ others please correct me if i am wrong]
But why would you want to do this?

---

### Post by ibuclaw on 2009-05-02
> **yangt299 said:**
> Thanks guys. However, is there a more efficient way to switch without going to the main menu, then clicking on session and then KDE or whatever? Is it possible to switch sessions without logging out of your original session? Thanks again!

Yes, I suppose that would be possible...

Something along the lines of (in pseudo-code, ie: **this won't work**)
```
killall gnome && kdeinit
```
Something that will kill all running gnome-desktop/panel/nautilus apps, then initiate the kde desktop, then vice versa...
I've never tried it though...

Just for convenience sake... I would probably just stick to logout/login...

Regards
Iain

---

### Post by yangt299 on 2009-05-02
I don't know, I was just wondering :P

---

### Post by MontelEdwards on 2009-05-02
> **tinivole said:**
> Yes, I suppose that would be possible...

Something along the lines of (in pseudo-code, ie: **this won't work**)
```
killall gnome && kdeinit
```
Something that will kill all running gnome-desktop/panel/nautilus apps, then initiate the kde desktop, then vice versa...
I've never tried it though...

Just for convenience sake... I would probably just stick to logout/login...

Regards
Iain
ah that sounds dangerous.
w

---

### Post by yangt299 on 2009-05-02
> **tinivole said:**
> Yes, I suppose that would be possible...

Something along the lines of (in pseudo-code, ie: **this won't work**)
```
killall gnome && kdeinit
```
Something that will kill all running gnome-desktop/panel/nautilus apps, then initiate the kde desktop, then vice versa...
I've never tried it though...

Just for convenience sake... I would probably just stick to logout/login...

Regards
Iain

does anyone have more information on this? Will it work? Thanks so much!

---

### Post by ibuclaw on 2009-05-02
> **monteledwards said:**
> ah that sounds dangerous.
w

Indeed, it may be, or it may not ...

Although this actually reminds me of one time when I somehow managed to get both running together ;)

Still have some screenies of it too.

---

### Post by MontelEdwards on 2009-05-02
> **tinivole said:**
> Indeed, it may be, or it may not ...

Although this actually reminds me of one time when I somehow managed to get both running together ;)

Still have some screenies of it too.
Woah!
That looks cool.

---

### Post by balloooza on 2009-05-02
Is that what you want, THAT is easy.

What you are seeing is kde running the gnome panel, verrrry simple

But this will only work when running kde THEN gnome, not gnome then start KDE. WHY? because kde 4.x is running plasma, this includes the desktop and the panel, and gnome will freak out , unluess you do a whole lot of extera work.

If THAT >IS< what you want, simply install
kubuntu-desktop
wait
then logout, start kde instead of gnome, then, from KDE run gnome-panel TADA, there it is, redundant, yes, cool, yes, Worth it, No. I like gnome, but I DON'T like people thinking that there is only the one way or the other way, figure out what works for you, fix what you don't like about one, it is your choice when it comes to linux.

I am going to change my sigtiture soon (thought you might want to know???)

---

### Post by yangt299 on 2009-05-02
Thanks so much for all your help :):):):):):):):)

---

### Post by -kg- on 2009-05-02
Of course, you could do what I've done; I did three separate installs of Jaunty, one each of Ubuntu, Kubuntu, and Xubuntu, each in their own partitions.

Now, instead of all the confusing and annoying entries in my menus for all the installed Desktops, I have one installation for each of the major DMs with just their software and all installed.

Of course, in order to switch, you have to completely reboot, but...I guess you can't have everything.

:lolflag:

---

