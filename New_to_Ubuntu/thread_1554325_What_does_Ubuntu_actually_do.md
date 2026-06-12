---
title: "What does Ubuntu actually do?"
date: 2010-08-16
forum: New to Ubuntu
---

### Post by bunburya on 2010-08-16
[FONT=&quot][FONT=Arial][SIZE=2]This is a very noob question. Basically I am wondering what features of Ubuntu are attributable to the DE used and what are attributable to Ubuntu itself. I currently run Gnome on Ubuntu and I really like it, but am considering moving to Arch to try it out. If I switched I would probably run Gnome on Arch. I know that Ubuntu and Arch use different package managers and installation managers, but apart from that what would be the main difference to the user?[/SIZE][/FONT][/FONT]

---

### Post by 29732 on 2010-08-16
umm, i see that you made 3 threads talking about the same thing



and what are you talking about??
all these abbreviations are too hard for me >.<

---

### Post by jtarin on 2010-08-16
Ubuntu allows you to engage in your OCD!
Ubuntu allows you to engage in your OCD!
Ubuntu allows you to engage in your OCD!
Ubuntu allows you to engage in your OCD!
Ubuntu allows you to engage in your OCD!
Ubuntu allows you to engage in your OCD!
:lolflag:

---

### Post by snowpine on 2010-08-16
The differences between Ubuntu and Arch are very big when you first install, then almost trivial for a few months, and then big again when Ubuntu comes out with a new release and Arch just keeps rolling.

Unless there is a specific difference/feature that requires you to switch to Arch, I'd just stick with Ubuntu.

---

### Post by ankspo71 on 2010-08-16
Hi,
The first major difference between Ubuntu and Arch, is there is no desktop installed on Arch. ;) If customizing your own desktop is what you are wanting to do, it is possible to do that with an ubuntu mini cd too, which also has no desktop when first installed.

> What does Ubuntu actually do?
Well, I find it can do more for me than most other distributions because of the large amount of packages in the repositories. Most people don't have my taste in choice of applications though, so for other people the differences in size of repositories won't matter as much.

> Basically I am wondering what features of Ubuntu are attributable to the DE used and what are attributable to Ubuntu itself.
The things that separate the 'ubuntu-desktop' package from other gnome desktops in other distributions is: Ubuntu is trying to make the Gnome desktop more user friendly, and the Ubuntu developers have created some of the software for their own desktop such as 'Ubuntu One', 'Ubuntu Software Center/Store', etc. LinuxMint (based on Ubuntu) has also done the same with their own Mint software. Every linux distribution is going to have some differences on the desktop, mostly the their choice in default applications and themes, but as far as the Gnome applications go, they are essentially the same across every distribution.
Hope this helps.

Edited: I came back to elaborate on my post ;)

---

### Post by bunburya on 2010-08-17
First of all sorry for posting it three times, whenever I posted it it wouldn't show up for some reason.

Second, thanks for the advice. So take Evolution for example, that is a Gnome app and not an Ubuntu app right? Would I still be able to use it if I switched to Gnome on Arch?

The main reason I'm thinking about switching to Arch is just to learn a bit more about Linux. I just wanna try something with a little steeper learning curve, but i wouldn't have the time for Gentoo or LFS.

---

### Post by snowpine on 2010-08-17
> **bunburya said:**
> First of all sorry for posting it three times, whenever I posted it it wouldn't show up for some reason.

Second, thanks for the advice. So take Evolution for example, that is a Gnome app and not an Ubuntu app right? Would I still be able to use it if I switched to Gnome on Arch?

The main reason I'm thinking about switching to Arch is just to learn a bit more about Linux. I just wanna try something with a little steeper learning curve, but i wouldn't have the time for Gentoo or LFS.

No problem; we had some database problems on the forum the other day--the multi-post was not your fault. 

Evolution is the same in Ubuntu and Arch. All of the apps are. The everyday experience of using the computer is the same.

Some people think the process of installing Arch teaches you "more about Linux" than installing Ubuntu because you are forced to use the command line. However, Ubuntu has a command line too (Applications, Accessories, Terminal) so don't feel there aren't plenty of fun advanced projects you can do in Ubuntu too. :) 

Furthermore Ubuntu also has a minimal installer (even though most people don't use it) if you are interested: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

To recap, the differences between distros are not the applications or the everyday experience of using them; it is in how you do the original install and how you maintain the system over time (package manager, support cycle, rolling vs. snapshot release, etc.)

---

### Post by muteXe on 2010-08-17
Slackware. Tis good. You will learn some linux with that.

---

### Post by Zorgoth on 2010-08-17
Indeed you are correct.

Like any Linux distro, most of what Ubuntu is is a collection of other projects.  The only things that I can think of off the top of my head that are "Ubuntu apps" would be the particular package manager, the System>Adiminstration>Hardware Drivers GUI, and Ubuntu One.

Well and of course Ubuntu makes its own tweaks to things.  Like the hardware support loaded into the kernel will be different.

---

### Post by bunburya on 2010-08-17
Thanks for the help everyone. Given that I've been using Ubuntu for a while now I probably should have known the answer to this but I never really thought about it!

Slackware is another distro I've been looking into. I'm not sure what I'll do. Basically I wanna try out something a bit more "difficult" while not over-burdening myself given that I've a busy year of college ahead. Sure I'll give Arch or Slack a go and if I really prefer Ubuntu I'll be back in time for Maverick!

---

### Post by LowSky on 2010-08-17
Some things are much easier in Ubuntu. For example: 

In Ubuntu to get proprietary drivers to work like wireless or graphics there is a an app for that. Arch doesn't. Have fun search down the install procedures some devices are more annoying than others.

Ubuntu uses a customized version of Gnome, Arch uses the vanilla version if it uses Gnome at all. The location of installed Applications and settings are in different locations and can be sometimes confusing to a new Arch user who comes from Ubuntu. Remember Arch uses the KISS ideology so it comes without a GUI. 

Arch's package manager pacman is command line based, and there are not many options for a GUI version, most I hear are not so good, but then again this is coming from people who probably like CLI. Ubuntu has 2 graphical options for application searching and a command line interface.

Ubuntu also has access to .deb files. which means you can install many applications in just a few clicks if they are not in the repos. Arch doesn't is own file extension and packages that are not in the repos will need to be installed by hand. Learn to use 'make'.

Arch uses root by default but Sudo can be used if a user wishes. Ubuntu uses Sudo with the root account disabled by default.

With Ubuntu moving toward a more internet friendly environment I find it is losing customization at least on the level I was used to in the old days. Arch can be set up any which way you like right from the start.

On my own computer I keep flirting with Arch but always come back to Ubuntu.

---

### Post by kwacka on 2010-08-17
just as you can dual boot with Windows and Ubuntu, you can dual-boot with ubuntu & Arch(or Slackware, or (if you really want to get your hands dirty 'linux from scratch').

Another alternative would be a virtual machine running under (e.g.) Virtualbox.

With either you retain your original setup for college work whilst also having a system to play around with.

If you really want to get deeper into command line, download and/or install RUTE (Rute Users Tutorial & Exposition) [from here]("http://rute.2038bug.com/index.html.gz") or sudo apt-get install rutebook

---

### Post by KdotJ on 2010-08-17
Just for thought, you could ways install Arch as a VM in a virtualisation program such as VirtualBox. This is what I did and it works great however the downside to running it (or many other distros) in a VM is that you don't have to fiddle with drivers and getting the correct things installed, which may be part of the "fun" and learning that you may be after. 
This VM option may be a good idea though if you don't want to possibly mess up everything with Arch and have no working OS until you either fix it or reintall ubuntu. Or do it all in a VM and then do it all for real once you've got the hang of Arch

---

### Post by bance on 2010-08-17
Thanks, 

Interesting thread......... Might try some of this stuff myself !

---

### Post by andrew.46 on 2010-08-20
Hi bunburya,

> **bunburya said:**
> Slackware is another distro I've been looking into. I'm not sure what I'll do. Basically I wanna try out something a bit more "difficult" while not over-burdening myself given that I've a busy year of college ahead.

The 'difficulty' of slackware is often overstated, a full installation gives a working system pretty quickly and the amazing slackbuilds.org fills in any gaps. The community is very different from Ubuntu though...

Andrew

---

### Post by jtarin on 2010-08-20
> **andrew.46 said:**
> Hi bunburya,



The 'difficulty' of slackware is often overstated, a full installation gives a working system pretty quickly and the amazing slackbuilds.org fills in any gaps. The community is very different from Ubuntu though...

AndrewOften overstated by "by people new to Linux". Coming from a GUI world and delving into the command line and editing is not everyone's cup of java. The stability of Slackware is often understated though. Slackware's deault is to run as root so you'd better be up on your sysadmin skills or you could bork your system fast,  but once learned the skills will stay with you.

---

### Post by jdong on 2010-08-20
One thing that Ubuntu does that Arch and Slackware tend not to, is to pre-configure "bundled" projects in a way that provides a positive out-of-the-box configuration for the typical user. This is something that some seasoned veterans dislike -- for example, opening XChat will connect you to Ubuntu's IRC servers and support channel, rather than popping up a "Configure your nickname and choose a server" dialog that the upstream stock version does.

---

