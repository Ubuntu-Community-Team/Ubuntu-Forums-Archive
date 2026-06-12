---
title: "Minimal Gnome install for server"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by yah.shoor on 2010-04-27
I've run through the Ubuntu install a few times, and I'm starting to get a feel for how I want it set up. There seem to be quite a few different ways to install a GUI, and I'm not sure which one I want. So, I have two questions:

1) How do I keep Gnome from starting whenever I reboot the machine? I'd really rather start it manually with startx, and kill it when I'm done with it. That means that I want gdm, I think, but I have no idea how to install it or set it up in such a way as to force me to invoke the GUI. If we have a power outage and the server is restarted, I want an unfriendly CLI sitting there and blinking, not a friendly GUI. :)

2) Which Gnome package do I want? The only parts I want are the GUI admin tools like synaptic - tools that I would use instead of the command line tools. Should I be installing gnome-core, or just gnome, or gnome-desktop-environment, or what? Is there even a way to tell what a given package contains when I'm sitting downstairs on my Windows machine?

---

### Post by yah.shoor on 2010-04-27
How about 

x-window-system-core 
gnome-core
gnome-system-tools

and NOT gdm

Would that get me what I want? I think it'd install all the stuff under "System -> Administration" but no firefox, audio apps, et cetera.

I'm having a surprisingly hard time finding a website somewhere that lists the contents of each package... I guess that I'm expected to be already in Ubuntu using its tools, right?

---

### Post by yah.shoor on 2010-04-27
> **yah.shoor said:**
> How about 
x-window-system-core 

So, what's this called these days anyways? Am I looking for xorg, or xwindows-xorg, or what?

---

### Post by arrrghhh on 2010-04-27
Why don't you just install ubuntu-server?  It doesn't include X or Gnome, but you don't need that stuff for a server...

Other than that I would recommend doing a minimal install and putting the pieces for a GUI together yourself.  Again, if this is a server you don't want a GUI at all... do you?

---

### Post by yah.shoor on 2010-04-27
I want a server with no GUI - it's been eight years since I used any Linux at all, but that's what I'm happiest with.  My sysadmin who has graciously allowed me to wedge an Ubuntu box in amongst his many Windows servers, really wants a minimal GUI so he can look at users and et cetera without learning how to use the command line. 

I think that all I need is the OpenSSH server package task at install, and a really minimal install of Gnome to keep my sysadmin happy. I'm completely comfortable editing the sshd_config on the command line, but I have no idea what I have to install in order to get my sysadmin the GUI tool "Users and Groups." 

It's been so long for me that I don't even know how to figure out what  GUI bits I need. That's why I'm posting in the Absolute Beginners forum.  Seriously, what's the name of the basic package for X? Is it xorg, or  xserver-xorg, or x-window-system-core? I see plenty of circa-2006  threads advising installation of x-window-system-core, but apparently  the name has been changed? I've found that searching Google with the  names of various packages takes me to packages.debian.org, and I can see  what would depend on xserver-xorg, but I can't tell what is *inside *of  it.

---

### Post by CharlesA on 2010-04-27
I think you can install gnome-core.

```
sudo apt-get gnome core
```

---

### Post by yah.shoor on 2010-04-27
> **CharlesA said:**
> I think you can install gnome-core.

[SIZE=2]That's what I think too, but it's just a guess on my part. 

So, my install looks like:
[/SIZE][SIZE=2]
Step through the installer and choose the OpenSSH server package task
Run [/SIZE][FONT=Courier New][SIZE=2]sudo apt-get update [/SIZE][/FONT][SIZE=2]from the command line right off the bat
Then [/SIZE][FONT=Courier New][SIZE=2]sudo apt-get install gnome-core[/SIZE][/FONT][SIZE=2]
Then [FONT=Courier New]sudo apt-get install [/FONT][/SIZE]  [FONT=Courier New][SIZE=2][FONT=&quot]sysv-rc-conf[/FONT][/SIZE][/FONT]

Then, I can set the runlevel of gdm low enough so that my sysadmin will actually have to type [FONT=Courier New]startx [/FONT]if he wants the GUI. Once again, I'm just guessing that [FONT=Courier New]sysv-rc-conf [/FONT]is the utility I want to keep Gnome from starting.

---

### Post by wojox on 2010-04-27
```
sudo apt-get update && sudo apt-get install xorg gnome-core
```

---

### Post by yah.shoor on 2010-04-27
Cool. I guess I'm going to go to the server room right now. :P

---

### Post by bodhi.zazen on 2010-04-27
better question is what makes you feel you need gnome ( X ) on a server ?

Most if not all the configuration is done via the command line or editing config files.

You can ssh into the server if you need copy-paste functionality.

If you are in need of graphical configuration tools I suggest webmin.

---

### Post by CharlesA on 2010-04-27
Second webmin. I originally used it to set up DHCP, Samba and SSH. Now I just copy the config files to a new install and do it that way.

I think I use SSH for 99% of the stuff I do on my server.

---

### Post by yah.shoor on 2010-04-27
> **bodhi.zazen said:**
> better question is what makes you feel you need gnome ( X ) on a server ?

Most if not all the configuration is done via the command line or editing config files.


Yeah, I am in agreement (although I've never heard of webmin, will look into it). This is what makes me feel like I need X on a server, I've already posted it:

[quote]My sysadmin who has graciously allowed me to wedge an Ubuntu box in  amongst his many Windows servers, really wants a minimal GUI so he can  look at users and et cetera without learning how to use the command  line. [\quote]

I think that webmin might make me happy, but more than anything else I want the guy who's letting me soil his perfect MS-only shop with a -nix server to be happy.

---

### Post by CharlesA on 2010-04-28
What is the purpose of the Ubuntu box going to be?

---

### Post by louieb on 2010-04-28
Lots of minimal GUI threads and posts in [Tutorials & Tips]("http://ubuntuforums.org/forumdisplay.php?f=100") such as ["Ubuntu-Desktop-Minimal"  ck post #121 too]("http://www.uluga.ubuntuforums.org/showthread.php?t=1155961"). 

looks like you got a machine to play with - have fun.

---

