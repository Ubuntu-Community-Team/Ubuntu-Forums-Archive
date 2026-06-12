---
title: "Ubuntu or Xubuntu?"
date: 2010-03-19
forum: New to Ubuntu
---

### Post by Bill Lariviere on 2010-03-19
Hi all, i'm absolutely new to Linux/Ubuntu. I'm having lots of typical Windows XP issues on a rather old (2001) computer, and decided to go for (X)Ubuntu. I played around with both live CD's of the latest version, but still can't decide which way to go. Based on my hardware, should i go for Ubuntu (Gnome) or Xubuntu (Xfce)?

Processor    x86 Family 6 Model 4 Stepping 4 AuthenticAMD ~1410 Mhz
BIOS-version/date    Award Software, Inc. ASUS A7A266 ACPI BIOS Revision 1006, 20/08/2001
Physical memory: 512 MB RAM
Video card:   NVIDIA GeForce2 MX/MX 400 64MB
USB 1.0 (no 2.0 support)
35 GB harddisk

Any help would be greatly appreciated!! (i'm totally new to this):)

---

### Post by RedRat on 2010-03-19
Well of course you could try both of them. Try out the Ubuntu and if you don't like it, format the hard drive and install Xubuntu. Another one you might want to look at, since you are coming from Windows XP is PCLinux. I had an old Dell much like yours, a bit less powerful, and PCLinux performed quite well on that machine--but that was like 3 years ago now. 

You might want to add some memory if that is possible with you machine, but know full well that it is 9 years old and hard drives do die. You might want to replace your hard drive, if you can find a replacement and also add a new USB 2 card in your machine. But at the end of the day, you are kinda beating a dead horse here.

---

### Post by Ozymandias_117 on 2010-03-19
I would go with Xubuntu. Xfce is much lighter, which means it will run faster, and and since your processor isn't all that fast... But if you are fine with the speed that Ubuntu runs, then I would choose that. But really, desktop managers just come down to personal preference.

You can always install the other if you want to try it:

Xubuntu:

```
sudo apt-get install xubuntu-desktop
```

Ubuntu:

```
sudo apt-get install ubuntu-desktop
```

---

### Post by NightwishFan on 2010-03-19
Hello and welcome to Ubuntu Forums, I am glad to meet you.

32-bit Ubuntu will run fine on there. Enjoy! Please ask or post a thread if you need any help.

---

### Post by Wamiduku on 2010-03-27
Lifting the thread, since I want a lean server. Playing with Ubuntu in VMWare, I found that both Ubuntu and Xubuntu (both in 64-bit) use about 200MB RAM, so there doesn't seem to be any difference.

(I'm going to run VirtualBox, and managing VB via command line is bad for my sanity, so I need a GUI on the server.)

---

### Post by PatrickMoore on 2010-03-27
what about an ubuntu minimal install? there are quite a few noce tutorials out there and they are quite lean. I personally love my minimal setup

---

### Post by uRock on 2010-03-27
Ubuntu will run poorly with only 512MB RAM. Lubuntu is the lightest and fastest version which runs the LXDE desktop environment. I would recommend giving it a spin. Xubuntu uses almost the same amount of resources as Ubuntu. Do feel free to give them all a try though.

---

### Post by Wamiduku on 2010-03-27
@PatrickMoore: Sounds interesting! Do you have a link to a tutorial that works? I've spent a lot of time on Linux tutorials that only result in lots of error messages, so if you remember a link to a tried and tested one, it'd be greatly appreciated.

---

### Post by NightwishFan on 2010-03-27
Here is my advice.

Install using the Ubuntu Server CD so you have the server optimized kernel and packages available. Then when you are connected to the internet just aptitude install a basic environment, whatever you are comfortable with.

These packages will install a very basic environment of the given desktop and let you install what you want after.

First install the package xorg.
```
sudo aptitude install xorg
```


Then these, if you like...

Gnome: gnome-core gdm
KDE: kde-minimal kdm
XFCE: xfce4 gdm
LXDE: lxde gdm

Or for window managers:

Fluxbox: fluxbox gdm
IceWm: icewm gdm

You could also not use GDM and just use startx to log in
I thought Slim was included in Ubuntu it seems not, xdm is an alternative.

---

### Post by cgroza on 2010-03-27
> **iRock said:**
> Ubuntu will run poorly with only 512MB RAM. Lubuntu is the lightest and fastest version which runs the LXDE desktop environment. I would recommend giving it a spin. Xubuntu uses almost the same amount of resources as Ubuntu. Do feel free to give them all a try though.

My PC has 256 mb Ram and a 1.6 GHz Cpu and its running well with a swap partition. Ubuntu will run very well on that machine.

---

### Post by NightwishFan on 2010-03-27
If you want lightweight I could probably put Debian on my pocket calculator. ;)

---

### Post by Wamiduku on 2010-03-27
> **NightwishFan said:**
> Here is my advice.

Install using the Ubuntu Server CD so you have the server optimized kernel and packages available. Then when you are connected to the internet just aptitude install a basic environment, whatever you are comfortable with.

Sounds promising, I'll try that. Thx for the advice! :)

---

### Post by uRock on 2010-03-27
> **cgroza said:**
> My PC has 256 mb Ram and a 1.6 GHz Cpu and its running well with a swap partition. Ubuntu will run very well on that machine.

Depends on one's definition of well, but if it makes you happy.:)

---

### Post by Wamiduku on 2010-03-27
> **Wamiduku said:**
> ... I found that both Ubuntu and Xubuntu (both in 64-bit) use about 200MB RAM, so there doesn't seem to be any difference

I have to correct my own post: those where the numbers for fresh downloads/installs of v9.10. I just ran updates on them both. Ubuntu now takes 500 MB and Xubuntu 450 MB. Huh?!? Something must have gotten seriously bloated in that update.

Tried Lubuntu 9.x BTW, but clicking the "Install" icon doesn't do anything at all. No install - no joy.

---

### Post by bhmildy on 2010-03-28
I'm running 9.10 Gnome with 512 MB RAM, 2.8Ghz processor, and the system kicks butt.  Regularly runs on 100MB.  Stinks when I try to run VirtualBox with Win2k with 168 MB RAM though.

Nightwishfan:  since this is an absolute beginners thread, could you explain for me what the differences are between x11, window managers, GDM, and a "basic environment" are? I thought you needed x for GDM to work? Thx

---

### Post by Ozymandias_117 on 2010-03-28
> **bhmildy said:**
> 
Nightwishfan:  since this is an absolute beginners thread, could you explain for me what the differences are between x11, window managers, GDM, and a "basic environment" are? I thought you needed x for GDM to work? Thx

x11: Almost every GUI relies on X11 to run. (I think they all do, but there may be some I'm unaware of)

window managers: The things that border your windows and put the close, minimize and maximize etc. Most Desktop environments (Like Gnome KDE XFCE and LXDE) have a Window Manager, file browser and a desktop panel

GDM: The Gnome logon screen. There are also KDM and XDM... Another option is to just run the command startx

---

### Post by edgy360 on 2010-03-28
> **iRock said:**
> Ubuntu will run poorly with only 512MB RAM. Lubuntu is the lightest and fastest version which runs the LXDE desktop environment. I would recommend giving it a spin. Xubuntu uses almost the same amount of resources as Ubuntu. Do feel free to give them all a try though.

Ubuntu works great for me on my old laptop, it is much faster than XP.

---

### Post by theozzlives on 2010-03-28
_True_ Linux servers don't use a GUI. I admit, at first, I ran Ubuntu Desktop as a server but now my server is running the REAL server software (CLI only). You don't have all the overhead of the GUI bogging down your server.

---

### Post by KdotJ on 2010-03-28
> **theozzlives said:**
> _True_ Linux servers don't use a GUI. I admit, at first, I ran Ubuntu Desktop as a server but now my server is running the REAL server software (CLI only). You don't have all the overhead of the GUI bogging down your server.


I too did the same, using desktop ubuntu as a server, but after playing around with the server edition in a VM, I decided to install It on my server. Got it running great now with no monitor or keyboard connected, all admin work done via ssh

---

### Post by Wamiduku on 2010-03-28
> **theozzlives said:**
> _True_ Linux servers don't use a GUI. I admit, at first, I ran Ubuntu Desktop as a server but now my server is running the REAL server software (CLI only). You don't have all the overhead of the GUI bogging down your server.
That's how i run my web server, but it doesn't work for my VM host. It would, if VMWare Server, which has a remote web gui, had worked my D510MO. Now I have to run Virtualbox instead, which has no remote GUI at all, so i need a GUI on the server. It's possible to run Virtualbox headless, but it's so much faster for me to use the VBox gui than to search the VBox manual for command line syntax.

---

### Post by Wamiduku on 2010-03-28
Darn - I've been trying to connect to the computer through remote desktop, but it's impossible to login that way, so remote desktop is **completely useless** for remote admin. 

Tried with a different VNC server ([http://www.marclewis.com/archives/2009/11/25/remote-desktop-on-xubuntu-910/](http://www.marclewis.com/archives/2009/11/25/remote-desktop-on-xubuntu-910/)) but still can't login. Also tried NoMachine's nxserver+nxclient, trying to get it to work by following the advice at [http://forum.xfce.org/index.php?topic=2536.0](http://forum.xfce.org/index.php?topic=2536.0), but everything becomes totally weird with the desktop split into small, unclickable windows. Tried FreeNX too, same result.

It's so frustrating, knowing that what I've been trying to do for hours now, is the equivalent of merely clicking the remote desktop checkbox in the System tab in Windows XP. 

If there were D510MO AHCI drivers for XP, I would have reached the point where I'd throw out Linux and install XP on the computer. I never regarded Windows as an OS that "just works", but after so many obscure command lines and config black magic, unsuccessfully trying to do something that takes 1 minute in Windows, does anyone still wonder why Windows users don't switch over to Linux?

It's great if you just need what's in the box, but it seems you can't do anything out-of-the-box without hours of reading about command line syntax and config file entries for every little thing you want to do.

OK, one last attempt: I'll ditch Xubuntu and install Ubuntu + nxserver and see if I can log in remotely. If that fails too, I'll reluctantly switch the system to the slower and noisier IDE emulation and install XP.

[edit: I tried X11 Forwarding and XMing too, but by then my patience only sufficed for half an hour of tinkering, which obviously wasn't enough to get the blasted thing working.]

---

### Post by Howleon on 2010-06-07
I got a Acer Aspire 1710
Intel P4 2.8 GHZ
RAM 512MB
Graphic carde nVidia geforce5400 with 64 MB.

I am just thinking about installing Xubuntu on it to get something lighter but it seems that Xubuntu is not so much lighter than Ubuntu.
Is it true or not?
Regards

---

### Post by NightwishFan on 2010-06-07
Xubuntu is ok. It is not absurdly lighter though.

---

### Post by slooksterpsv on 2010-06-07
I personally recommend Xubuntu with those specs. Not that Ubuntu won't run, cause Ubuntu only requires like 256 or 384 MB of RAM, but if you want a snappier system, Xubuntu is light on resources - I've thought about switching to it... I like my Ubuntu though.

---

### Post by themarker0 on 2010-06-07
> **Howleon said:**
> I got a Acer Aspire 1710
Intel P4 2.8 GHZ
RAM 512MB
Graphic carde nVidia geforce5400 with 64 MB.

I am just thinking about installing Xubuntu on it to get something lighter but it seems that Xubuntu is not so much lighter than Ubuntu.
Is it true or not?
Regards

Ha i have the same one. If your going to do an XFCE install, do it the right way and do it from the Ubuntu Minimal cd. Its much less crap and much faster from my own experience. Gnome with no effects should run decent on it. I had it on it for about a year, before scrapping it. Though saying that was 2 or 3 years ago now, and it was an older version of ubuntu. I would install both managers if you have the hard drive space. If not just use XFCE, its decent ;)


Edit: After seeing your okay with windows, try LXDE see if you like it. I use it on my new Acer Aspire Timeline, and i love it a lot.

---

### Post by kaldor on 2010-06-07
I recommend Wolvix for lightness, but Ubuntu'd run fine on that. I am no fan of Xubuntu at all.

---

### Post by 4Orbs on 2010-06-07
After 3 years of distro hopping, I am completely satisfied with what I consider to be the most solid setup availabe... light but not the lightest... consistently reliable... easy to configure and use... very pretty.

First, install Xubuntu 10.04 and configure it to work it's best. Then install Openbox (window mgr), lxpanel (taskbar), lxappearance (so you can use gtk2 themes), docker (so the network mgr applet has a home on the desktop), Nitrogen (to manage your wallpapers), obmenu (easily modify the Openbox menu), obconf (manage Openbox themes), openbox-xdgmenu (keeps the menu updated when new apps are installed), libxml2-dev (required for the xdg menu to work), openbox-themes (plenty of extra themes for the window mgr), menu (makes the system menu work correctly in lxpanel and openbox)

And here is the code to paste in the terminal to install all the above stuff (except Xubuntu):
```
sudo apt-get install docker menu obmenu lxpanel lxappearance openbox openbox-xdgmenu nitrogen obconf openbox-themes libxml2-dev
```

Then login to the openbox session instead of the xubuntu session and spend a little time configuring the openbox session. All the pieces work together nicely (better than lxde desktop IMHO). Thunar is a near perfect file mgr. And the whole shebang only uses 70 to 80 MB of ram at login time (even with Conky and Cairo-dock running).

This whole setup is very similar to the original Crunchbang Linux, which was fabulous.

And [HERE IS A LINK]("http://urukrama.wordpress.com/openbox-guide/") to an excellent guide for configuring Openbox.

And, to make this even easier for you, here is the autostart.sh to be placed in your .config/openbox folder. The first thing you want to do is open nitrogen and point it to the wallpapers folder - /usr/share/xfce4/backdrops HINT: copy/paste the below into a blank mousepad file and save in your personal home folder as .config/openbox/autostart.sh
```
nitrogen --restore &
docker &
sleep 2 && xscreensaver &
sleep 3 && lxpanel &
#sleep 4 && conky &
#sleep 5 && cairo-dock &
sleep 6 && nm-applet &
```

Configuration tip- lxpanel settings, change the default file mgr to thunar, default terminal to xfce4-terminal, and logout command to killall openbox

And my apologies if you find my enthusiasm excessive. Consider this post as "How to Un-bloat Xubuntu 10.04"

---

### Post by XubuRoxMySox on 2010-06-07
[SIZE="6"][COLOR="Blue"]Xubuntu[/COLOR][/SIZE] is a prettier, simpler, faster Ubuntu in my opinion and experience. Your mileage may vary, as they say. Think of Xfce as "Gnome Lite."

Xubuntu is not "lightweight," **nor is it really meant to be**, as you can read from their own Strategy Document ([here]("https://wiki.ubuntu.com/Xubuntu/StrategyDocument")).

An excerpt from the document:

> Xubuntu does not exclusively target users with low, modest, or high powered machines but instead targets the entire spectrum with a strong focus on enabling lower end machines. Xubuntu's extra responsiveness and speed, among other positive traits, can be appreciated by all users regardless of their hardware.

"Lightweightness" is hardly the only reason that people prefer and use [Xfce]("http://xfce.org"). It's an awesome desktop environment in its own right. Fast, intuitive, responsive, quite configurable, and very pretty. I like the simple applets like weather, analog clock, and Orage calendar; the right-click menu, the Xfce "goodies." Yet faster than Gnome on my machine, but without sacrificing a lot of functionality the way [LXDE]("http://lxde.org") does.

Xubuntu strikes an ideal balance for me, and runs superbly on my old hand-me-down Dell Dimension with it's paltry little 512 megs of RAM.

Really enjoying it,
Robin

---

### Post by IAmAnarch on 2010-06-07
> **Bill Lariviere said:**
> Hi all, i'm absolutely new to Linux/Ubuntu. I'm having lots of typical Windows XP issues on a rather old (2001) computer, and decided to go for (X)Ubuntu. I played around with both live CD's of the latest version, but still can't decide which way to go. Based on my hardware, should i go for Ubuntu (Gnome) or Xubuntu (Xfce)?

Processor    x86 Family 6 Model 4 Stepping 4 AuthenticAMD ~1410 Mhz
BIOS-version/date    Award Software, Inc. ASUS A7A266 ACPI BIOS Revision 1006, 20/08/2001
Physical memory: 512 MB RAM
Video card:   NVIDIA GeForce2 MX/MX 400 64MB
USB 1.0 (no 2.0 support)
35 GB harddisk

Any help would be greatly appreciated!! (i'm totally new to this):)
What I have heard is that even though Xubuntu is designed to be lightweight, it was loaded up with a lot of "features" that caused it to be slightly *more* bloated than its big brother. I use Ubuntu 10.04 on a box that's about the same age (and has similar specs) as yours and it's perfectly fine!

---

### Post by NightwishFan on 2010-06-07
XFCE always seems to show up as using more RAM, but I highly doubt it is 'bloated'. I have built my own ground up systems on Debian using XFCE, and they tend to idle around 300-400mb of RAM. The Fedora XFCE respin has a lot more on it than Xubuntu, it has pulseaudio/selinux etc...

It really is not slow. I also test my machines on limited resources by booting my kernel with: nosmp mem=256m to see how they perform. Debian does far better on 256mb than any stock Ubuntu, but I can still get firefox up.

---

### Post by NUboon2Age on 2010-06-07
> **Bill Lariviere said:**
> Hi all, i'm absolutely new to Linux/Ubuntu. I'm having lots of typical Windows XP issues on a rather old (2001) computer, and decided to go for (X)Ubuntu. I played around with both live CD's of the latest version, but still can't decide which way to go. Based on my hardware, should i go for Ubuntu (Gnome) or Xubuntu (Xfce)?

Processor    x86 Family 6 Model 4 Stepping 4 AuthenticAMD ~1410 Mhz
BIOS-version/date    Award Software, Inc. ASUS A7A266 ACPI BIOS Revision 1006, 20/08/2001
Physical memory: 512 MB RAM
Video card:   NVIDIA GeForce2 MX/MX 400 64MB
USB 1.0 (no 2.0 support)
35 GB harddisk

Any help would be greatly appreciated!! (i'm totally new to this):)

Since I've tried both for someone new and relatively low-resource machine I might recommend Ubuntu Netbook Edition.  it handles low resources well and is not as inscrutable as Xubuntu can be at times.

---

### Post by cgroza on 2010-06-07
> **uRock said:**
> Ubuntu will run poorly with only 512MB RAM. Lubuntu is the lightest and fastest version which runs the LXDE desktop environment. I would recommend giving it a spin. Xubuntu uses almost the same amount of resources as Ubuntu. Do feel free to give them all a try though.


well my ubuntu works well with 256 mb ram...

---

