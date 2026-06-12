---
title: "Headless Server won't boot without screen??"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by Joeasaurus on 2009-05-14
Hi, I'm not sure if it should go in this thread so feel free to move me :)

I'm having trouble with my Xubuntu install.
I currently have my Xubuntu as my home server/web server. it has Apache2 and Samba installed and working.
I finally got OpenSSH setup so that i could have my server headless in a cupboard and it works fine once the computer is booted. I have the computer logging in automatically so that i dont have to be there, i just turn it on.
the problem is when i unplug the screen and boot.
after 10 minutes of trying to connect and scratching my head, i plugged the screen back in and was met by a message box telling me that it was running in low graphics mode blah blah.
I'm wondering how to get it to boot as if the screen was there but without a screen plugged in.
I know i'll get murdered for saying it, but Windows would do this with no problems what-so-ever.

Can anyone help me?

---

### Post by BDNiner on 2009-05-14
Because you installed a GUI then you cannot run headless. The boot process checks for a monitor when you have one of the DEs installed. Your best bet if you want to run headless is to install the server edition.

---

### Post by whoop on 2009-05-14
Don't take my word for it, never tried (maybe I never will)  but wouldn't running this make it work also?
Just remove everything xubuntu related.
```

sudo apt-get remove a2ps abiword abiword-common abiword-help abiword-plugin-grammar abiword-plugin-mathview abiword-plugins app-install-data-commercial aumix catfish cupsys-driver-gutenprint exo-utils fortune-mod fortunes-min gigolo gnumeric gnumeric-common gnumeric-doc gnumeric-gtk gpicview gtk2-engines-xfce imagemagick imagemagick-doc latex-xft-fonts libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libdiscid0 libexo-0.3-0 libfftw3-3 libgda3-3 libgda3-bin libgda3-common libgdl-1-0 libgdl-1-common libgdome2-0 libgdome2-cpp-smart0c2a libgoffice-0-6 libgoffice-0-6-common libgoffice-gtk-0-6 libgsf-gnome-1-114 libgtkmathview0c2a liblink-grammar4 libloudmouth1-0 libmad0 libmpcdec3 libnotify-bin libofa0 libots0 librecode0 libt1-5 libtagc0 libthunar-vfs-1-2 libtunepimp5 libwv-1.2-3 libxfce4menu-0.1-0 libxfce4util4 libxfcegui4-4 libxfconf-0-2 link-grammar-dictionaries-en listen mousepad mozilla-thunderbird orage oss-compat psutils python-gnome2-extras python-musicbrainz2 python-mutagen python-ogg python-pymad python-pyogg python-pysqlite2 python-pyvorbis python-tunepimp scim-modules-table scim-tables-additional tango-icon-theme tango-icon-theme-common tcl8.4 thunar thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-thumbnailers thunar-volman thunderbird vim-runtime wdiff xchat xchat-common xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-dict xfce4-dict-plugin xfce4-fsguard-plugin xfce4-governor-plugin xfce4-mailwatch-plugin xfce4-mixer xfce4-mount-plugin xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-places-plugin xfce4-quicklauncher-plugin xfce4-screenshooter xfce4-session xfce4-settings xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfconf xfdesktop4 xfdesktop4-data xfprint4 xfswitch-plugin xfwm4 xfwm4-themes xubuntu-artwork xubuntu-artwork-usplash xubuntu-default-settings xubuntu-desktop xubuntu-docs

```
Maybe remove xorg also. 
Or you could just tell Xubuntu not to start in graphics mode, saves you a complete reinstall.

---

### Post by cariboo on 2009-05-14
The Ubuntu server version is designed to run without a gui, that is why you are having problems. Have a look at this [howto]("http://stevenharman.net/blog/archive/2008/12/13/vnc-to-a-headless-ubuntu-box.aspx"). To use this howto you will need to prevent X from starting. To do this, you should have openssh-server installed. it is available in the repositories. Ssh in to your server, then at the prompt type:

```
sudo /etc/init.d/xdm stop
```

then remove xdm from startup:

```
sudo update-rc.d -F xdm remove
```

Then follow the howto to install vncserver.

---

### Post by BDNiner on 2009-05-14
> **whoop said:**
> Don't take my word for it, never tried (maybe I never will)  but wouldn't running this make it work also?

```

sudo apt-get remove a2ps abiword abiword-common abiword-help abiword-plugin-grammar abiword-plugin-mathview abiword-plugins app-install-data-commercial aumix catfish cupsys-driver-gutenprint exo-utils fortune-mod fortunes-min gigolo gnumeric gnumeric-common gnumeric-doc gnumeric-gtk gpicview gtk2-engines-xfce imagemagick imagemagick-doc latex-xft-fonts libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libdiscid0 libexo-0.3-0 libfftw3-3 libgda3-3 libgda3-bin libgda3-common libgdl-1-0 libgdl-1-common libgdome2-0 libgdome2-cpp-smart0c2a libgoffice-0-6 libgoffice-0-6-common libgoffice-gtk-0-6 libgsf-gnome-1-114 libgtkmathview0c2a liblink-grammar4 libloudmouth1-0 libmad0 libmpcdec3 libnotify-bin libofa0 libots0 librecode0 libt1-5 libtagc0 libthunar-vfs-1-2 libtunepimp5 libwv-1.2-3 libxfce4menu-0.1-0 libxfce4util4 libxfcegui4-4 libxfconf-0-2 link-grammar-dictionaries-en listen mousepad mozilla-thunderbird orage oss-compat psutils python-gnome2-extras python-musicbrainz2 python-mutagen python-ogg python-pymad python-pyogg python-pysqlite2 python-pyvorbis python-tunepimp scim-modules-table scim-tables-additional tango-icon-theme tango-icon-theme-common tcl8.4 thunar thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-thumbnailers thunar-volman thunderbird vim-runtime wdiff xchat xchat-common xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-dict xfce4-dict-plugin xfce4-fsguard-plugin xfce4-governor-plugin xfce4-mailwatch-plugin xfce4-mixer xfce4-mount-plugin xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-places-plugin xfce4-quicklauncher-plugin xfce4-screenshooter xfce4-session xfce4-settings xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfconf xfdesktop4 xfdesktop4-data xfprint4 xfswitch-plugin xfwm4 xfwm4-themes xubuntu-artwork xubuntu-artwork-usplash xubuntu-default-settings xubuntu-desktop xubuntu-docs

```

This would remove the XFCE desktop altogether. Do you log into the desktop to manager the server or are you command line only?

---

### Post by R Clemons on 2009-05-14
you shouldn't have to do all that, you should be able to remove the xubuntu desktop and it will remove everything else

---

### Post by kanikilu on 2009-05-14
Supposedly someone was able to get this to work (page 2): [http://ubuntuforums.org/showthread.php?t=618965](http://ubuntuforums.org/showthread.php?t=618965) -- I haven't tried it, though, since my headless servers do not have Xorg, GDM, etc...

Rather than reinstalling, you could just try disabling GDM: [http://www.cyberciti.biz/faq/prevent-xorg-from-starting-in-linux/](http://www.cyberciti.biz/faq/prevent-xorg-from-starting-in-linux/)

---

### Post by whoop on 2009-05-14
> **R Clemons said:**
> you shouldn't have to do all that, you should be able to remove the xubuntu desktop and it will remove everything else
I do not think the xubuntu-desktop meta-package will remove everything. There are a lot of recommends in that package that are installed when you install xubuntu, and not only decencies.
However I do think it is the best (at least the easiest and safest) option to set the machine to not boot in graphical mode at startup.

---

### Post by Joeasaurus on 2009-05-14
WOW!!
Thanks for all the responses guys!!
I understand that its graphical and thats why i cant have it headless. it does make sense.
The only thing is, and you can all laugh hehehe, I have my server on wireless.
I tried setting it up with Ubuntu ServerEdition and i got it installed as far as the network bit and it couldnt find my network.
It happens like this every time I try to access the network from a CLI

I went with graphical just coz the network connections work that way.

does any of that make sense??

[EDIT] also, the other point of it being graphical is so i can have it autologin. simply coz it won't connect to the wireless until its logged in. Thus meaning i cant ssh and login coz it won't be connected to the network yet..

---

### Post by Dragonbite on 2009-05-14
Isn't there something about running X over SSH?  You would need some X server and DE/Window manager I would suppose so may not want to remove Xfce (et. al) but just turn it off?

---

### Post by Joeasaurus on 2009-05-14
> **Dragonbite said:**
> Isn't there something about running X over SSH?  You would need some X server and DE/Window manager I would suppose so may not want to remove Xfce (et. al) but just turn it off?

That sounds good. If it would still boot, autologin and connect to my network??

---

### Post by Dragonbite on 2009-05-14
> **Joeasaurus said:**
> That sounds good. If it would still boot, autologin and connect to my network??

Why does it have to autologin?  If you are running services, then they should run without logging in.  For example, I have a shared printer hooked up to my desktop. It doesn't have to log in, just be up-and-running at the login screen and my laptop can print to it over the network.

Likewise, the system should be able to auto-connect to the network, shouldn't it? In the above example, once it's on it's available.  

The only thing I need to do (don't HAVE to, but it causes headaches) is to give my desktop a static IP address so I can SSH into it from the laptop if I need.

That's how I connect to my Ubuntu Server (8.04) that I have set up as a headless server (file/web).

---

### Post by Joeasaurus on 2009-05-14
> **Dragonbite said:**
> Why does it have to autologin?  If you are running services, then they should run without logging in.  For example, I have a shared printer hooked up to my desktop. It doesn't have to log in, just be up-and-running at the login screen and my laptop can print to it over the network.

Likewise, the system should be able to auto-connect to the network, shouldn't it? In the above example, once it's on it's available.  

The only thing I need to do (don't HAVE to, but it causes headaches) is to give my desktop a static IP address so I can SSH into it from the laptop if I need.

That's how I connect to my Ubuntu Server (8.04) that I have set up as a headless server (file/web).

hmmmm
Ive just tested it out and it seems the err is in the ssh
i can get to my website while its logged out, so it must be connected, but I can't ssh into it :S
so if we can get that sorted, then i have no qualms in installing Ubuntu Server again and stopping wasting your time hehehe

---

### Post by Dragonbite on 2009-05-14
> **Joeasaurus said:**
> hmmmm
Ive just tested it out and it seems the err is in the ssh
i can get to my website while its logged out, so it must be connected, but I can't ssh into it :S
so if we can get that sorted, then i have no qualms in installing Ubuntu Server again and stopping wasting your time hehehe

You have SSH-Server installed and running?

I've had luck using the "[[COLOR="Blue"]The Perfect Server[/COLOR]]("http://www.howtoforge.org/perfect-server-ubuntu8.04-lts")" series on HowToForge.org. It's going to go into much further detail about installing and using Ubuntu Server, but you should be able to gleam off some information regarding getting it set up with SSH, etc.

---

### Post by Joeasaurus on 2009-05-14
> **Dragonbite said:**
> You have SSH-Server installed and running?

I've had luck using the "[[COLOR=Blue]The Perfect Server[/COLOR]]("http://www.howtoforge.org/perfect-server-ubuntu8.04-lts")" series on HowToForge.org. It's going to go into much further detail about installing and using Ubuntu Server, but you should be able to gleam off some information regarding getting it set up with SSH, etc.

Awesome, I'll try it out and get back to you guys in the next coupla guys.

Thanks for your help Everyone, Especially Dragonbite :)

---

### Post by Joeasaurus on 2009-05-17
> **Joeasaurus said:**
> Awesome, I'll try it out and get back to you guys in the next coupla guys.

Thanks for your help Everyone, Especially Dragonbite :)

ok so im back after trying out that guide.

It's a pretty good guide i must say and thank you to Dragonbite for the reference.

I installed Ubuntu Server Edition (8.10) and it went swimmingly until it tried to detect my wireless. Im using a Cisco Aironet PCI card so i was expecting it to work, but just like the last time i tried it, it failed to see m,y network.

This forced me into a massive row with my parents while i tried to convince them to let me put the server into their room (where MY router is. God they suck). You'll all say why not o that in the first place, but the point was, I was avoiding the inevitable arguement.

But anyways, that aside, the server is now on a wired connection to my router and working perfectly :D

Thanks to Everyone for your quick and useful responses :)

---

