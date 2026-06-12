---
title: "Is 512MB RAM enough to run Ubuntu?"
date: 2011-03-29
forum: New to Ubuntu
---

### Post by brawnypandora0 on 2011-03-29
If not, should I get lubuntu instead?

---

### Post by Dutch70 on 2011-03-29
> **brawnypandora0 said:**
> If not, should I get lubuntu instead?

1GB is recommended on the link below.
[[COLOR="Blue"]https://help.ubuntu.com/community/Installation/SystemRequirements[/COLOR]]("https://help.ubuntu.com/community/Installation/SystemRequirements")

Xubuntu may be a better option. You can find more info on Xubuntu & Lubuntu on that link also.

You can also add the Lubuntu desktop environment to Xubuntu and choose which to login to at the login screen.
It's just about 1 command to add it.

With that amount of RAM, read this before creating your swap partition. 
[[COLOR="Blue"]https://help.ubuntu.com/community/SwapFaq[/COLOR]]("https://help.ubuntu.com/community/SwapFaq")

---

### Post by mastablasta on 2011-03-29
yes 512MB is enough to run Ubuntu. In fact it runs on as little as 256 MB ram (depends also on the processor) . but as suggested a lighter weight DE might run even faster (xubuntu, Lubuntu).

---

### Post by brawnypandora0 on 2011-03-29
1GB recommended!?!?! Does that mean in future years, it'll become 2GB recommended?

---

### Post by Grenage on 2011-03-29
> **brawnypandora0 said:**
> 1GB recommended!?!?! Does that mean in future years, it'll become 2GB recommended?

Yes; Ubuntu is not a minimalist OS, it's a modern 'average-user'-orientated OS.

---

### Post by brawnypandora0 on 2011-03-29
When will the minimum RAM requirement hit a ceiling?

---

### Post by Grenage on 2011-03-29
> **brawnypandora0 said:**
> When will the minimum RAM requirement hit a ceiling?

Probably not in our lifetime, it's been steadily increasing for decades!

---

### Post by Paqman on 2011-03-29
It'll run ok on 512MB, but you'll have to be careful about what apps you run. There are lightweight equivalents to a lot of stuff:

Open Office = Abiword & Gnumeric or an online package like Google Docs or Zoho (install [webservice-office-zoho](apt:webservice-office-zoho) for Zoho integration)
Evolution = Webmail (install the package [desktop-webmail](apt:desktop-webmail))
GIMP = pixlr.com

I'm sure other people have more good suggestions. You should also go to System > Prefs > Startup Applications and uncheck anything you're not using, and make sure you've got some swap space, about 1GB should be plenty.

---

### Post by Dutch70 on 2011-03-29
> **brawnypandora0 said:**
> When will the minimum RAM requirement hit a ceiling?

> **Grenage said:**
> Probably not in our lifetime, it's been steadily increasing for decades!

:lolflag:

---

### Post by brawnypandora0 on 2011-03-29
How do I know which ones to uncheck? Even opening up Firefox or My Documents is unbearably slow--at least ten seconds wait. I guess I have no choice but to switch to lubuntu.

Is it possible to directly switch from Ubuntu to lubuntu without doing a reformat? I have 60GB worth of files on my laptop and my USB 1.0 flash drive is only 1GB capacity. I don't want to transfer everything over to my desktop, do a format, and then transfer everything back to my laptop.

---

### Post by Grenage on 2011-03-29
> **brawnypandora0 said:**
> How do I know which ones to uncheck? Even opening up Firefox or My Documents is unbearably slow--at least ten seconds wait.

Things like Bluetooth and Remote Desktop aren't usually necessary.  What kind of RAM does your computer take, and where are you based?

---

### Post by Grenage on 2011-03-29
> **brawnypandora0 said:**
> How do I know which ones to uncheck? Even opening up Firefox or My Documents is unbearably slow--at least ten seconds wait. I guess I have no choice but to switch to lubuntu.

Is it possible to directly switch from Ubuntu to lubuntu without doing a reformat? I have 60GB worth of files on my laptop and my USB 1.0 flash drive is only 1GB capacity. I don't want to transfer everything over to my desktop, do a format, and then transfer everything back to my laptop.

You can probably just install lubuntu-desktop from a terminal.

---

### Post by Dutch70 on 2011-03-29
You can also probably find lubuntu-desktop and/or xubuntu-desktop in synaptic package manager.

---

### Post by Paqman on 2011-03-29
> **brawnypandora0 said:**
> How do I know which ones to uncheck?


Anything you're not actually using. For example, if you aren't visually impaired, then you don't need Visual Assistance, and if you aren't using Evolution then you can uncheck that.

> 
Is it possible to directly switch from Ubuntu to lubuntu without doing a reformat? I have 60GB worth of files on my laptop and my USB 1.0 flash drive is only 1GB capacity. I don't want to transfer everything over to my desktop, do a format, and then transfer everything back to my laptop.

Yes, paste the following command into a terminal window, then reboot:

```
sudo apt-get remove acpi-support acpid adium-theme-ubuntu aisleriot alacarte app-install-data app-install-data-partner apt-xapian-index apturl apturl-common at-spi avahi-autoipd avahi-daemon baobab binfmt-support binutils bluez-alsa bluez-cups bluez-gstreamer bogofilter bogofilter-bdb bogofilter-common branding-ubuntu brasero brasero-cdrkit brasero-common brltty brltty-x11 byobu capplets-data checkbox checkbox-gtk cli-common compiz compiz-core compiz-fusion-plugins-main compiz-gnome compiz-plugins compizconfig-backend-gconf computer-janitor computer-janitor-gtk couchdb-bin cups-bsd dc desktopcouch dmz-cursor-theme doc-base docbook-xml dvd+rw-tools empathy empathy-common eog erlang-base erlang-crypto erlang-inets erlang-mnesia erlang-public-key erlang-runtime-tools erlang-ssl erlang-syntax-tools erlang-xmerl espeak espeak-data evolution evolution-common evolution-couchdb evolution-data-server evolution-data-server-common evolution-exchange evolution-indicator evolution-plugins evolution-webcal example-content exiv2 fancontrol file-roller firefox firefox-branding firefox-gnome-support foo2zjs foomatic-db-compressed-ppds foomatic-db-engine foomatic-filters gbrainy gcalctool gcc gcc-4.4 gconf-defaults-service gconf-editor gdm gdm-guest-session gedit gedit-common genisoimage ghostscript-x gnome-about gnome-accessibility-themes gnome-applets gnome-applets-data gnome-codec-install gnome-control-center gnome-desktop-data gnome-dictionary gnome-doc-utils gnome-games-common gnome-mag gnome-mahjongg gnome-media gnome-media-common gnome-menus gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-screensaver gnome-screenshot gnome-search-tool gnome-session gnome-session-bin gnome-session-canberra gnome-session-common gnome-settings-daemon gnome-sudoku gnome-system-log gnome-system-monitor gnome-terminal gnome-terminal-data gnome-themes-selected gnome-themes-ubuntu gnome-user-guide gnome-utils gnome-utils-common gnomine gstreamer0.10-alsa gstreamer0.10-gnonlin gstreamer0.10-plugins-base-apps gstreamer0.10-pulseaudio gstreamer0.10-tools gtk2-engines-murrine gucharmap guile-1.8-libs gvfs-backends gwibber gwibber-service hpijs hplip hplip-cups hplip-data humanity-icon-theme ibus ibus-gtk ibus-pinyin ibus-pinyin-db-android ibus-pinyin-db-open-phrase ibus-table im-switch indicator-applet indicator-applet-session indicator-application indicator-me indicator-messages indicator-session indicator-sound inputattach kerneloops-daemon launchpad-integration lftp libappindicator0.1-cil libarchive1 libart2.0-cil libasound2-plugins libatspi1.0-0 libavahi-core7 libavahi-gobject0 libbrasero-media1 libbrlapi0.5 libc-dev-bin libc6-dev libcairo-perl libcairomm-1.0-1 libcamel1.2-14 libcanberra-pulse libclutter-1.0-0 libclutter-gtk-0.10-0 libcolamd2.7.1 libcompizconfig0 libcouchdb-glib-1.0-2 libcrypt-passwdmd5-perl libcryptui0 libcurl3 libdaemon0 libdconf0 libdecoration0 libdesktopcouch-glib-1.0-2 libdigest-sha1-perl libdmapsharing2 libdotconf1.0 libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-7 libedataserver1.2-13 libedataserverui1.2-8 libegroupwise1.2-13 libespeak1 libevolution libexempi3 libexiv2-6 libfile-copy-recursive-perl libfolks-telepathy0 libfolks0 libfreezethaw-perl libgail-common libgail-gnome-module libgconf2.0-cil libgd2-xpm libgdata-common libgdata-google1.2-1 libgdata1.2-1 libgdata7 libgdict-1.0-6 libgee2 libgexiv2-0 libglade2.0-cil libgladeui-1-9 libglib-perl libglib2.0-cil libglib2.0-data libglibmm-2.4-1c2a libgmime-2.4-2 libgmime2.4-cil libgnome-mag2 libgnome-media0 libgnome-menu2 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2-canvas-perl libgnome2-perl libgnome2-vfs-perl libgnome2.24-cil libgnomekbd-common libgnomekbd4 libgnomepanel2.24-cil libgnomevfs2-extra libgoocanvas-common libgoocanvas3 libgpod-common libgpod4 libgraphite3 libgsl0ldbl libgtk-vnc-1.0-0 libgtk2-perl libgtk2.0-cil libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml3.14-19 libgtkmm-2.4-1c2a libgtksourceview2.0-0 libgtksourceview2.0-common libgucharmap7 libgweather-common libgweather1 libgwibber0 libhpmud0 libhyphen0 libibus2 libido-0.1-0 libindicate-gtk2 libindicate4 libjs-jquery liblaunchpad-integration1.0-cil liblouis-data liblouis2 libmetacity-private0 libmission-control-plugins0 libmldbm-perl libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo2.0-cil libmono-corlib2.0-cil libmono-i18n-west2.0-cil libmono-management2.0-cil libmono-posix2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-system2.0-cil libmtp8 libmusicbrainz4c2a libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libnss-mdns libopencc1 libpam-ck-connector libpam-gnome-keyring libpango-perl libpangomm-1.4-1 libportaudio2 libprotobuf6 libprotoc6 libpulse-browse0 libpulse-mainloop-glib0 librarian0 librasqal2 librdf0 libsane-hpaio libsctp1 libsdl1.2debian-pulseaudio libsensors4 libsigc++-2.0-0c2a libsnmp-base libsnmp15 libspeechd2 libspeexdsp1 libstlport4.6ldbl libsyncdaemon-1.0-1 libtelepathy-farsight0 libtelepathy-glib0 libtelepathy-logger1 libtotem-plparser17 libubuntuone-1.0-1 libuuid-perl libvala-0.10-0 libwmf0.2-7-gtk libxklavier16 libxml2-utils libxp6 light-themes linux-libc-dev lksctp-tools lm-sensors lp-solve manpages-dev media-player-info metacity metacity-common min12xxw mono-2.0-gac mono-csharp-shell mono-gac mono-gmcs mono-runtime mousetweaks mscompress mtools nautilus nautilus-data nautilus-sendto nautilus-sendto-empathy nautilus-share network-manager-pptp network-manager-pptp-gnome notify-osd notify-osd-icons onboard openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-emailmerge openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress openoffice.org-math openoffice.org-style-galaxy openoffice.org-style-human openoffice.org-writer openprinting-ppds pinyin-database pitivi pkg-config plymouth-theme-ubuntu-logo pnm2ppa protobuf-compiler pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-x11 pulseaudio-utils pxljr python-appindicator python-argparse python-avahi python-brlapi python-configglue python-couchdb python-crypto python-desktopcouch-records python-egenix-mxdatetime python-egenix-mxtools python-farsight python-gmenu python-gnomeapplet python-gnomekeyring python-gst0.10 python-gtksourceview2 python-gtkspell python-ibus python-imaging python-indicate python-launchpad-integration python-libproxy python-louis python-mako python-markupsafe python-newt python-openssl python-pam python-papyon python-pexpect python-protobuf python-pyatspi python-pycurl python-pygoocanvas python-pyinotify python-rdflib python-serial python-speechd python-telepathy python-twisted-bin python-twisted-core python-twisted-names python-twisted-web python-ubuntuone python-ubuntuone-client python-ubuntuone-storageprotocol python-uno python-virtkey python-wnck python-xapian quadrapassel radeontool rarian-compat rdesktop rhythmbox rhythmbox-plugin-cdrecorder rhythmbox-plugins rhythmbox-ubuntuone-music-store rtkit samba-common samba-common-bin sane-utils screen screen-resolution-extra screensaver-default-images scrollkeeper seahorse sessioninstaller sgml-data shotwell smbclient software-center speech-dispatcher splix ssh-askpass-gnome syslinux syslinux-common telepathy-butterfly telepathy-gabble telepathy-haze telepathy-idle telepathy-logger telepathy-mission-control-5 telepathy-salut tomboy toshset totem totem-common totem-mozilla totem-plugins tsclient ttf-indic-fonts-core ttf-kacst-one ttf-khmeros-core ttf-lao ttf-opensymbol ttf-punjabi-fonts ttf-takao-pgothic ttf-thai-tlwg ubufox ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-mono ubuntu-sounds ubuntu-sso-client ubuntu-system-service ubuntu-wallpapers ubuntuone-client ubuntuone-client-gnome uno-libs3 update-inetd ure usb-creator-common usb-creator-gtk vinagre vino whois wodim x-ttcidfont-conf xcursor-themes xdg-user-dirs-gtk xfonts-mathml xscreensaver-gl xsltproc xul-ext-ubufox xulrunner-1.9.2 yelp zenity && sudo apt-get install lubuntu-desktop

```

---

### Post by brawnypandora0 on 2011-03-29
> **Grenage said:**
> Things like Bluetooth and Remote Desktop aren't usually necessary.  What kind of RAM does your computer take, and where are you based?

DDR RAM What does where am I based mean? I bought my computer in 2001 and I never intend to upgrade (I don't like spending money on electronics since I only use my computer for homework and very basic tasks), so I hope Linux's slimmed down operating systems never increase their memory requirements.

---

### Post by brawnypandora0 on 2011-03-29
WOw that's a really long command. So after I reboot, will all my settings be intact? For example, my saved passwords in Firefox and all my bookmarks wouldn't all of a sudden get deleted right?

---

### Post by Paqman on 2011-03-29
> **brawnypandora0 said:**
> DDR RAM What does where am I based mean? 

What country are you in?


> I hope Linux's slimmed down operating systems never increase their memory requirements.

While there will always be distros that specialise in lightweight desktops, you should expect that in general the hardware requirements of all software will trend upwards. The problem is the applications as much as the OS. Linux is generally pretty lightweight compared to Windows or OSX, but a lot of the desktop apps you'll want to run aren't.

Installing more RAM is quick, cheap, extremely easy and would make a huge difference to your machine. 

If you're feeling adventurous doing a minimal install from a command line is pretty much guaranteed to give you a better performing system given your hardware, but even using a script like the one in my sig it's a bit messier than a regular install.

---

### Post by Paqman on 2011-03-29
> **brawnypandora0 said:**
> WOw that's a really long command.

Just copy and paste, you don't need to type it out.

> 
So after I reboot, will all my settings be intact? For example, my saved passwords in Firefox and all my bookmarks wouldn't all of a sudden get deleted right?

Yep. Your settings live in your home folder, and aren't deleted even when you uninstall an app (although you can tell the package manager to do so if you want)

---

### Post by Grenage on 2011-03-29
> **brawnypandora0 said:**
> DDR RAM What does where am I based mean? I bought my computer in 2001 and I never intend to upgrade (I don't like spending money on electronics since I only use my computer for homework and very basic tasks), so I hope Linux's slimmed down operating systems never increase their memory requirements.

I have an old DDR2 4200 laptop RAM, and would have offered it if compatible.

---

### Post by brawnypandora0 on 2011-03-29
My other laptop has Linux Mint. What's the terminal line command to switch from Linux Mint to lubuntu?

---

### Post by mastablasta on 2011-03-29
there are much simpler measures to take than installing a different DE.
 
For example you never said what kind of graphics card you have. it (poor drivers) might be the cause of slow down.
 
Then if you are not useing virutal destkops turn them off. default you have 4 enabled. Then turn off the effects.
 
Firefox 4, Chromium is much faster than FF3.6. So using alternative applications is also an option. but not always. i take it AbiWord has even less compatibility between it and MS Office.
 
As for linux Mint LXDE install (yes they too have an LXDE version) it would be best to ask in linuxmint forums.

---

### Post by Dutch70 on 2011-03-29
> **brawnypandora0 said:**
> My other laptop has Linux Mint. What's the terminal line command to switch from Linux Mint to lubuntu?

Edit: According to Old_Man_Unix, this won't do what you want it to do.
lubuntu-desktop & xubuntu-desktop are in synaptic package manager in Ubuntu. Just open synaptic and search.

---

### Post by Old_Man_Unix on 2011-03-29
> **Dutch70 said:**
> You can also probably find lubuntu-desktop and/or xubuntu-desktop in synaptic package manager.

Our experience come from restoring/rejuvenating 'donated' PCs for non-profits, so that is viewpoint of this response.

Lubuntu is much more than just the desktop.  It is actually a tuned distribution for resource-challenged systems.  So just installing the desktop will not really do the job.  

As many on this thread have attested, running Ubuntu in 512Mb is a painful experience, to put it bluntly.   Many 'favorite' applications that are installed by default will only run slowly, if at all. You might be able to tolerate this poor performance  for yourself, but it isn't something that you would subject someone else to. 

The problem is not just the amount of RAM.  Although that IS a major issue, it can often be rectified for little effort or cost.  The system processor itself may be marginal.  Maybe it is a P3 or a Celeron.  These just don't do a good job with Ubuntu out-of -the-box.

Sure you can tune your system but if you do that to any significant extent, are you still running Ubuntu?

Lubuntu is a well-designed distribution and keeps you in the Ubuntu family - you can use the same repositories, and most of the information on Ubuntu is still applicable.    Most users report they are quite comfortable with the look-and-feel of it. It's the one we install as a matter of routine. 

With 512Mb of RAM and  almost any processor, Lubuntu will perform more than adequately out-of-the box. 

If you willing to leave the family, there are even lighter weight distributions, some of which have been mentioned here.  We have tried them out but we still feel Lubuntu is the way to go.



> **mastablasta said:**
> i take it AbiWord has even less compatibility between it and MS Office.
 


[FONT=Verdana]Abiword is compatible with all the MS Word formats.   It is also compatible with the Open Office/Libreoffice formats for  word processing.  So that isn't an issue.

A *real* issue with Lubuntu as far as office apps were concerned  was that there was no presentation editor.  That has been fixed with the  release of **Ease. **[/FONT]

---

### Post by Old_Man_Unix on 2011-03-29
** <<ignore>>**[FONT=Verdana][/FONT]

---

### Post by vandamme on 2011-03-29
You might try LinuxMint XFCE, which just came out.
[http://blog.linuxmint.com/?p=1708](http://blog.linuxmint.com/?p=1708)
Clem brags about saving 100+ megs of memory, faster, etc. I just downloaded it but I screwed up the install because I have too many partitions (mint 7 & 8) and have no idea where the sam hill the grub configuration file is, so I can't access the new distro. The moral of my story is I'm going to just delete all the other partitions and put one distro on it. 

I also tried Puppy and it's unbelievably fast on my 256M , 6 year old laptop. Unfortunately the wifi drivers won't work. It's fast because it runs in RAM. Give it a shot off the live disk, just for fun.

---

### Post by sea_dawg on 2011-03-29
Like brawnypandora0 I also run older hardware at home.  Though for different reasons.  Computers as all electronics are, are environmentally very dirty, I want to get the longest life that I reasonably can out of any electronics purchase I make.

Until last week my old Gateway desktop was limping along on 512MB.  Upgrading the memory made a HUGE performance difference.  Maverick now zips along very nicely with applications loading quickly.  Swap space is hardly used anymore.

Some thoughts and lessons learned on memory upgrades for my old machine. Because our machines are similar vintage these may apply to your situation. My mother board has 4 memory slots and can address a maximum of 4G of memory.  So that's what I went for, 4 X 1G sticks.  I think I wasted a bit of money.  It looks like Ubuntu, Like Win XP, is able to "see" 2.9G of memory.

More knowledgeable persons may be able to explain this, I can't.

Here are three less expensive paths I could have taken had I understood this. Memory installed in my machine since new were two 256M sticks for a total of 512M.

1 - I could have purchased two more 256M sticks for about $8 - $15 each used thereby doubling my memory to 1G.  In any system, not only computers, if you are up against the limits and can double your capacity you will see a big difference.  This upgrade, though somewhat limiting, would have been the most bang for the buck.

2 - I could have purchased two 512M sticks for slightly more $$ than the two 256M sticks and ended up with 1.5G of memory.

3 - I could have purchased two 1G sticks for half the price of the four that I did purchase, installed them with the existing 256M sticks and ended up with 2.5G of memory, very close to what is now recognized by my system.  That is what I wish I'd done.

I always upgrade / repair this old work horse with used parts.  There is a never ending supply of used parts available at a fraction of their new cost, they work fine and are much greener.  The only exception to this being the HDD.

---

### Post by Paqman on 2011-03-29
> **sea_dawg said:**
> My mother board has 4 memory slots and can address a maximum of 4G of memory.  So that's what I went for, 4 X 1G sticks.  I think I wasted a bit of money.  It looks like Ubuntu, Like Win XP, is able to "see" 2.9G of memory.

More knowledgeable persons may be able to explain this, I can't.


If you'd installed 64-bit you would have access to all your memory. IIRC even recent versions of 32-bit Ubuntu should be able to make some use of all 4GB, due to a hack called PAE. I'm not 100% sure about that, I haven't used 32-bit on anything except netbooks.

Having said that, 4GB of RAM generally is a waste of money on Ubuntu. I have 4GB, and the only time I go anywhere near using it is when I run big fat VMs. I would have been fine even for this with 3GB, but I only have two DDR3 slots.

If you're just using normal desktop apps 1GB is plenty for Ubuntu.

---

### Post by nathan726 on 2011-03-29
> **Paqman said:**
> IIRC even recent versions of 32-bit Ubuntu should be able to make some use of all 4GB, due to a hack called PAE. I'm not 100% sure about that, I haven't used 32-bit on anything except netbooks.

PAE works a charm. I had 1Gb ram and recently upgraded to 4Gb - I installed the PAE kernel and Ubuntu can access the full 4Gb.

---

### Post by sea_dawg on 2011-03-29
Paqman, thank you for the explanation.  I have checked, my machine is not capable of running 64 bit.

Your explanations reaffirm that I did indeed waste $$$ on 4G of memory.  I hope this helps brawnypandora0 choose the correct path in upgrading.

---

### Post by mcduck on 2011-03-29
> **brawnypandora0 said:**
> DDR RAM What does where am I based mean? I bought my computer in 2001 and I never intend to upgrade (I don't like spending money on electronics since I only use my computer for homework and very basic tasks), so I hope Linux's slimmed down operating systems never increase their memory requirements.

Your problem here isn't actually the requirements of the operating system, but instead the fact that the requirements for those basic tasks keep on increasing.

Browsing a web site requires a lot more memory and CPU power today than it required back in 2001. All the flash animations, javascript-heavy sites, dynamic content and multimedia that has become part of the WWW requires much more from your computer, and there's nothing the OS can do about it.

Same goes for text processing and other basic work as well. And the requirements are only going to increase in future. People want prettier things and easier things, and all that will inevitably keep on increasing the requirements for basic every-day computing.

It's absolutely possible to get a nice graphical Ubuntu desktop that only uses 40MB of RAM (my other Ubuntu system is currently using 43MB). You'll still need a *lot* more to run the actual programs and to do the actual tasks you'd want to do with it.

---

### Post by cyberphrog on 2011-03-29
I'm running 10.04 on several PCs that have only 512MB.  These are old windows PCs that I wanted to put back into productive use for family members.  Works fine for a basic Ubuntu platform running typical apps, and makes good re-use of an older machine that would otherwise go to scrap.  If you're into higher-end applications, then obviously mo RAM is mo better!

---

### Post by walt.smith1960 on 2011-03-29
Here are 2 screen shots of a system similar to that under discussion.  I haven't done anything to 'lighten' Ubuntu except remove open office and install Libre Office.  I did install LovingLinux' FlashVideoReplacer plugin which seems to help but video is still choppy.

[ATTACH]187483[/ATTACH]

[ATTACH]187484[/ATTACH]

Nobody is going to mistake one of these systems for a quad core firebreather but it is usable for web browsing & basic office tasks.

---

### Post by sleepingdragon on 2011-03-29
OK. Time to throw the cat amongst the pigeons... what about [Bodhi Linux]("http://www.bodhilinux.com/")? 

It's an Ubuntu base will all the heavy stuff thrown out. They've just got to their 1.0 release and it's based on E17. Looks nice and starts off with a very minimal configuration - even CUPS is given as an optional extra. I got it going nice in 128MB and it should be happy enough with 512MB.

---

### Post by DuckHook on 2011-03-29
I'm very happy with Xubuntu on my 6-year old Dell w/ 512 Mb. I replaced Firefox with Epiphany and fulfill my simple mail needs through webmail. Have had as many as 6 apps running without noticeable lag. Games are slower, but are just as dependant on CPU speed and graphics set as they are on memory. Add System Load Monitor to panel for a quick and dirty idea of CPU/memory/swap load.

---

### Post by DuckHook on 2011-03-29
PAE will see 4 G which is very useful in all sorts of stuff like VMs, Wine, games etc. More RAM never hurts.

---

### Post by 3Miro on 2011-03-29
On 512MB of RAM, I would recommend 32-bit Xubuntu. LXDE is nice too, but it can still be somewhat buggy. I also don't think there is that much difference between the RAM usage between the two.

Ubuntu should run fine though, so long as you don't open too many things at once.

---

### Post by brawnypandora0 on 2011-03-31
> **Dutch70 said:**
> Edit: According to Old_Man_Unix, this won't do what you want it to do.
lubuntu-desktop & xubuntu-desktop are in synaptic package manager in Ubuntu. Just open synaptic and search.

WHat do you mean search? Type in "lubuntu"? I get four results, the bottom one says: lubuntu-desktop version 0.13. Is that the one?

---

### Post by brawnypandora0 on 2011-03-31
Well is it? Two problems:

1) It says it can't be authenticated and may harm my computer

2) How do I know if it will delete/overwrite all the Ubuntu files?

Please answer, I can't wait to get rid of Ubuntu for the faster lubuntu.

---

### Post by Dutch70 on 2011-03-31
LOL ...Looks like you really couldn't wait. :lol:
[[COLOR="RoyalBlue"]http://ubuntuforums.org/showthread.php?p=10620526#post10620526[/COLOR]]("http://ubuntuforums.org/showthread.php?p=10620526#post10620526")

Had I know you were going to forget user your name, I would have been more careful with my suggestions...lol  j/k. 

Glad you got it all worked out.

---

### Post by Rasa1111 on 2011-03-31
My fathers main desktop at his house only has 512 RAM, but runs Ubuntu 10.10 great!

---

### Post by brawnypandora0 on 2011-06-08
Between Xubuntu and Lubuntu, which one is faster? Wikipedia says Lubuntu, but can someone confirm this?

Someone mentioned Bodhi Linux...any other distros faster than both lubuntu and Xubuntu?

---

### Post by brawnypandora0 on 2011-06-08
> **mastablasta said:**
> there are much simpler measures to take than installing a different DE.
 
For example you never said what kind of graphics card you have. it (poor drivers) might be the cause of slow down.
 
Then if you are not useing virutal destkops turn them off. default you have 4 enabled. Then turn off the effects.
 
Firefox 4, Chromium is much faster than FF3.6. So using alternative applications is also an option. but not always. i take it AbiWord has even less compatibility between it and MS Office.
 
As for linux Mint LXDE install (yes they too have an LXDE version) it would be best to ask in linuxmint forums.

What are virtual desktops? How do I turn it off?

---

### Post by brawnypandora0 on 2011-06-09
Where do I go to turn things off?

---

### Post by mastablasta on 2011-06-09
virtual desktops are desktops that exists separatelly from the one you are looking at. think of it like having more monitors on one monitor. 
 
i am not sure where they are turned off in new version but it's usually in one of the desktop settings.

---

### Post by brawnypandora0 on 2011-06-23
Is LXDE ubuntu better or Peppermint OS? Which one comes with more packages pre-installed and which one has better hardware support?

---

### Post by TBABill on 2011-06-23
I believe the latest Peppermint is based on Mint LXDE which is based on Lubuntu....so for the most part their hardware support should be identical. None offer additional hardware support beyond what Lubuntu offers that I'm aware of, but it's been a while since I've looked into Peppermint. Packages pre-installed....no idea but you can go to each's site and compare lists of packages.

---

### Post by nrundy on 2011-06-23
> **brawnypandora0 said:**
> If not, should I get lubuntu instead?

Ubuntu runs fine on my box with just 512mb ram. It runs a lot better than winxp did with 512mb.

---

### Post by dFlyer on 2011-06-23
Ubuntu will run fine with 512 meg. It will run better with more.

---

### Post by curts on 2011-06-24
If you are running a full-up Ubuntu 10.04 or 11.04 with 1 GB RAM or less, you **must** have some swap configured and enabled to not experience degraded performance.  I'm running 1 GB RAM and 2 GB swap.

I experienced this first-hand recently when 11.04 didn't install my existing swap partition correctly and was running without it.  Furthermore, the 11.04 installer messed up the existing swap partition's format, so my 10.04 installation couldn't use it either.  Very painful until I figured out what had happened and got it sorted.

---

### Post by brawnypandora0 on 2011-06-24
> **curts said:**
> If you are running a full-up Ubuntu 10.04 or 11.04 with 1 GB RAM or less, you **must** have some swap configured and enabled to not experience degraded performance.  I'm running 1 GB RAM and 2 GB swap.

I experienced this first-hand recently when 11.04 didn't install my existing swap partition correctly and was running without it.  Furthermore, the 11.04 installer messed up the existing swap partition's format, so my 10.04 installation couldn't use it either.  Very painful until I figured out what had happened and got it sorted.

What's swap?

---

### Post by danbishop on 2011-06-24
Swap is hard drive space allocated for use as RAM (for when you run out). It's obviously much slower than RAM so is only used when it's really needed.

The installer will guide you through setting up swap and in fact will probably even do it automatically depending on what you select.

---

### Post by TBerk on 2011-07-02
Already been answered but I'm going to 'Me Too' in reply...

I run regular Ubuntu on dual core processor systems on a daily basis w/ 1 and 2Gigs of RAM.

But just this last week I cleaned up a WinXP installation on a friend's laptop w/ a Celeron single core processor that has a maximum of 512Meg or RAM in it.

I choose Xubuntu 10.10 for him, dual boot install and a separate partition for the '/' (system files) and the '/Home' location (stuff and most settings I wont loose if I zero out the OS itself). 

It was a bit of an experiment, in that I wasn't sure the Dell 1000 was going to do well, but it came through w/ flying colours.



TBerk
I think this Summer I'm going to get back to Compiling from Scratch more and more...

---

### Post by fleamour on 2011-07-02
Last time I tried Lubuntu it was not fit for purpose.  Mint LXDE seemed a wholly more classy affair.  But now I've switched back to Xubuntu (XFCE) as it is more fully featured.  

LXDE does not have such niceties as movable desktop icons & is a bit basic.  I understand things could have moved on by now, but I'm happy with XFCE running a PIII with 512MB RAM.

---

### Post by amjjawad on 2011-07-02
Yes, 512MB is enough (if GNOME what we're talking about) to run Ubuntu 10.04 but it might be slow on 11.04.

I had 10.04 on P4 and less than 512MB of RAM and it was running without any issue.
I installed 11.04 and I can tell it's getting slower.

SWAP Partition is *better* to be 1GB, just in case.

As for other variants:
Not sure about KDE - never used it and don't want to.
Yes for Xubuntu
and definitely YES with Lubuntu.

Lubuntu 11.04 is great indeed and has lots of improvement over 10.04.

There are many other distributions which will run VERY smoothly with such RAM.

---

### Post by brawnypandora0 on 2011-07-02
I've decided to try Peppermint OS. I hear it works on even 128MB RAM. Anyone here use it?

---

### Post by Ahunt on 2011-07-02
We use Lubuntu and we love it. Even if you can get Ubuntu running on 512 MB you will find that it may be frustratingly slow and that you can only run one or two applications at a time. I suggest trying out Lubuntu, it works well.

---

### Post by brawnypandora0 on 2011-07-02
> **Ahunt said:**
> We use Lubuntu and we love it. Even if you can get Ubuntu running on 512 MB you will find that it may be frustratingly slow and that you can only run one or two applications at a time. I suggest trying out Lubuntu, it works well.

Already tried it, but it's still not as fast as I would like, so I'm gonna give Peppermint a try.

---

### Post by amjjawad on 2011-07-03
> **brawnypandora0 said:**
> Already tried it, but it's still not as fast as I would like, so I'm gonna give Peppermint a try.

Lubuntu 11.04 all the way for 512MB of RAM. However, it's your call :)
At least, it's supported here and with the next release, it's going to be the official variant for Ubuntu.

---

### Post by Psyco430404 on 2011-07-03
im running an install with compiz and all on 256 mb DDR, so yes 512 can lol.

---

### Post by amjjawad on 2011-07-03
This is on Ubuntu 11.04 (Classic Desktop with no effect) with Firefox 5 with 4 tabs and Chromium 12 with 3 tabs.

So, simply, 11.04 is NOT usable (because it will be SO SLOW) with 512MB of RAM. Imagine what if I was logging in to Unity (which is not working with my PC anyway)?

Lubuntu on the same PC is running super fast.

---

