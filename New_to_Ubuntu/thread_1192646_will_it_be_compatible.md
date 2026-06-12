---
title: "will it be compatible"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by orky7 on 2009-06-20
hi my old comp config is P-III, intel 810 motherboard and 120 mb ram(to be exact) will xubuntu 8.04 or 8.10 run smoothly or close to smoothness with my RAM yup they say min requirement is 128 MB RAM but i don't want to work in a slow or hang sort of environment........and if there is some other distro that work fine with my config. but easy to install application like xubuntu please do me know...
thank u.....

---

### Post by shifty_powers on 2009-06-20
i think it will suffer with 120mb ram.

you could always install it and replace xfce with something like icewm...

---

### Post by oldos2er on 2009-06-20
Try either Puppy Linux or Damn Small Linux.

---

### Post by orky7 on 2009-06-20
ok first how to replace xfce with icewn and can i install debian packages in damn small linux and puppy.....

can i use lenny + Xfce for 120 mb ram...

---

### Post by halitech on 2009-06-20
current versions of xubuntu will die on those specs. DSL or puppy will be better. Puppy uses its own package manager, DSL is supposed to be a debian install if you do it to hard drive.

you can try the info here and replace XFCE with LXDE 

[http://forums.debian.net/viewtopic.php?t=26566](http://forums.debian.net/viewtopic.php?t=26566)

---

### Post by orky7 on 2009-06-20
@hailtech ---u r using lenny +xfce in ur 98 mb ram lappy so can i do it...and where do i get lenny+xfce pre installed as lenny come only with kde or/and gnome i think.....

---

### Post by snowpine on 2009-06-20
Hi Orky, I also would recommend Debian Lenny over Xubuntu for your hardware. You can install Debian with Xfce or LXDE by using this disc: [http://cdimage.debian.org/debian-cd/5.0.1/i386/iso-cd/debian-501-i386-xfce+lxde-CD-1.iso](http://cdimage.debian.org/debian-cd/5.0.1/i386/iso-cd/debian-501-i386-xfce+lxde-CD-1.iso)

Here is some interesting reading material about Debian Xfce vs. Xubuntu:
[http://distrowatch.com/weekly.php?issue=20090427#feature](http://distrowatch.com/weekly.php?issue=20090427#feature)
[http://distrowatch.com/weekly.php?issue=20090504#feature](http://distrowatch.com/weekly.php?issue=20090504#feature)

---

### Post by orky7 on 2009-06-20
thanks snowpine i will try this one.....

---

### Post by halitech on 2009-06-21
thanks snowpine, I was away overnight so didn't get a chance to reply.

orky7, that #2 laptop keeps getting bounced around with a few low spec distros but I found Debian Lenny with LXDE runs a little better, just sucks it will only do 800x600 :(

---

### Post by boof1988 on 2009-06-21
> **orky7 said:**
> hi my old comp config is P-III, intel 810 motherboard and 120 mb ram(to be exact) will xubuntu 8.04 or 8.10 run smoothly or close to smoothness with my RAM yup they say min requirement is 128 MB RAM but i don't want to work in a slow or hang sort of environment........and if there is some other distro that work fine with my config. but easy to install application like xubuntu please do me know...
thank u.....

Here is another option if you (or anyone else who finds this thread) is interested.

I'm using Juanty (Ubuntu 9.04) since I know that it has LXDE in the repositories.  This installation process will use the LXDE Desktop (on Ubuntu) which should be able to run on your system.  Alternatively... one could use the [LXDE LiveCD](http://lxde.org/download), which might use different repositories.  *dunno*

[LIST=1]
[*]Ensure you network cable is plugged in and *hope* your network card is supported.
[*]Acquire (or obtain) the *ubuntu-9.04-alternate-i386.iso* on your preferred media.
[*]Boot the CD (or your preferred media) and choose your language.
[*]Press <F4> to bring up the installation "Modes" menu.
(SEE: ChooseCLIInstallation.png)
[*]Select "Install a command-line system" and press <Enter>.
[*]Make sure that "Install Ubuntu" is still selected and press <Enter>.
(SEE: InstallUbuntu.png)
[*]Follow the prompts to install a Ubuntu CLI OS.
[*]After installation and reboot, login to the CLI using your *username* and *password*.  This should bring you to a command-line-interface.
[*]To add the *ubuntu-9.04-alternate-i386.iso* disk as a repository, ensure it is in the CD-drive and then type the following and press <Enter>.
```
sudo apt-cdrom add
```
[*]Type your *password* (it will not be shown on the screen, not even any "*"'s will be shown) and press <Enter>.
[*]To make sure that the repositories are updated properly, type the following and press <Enter>.
```
sudo apt-get update
```
[*]To install the LXDE desktop, type the following and press <Enter>.  (It may take awhile to complete)
```
sudo apt-get install lxde xinit
```
[*]To start the LXDE desktop environment type the following and press <Enter>.
```
startx
```
[/LIST]

The LXDE (GUI) desktop environment (very basic system with network, leafpad and file browser) should now be started.

Note: In my VirtualBox, this installation (up to this point) uses about 50MB RAM.  Your mileage may vary.

Once this is completed, additional packages can be added using (in a terminal)...

To install <packagename> via the terminal:
```
sudo apt-get install <packagename>
```

-or-

To use aptitude (a terminal-based package installer:
```
sudo aptitude
```

-or-

To install a package-management GUI (like [Synaptic](http://packages.ubuntu.com/jaunty/synaptic)):

```
sudo apt-get install synaptic
```

I checked the memory usage after installation of *synaptic* and it didn't seem to go up much (if any).

Attached is (also) a screenshot of the LXDE Desktop.
(SEE: LXDE.Desktop.png)

Hope this helps a bit.

---

### Post by LewRockwell on 2009-06-21
running DSL on a 1997 Gateway laptop with a 150mhz processor, 224mb ram, 3gb drive, PCMCIA lan card

---

