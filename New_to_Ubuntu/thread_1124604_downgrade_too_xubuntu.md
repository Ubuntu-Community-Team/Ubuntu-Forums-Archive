---
title: "downgrade too xubuntu"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by jake43025 on 2009-04-13
i have just installed version 9.04 and everything seems to be working great.:p my only problem really is i may have too use xubuntu cause my system only has 256mb ram and its kinda slow.is there a way too downgrade too xubuntu without have too format my whole drive?iam dualbooting xp at the moment and didnt really want too delete it just yet.my other question is will xubuntu have the same wifi drivers/software so it will work like it does in ubuntu?(my wifi card is a ipw2100)

also i installed epiphany web browser but i can only run it from the terminal.i searched in applications but no shortcut was made.how do i make a shortcut for epiphany and have it on my desktop or app menu?thanks.

---

### Post by ninjapirate89 on 2009-04-13
I don't think you can turn a ubuntu install into a xubuntu install. If it can be done I guarantee its much easier to just do a fresh install.

---

### Post by SunnyRabbiera on 2009-04-13
Xubuntu isnt really a downgrade, its just a bit different.
Anyhow there is no need to reformat or burn a new disk, if you can open synaptic package manager under system> administration > synaptic package manager
and then search and install the package xubuntu-desktop it will install what you need without a reformat.
By the way using a beta is a good reason why you are having issues...

> **ninjapirate89 said:**
> I don't think you can turn a ubuntu install into a xubuntu install. If it can be done I guarantee its much easier to just do a fresh install.

Not in full but it will allow the OP to have a faster system, installing xubuntu-desktop should do most of the work though

---

### Post by pspsampsp on 2009-04-13
to get the shortcut for epiphany right click on the applications menu and go edit , find internet and click on that so it shows all the programs in side that sub menu and now make sure epiphany is clicked.(sorry if thats confusing i suck at giving advice). to change from ubuntu to xubuntu try this running these commands in terminal: sudo apt-get install xubuntu-desktop
sudo apt-get remove xubuntu desktop
sudo apt-get autoremove

(taken from [http://tuxicity.wordpress.com/2007/01/30/howto-switch-from-ubuntu-to-kubuntu-or-xubuntu-or-edubuntu-or-vice-versa-610-edgy/](http://tuxicity.wordpress.com/2007/01/30/howto-switch-from-ubuntu-to-kubuntu-or-xubuntu-or-edubuntu-or-vice-versa-610-edgy/) )

---

### Post by halitech on 2009-04-13
not sure if this will work in 9.04 but you could try the info here

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

this will explain how to install XFCE (the basis for Xubuntu) and how to remove all Gnome apps.

---

### Post by t0p on 2009-04-13
> **pspsampsp said:**
> to change from ubuntu to xubuntu try this running these commands in terminal: sudo apt-get install xubuntu-desktop
sudo apt-get remove xubuntu desktop
sudo apt-get autoremove


Has anyone here successively run these commands?  It seems to  me that they will install xubuntu-desktop, then remove it and its residuals, leaving only what you had before.  Am I wrong?

---

### Post by halitech on 2009-04-13
I think there is a typo in the original commands. Second step should be 
```
sudo apt-get remove ubuntu-desktop
```
onoly problem with this is that just removes the meta-package for the desktop. the link I gave has a list of all programs to actually remove
```
sudo apt-get remove alacarte binfmt-support brltty brltty-x11 capplets-data cdrdao cli-common compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compiz-wrapper compizconfig-backend-gconf contact-lookup-applet dcraw deskbar-applet ekiga eog evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins evolution-webcal example-content f-spot fast-user-switch-applet firefox-3.0-gnome-support firefox-gnome-support gconf-editor gdm-guest-session gedit gedit-common gnome-about gnome-applets gnome-applets-data gnome-control-center gnome-desktop-data gnome-menus gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-session gnome-settings-daemon gnome-spell gnome-terminal gnome-terminal-data gnome-themes gnome-user-guide gnome-utils gstreamer0.10-plugins-base-apps gstreamer0.10-pulseaudio gstreamer0.10-schroedinger gstreamer0.10-tools gvfs-bin gvfs-fuse human-icon-theme human-theme hwtest hwtest-gtk libao2 libart2.0-cil libasound2-plugins libcanberra-gnome libcanberra-gtk-module libcanberra-gtk0 libcanberra0 libcompizconfig0 libdecoration0 libdeskbar-tracker libdirectfb-1.0-0 libebackend1.2-0 libedata-book1.2-2 libedata-cal1.2-6 libedataserverui1.2-8 libeel2-2 libeel2-data libegroupwise1.2-13 libexchange-storage1.2-3 libexempi3 libflickrnet2.1.5-cil libgconf2.0-cil libgdata-google1.2-1 libgdata1.2-1 libgdiplus libgif4 libglade2.0-cil libglib2.0-cil libglitz-glx1 libglitz1 libgmime-2.0-2a libgmime2.2-cil libgnome-keyring1.0-cil libgnome-pilot2 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2.0-cil libgnomevfs2-bin libgpod-common libgpod3 libgtk2.0-cil libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml3.14-19 libhyphen0 libicu38 liblpint-bonobo0 libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo1.0-cil libmono-cairo2.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds1.0-cil libmono-data-tds2.0-cil libmono-i18n1.0-cil libmono-i18n2.0-cil libmono-security1.0-cil libmono-security2.0-cil libmono-sharpzip0.84-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data1.0-cil libmono-system-data2.0-cil libmono-system-web1.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono1.0-cil libmono2.0-cil libmtp8 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libneon27 libopal-2.2 libpisock9 libpisync1 libpt-1.10.10 libpt-1.10.10-plugins-alsa libpt-1.10.10-plugins-v4l libpt-1.10.10-plugins-v4l2 libpulsecore5 libsamplerate0 libschroedinger-1.0-0 libsdl1.2debian libsdl1.2debian-alsa libsgutils1 libspeexdsp1 libsqlite0 libtracker-gtk0 libts-0.0-0 libwps-0.1-1 libx11-xcb1 mesa-utils metacity mono-common mono-gac mono-jit mono-runtime mousetweaks mtools nautilus nautilus-cd-burner nautilus-data nautilus-sendto nautilus-share openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-emailmerge openoffice.org-gnome openoffice.org-gtk openoffice.org-impress openoffice.org-math openoffice.org-style-human openoffice.org-writer pkg-config pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11 python-beagle python-gmenu python-gtksourceview2 python-uno rarian-compat rdesktop rhythmbox screen-resolution-extra sg3-utils sqlite sqlite3 syslinux tangerine-icon-theme tomboy tracker tracker-search-tool tracker-utils tsclient ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-gdm-themes ubuntu-system-service ubuntu-wallpapers untex usb-creator usplash-theme-ubuntu vino whois wv xdg-user-dirs xdg-user-dirs-gtk xulrunner-1.9-gnome-support && sudo apt-get install xubuntu-desktop
```

which actually does it all in 1 step

---

### Post by pspsampsp on 2009-04-13
i used the guide i linked to when i was using 8.10 so i think it should work.

---

### Post by Paqman on 2009-04-13
> **t0p said:**
> Has anyone here successively run these commands?  It seems to  me that they will install xubuntu-desktop, then remove it and its residuals, leaving only what you had before.  Am I wrong?

Sort of. Installing xubuntu-desktop will install all the Xubuntu apps, but apt-get remove xubuntu-desktop will only remove the meta-package, and leave all it's dependencies. Which is just a bizarre thing to do.

---

### Post by jake43025 on 2009-04-13
well i got xfce installed,and seems too be doing better.iam sure it doesnt help it thats its a beta like sunny was saying.i got the shortcuts figured out too.:p i guess if iam still having problems ill just go back too the stable version of xubuntu and just wait for the 9.04 version to be complete before i try to reinstall it.i appreciate the help everyone.

---

### Post by moredhel on 2009-04-13
If you still aren't getting good enough performance you could try LXDE which is even more of a performance-orientated Desktop Environment :)

---

### Post by jake43025 on 2009-04-13
i think i may try too install that too.i need the least amount of ram use possible.

---

### Post by ninjapirate89 on 2009-04-13
What is stopping you from just doing a clean install of xubuntu?

---

### Post by moredhel on 2009-04-13
Mmm, well you will find that LXDE is *significantly* faster, far more than the move from GNOME to Xfce.

---

### Post by Paqman on 2009-04-13
> **ninjapirate89 said:**
> What is stopping you from just doing a clean install of xubuntu?

You don't need to do a reinstall just to change your DE. Just install the packages and log out.

---

### Post by ninjapirate89 on 2009-04-13
> **Paqman said:**
> You don't need to do a reinstall just to change your DE. Just install the packages and log out.

I know but it seems to me that if he is using a computer with only 256MB of RAM then it would be easier to just install xubuntu.

---

### Post by halitech on 2009-04-13
> **ninjapirate89 said:**
> I know but it seems to me that if he is using a computer with only 256MB of RAM then it would be easier to just install xubuntu.

hmmmm, let's see

open a terminal and type in ```
sudo apt-get install xubuntu-desktop
```compared to reinstalling a complete system and then having to do the updates. Personally, installing the xubuntu desktop seems faster to me, although with the amount of bloat in xubuntu due to all the gnome apps and dependencies he might as well run ubuntu.

if you are going to reinstall, might I suggest going with Debian with XFCE or LXDE and get some actual speed improvement out of your system?

---

### Post by jake43025 on 2009-04-13
the reason i didnt want to just download xubuntu and reinstall it cause iam still dualbooting with xp.iam not quite ready  for ubuntu as my everyday system.i installed lxde which seemed a lot quicker,but ended up losing my wifi for some reason.iam sure there is a manual way to setup that but ill figure that out later.

i think my main problem is iam using the beta which could be making it slower.iam downloading xubuntu 8.10 and will just have too reinstall both xp and xubuntu.ill let you know how it goes once iam done.

---

### Post by jake43025 on 2009-04-13
dont know if iam quite ready for debian "halitech" but from what i read it sounds really fast.i think iam just at the beginners stage of linux.

---

### Post by halitech on 2009-04-13
jake,

basically Ubuntu is Debian SID (testing) so if you can handle Ubuntu you can handle Debian. I went from Ubuntu (7.04 was the last version I used) to Debian Etch with XFCE and yes, there were a few hiccups and doh moments for me but for the most part, I don't regret changing and most of the tips and help from here work with Debian (aside from a few network things using Thunar) so its not like you will be totally lost. However, having said that, it is your computer and your free choice on what you want to run.

---

### Post by Paqman on 2009-04-13
> **halitech said:**
> with the amount of bloat in xubuntu due to all the gnome apps and dependencies he might as well run ubuntu.


I've found that with Xubuntu myself. It's really not that much lighter than the Gnome version, and lacks a lot of the nice features. Thunar just doesn't look good compared to Nautilus, for example.

---

### Post by halitech on 2009-04-13
> **Paqman said:**
> I've found that with Xubuntu myself. It's really not that much lighter than the Gnome version, and lacks a lot of the nice features. Thunar just doesn't look good compared to Nautilus, for example.

thats why when I borked my system a while ago I decided to go back to the root and install Debian with XFCE. I find it is so much faster on my system and other then the lack of network support in thunar (which I can live without) I find it so much better. My boot time dropped by almost 2 minutes as well and by using Debian Testing, I can get more up to date apps then with using Ubuntu and having to upgrade every 6 months.

---

### Post by moredhel on 2009-04-13
I don't think there is the need to move to debian... just install LXDE.

Crunchbang is based off Ubuntu and it's openbox-based (the window manager that LXDE uses) but it doesn't have as much as LXDE does (and LXDE will be practically as fast)

---

### Post by jake43025 on 2009-04-13
i think my only problem with installing debian is i dont have an internet connection.iam using the librarys wifi as my dedicated connection.does debian have xfce installed or do u have too download that and install it?the only other problem is i would have too setup my wifi which would also need me too be connected on the actual lan network adapter too setup that.

---

### Post by halitech on 2009-04-13
Debian does have a pre-built download with XFCE and LXDE on it so you would only need the 1 cd.

[http://cdimage.debian.org/cdimage/weekly-builds/i386/iso-cd/debian-testing-i386-xfce+lxde-CD-1.iso](http://cdimage.debian.org/cdimage/weekly-builds/i386/iso-cd/debian-testing-i386-xfce+lxde-CD-1.iso)

Wife could be an issue depending on which card you have

---

### Post by jake43025 on 2009-04-13
ill try out that version and see how it goes.my wifi adapter is a  intel ipw2100.this is the only install guide i could find for it:

[http://jblevins.org/computing/linux/ipw2100](http://jblevins.org/computing/linux/ipw2100)

i think it starts from step 7 for the debian installs(module-assistant).i might be back too the beginning though cause i would need too download the update packages for it,unless it came with it already.

---

### Post by halitech on 2009-04-13
the link I gave you is for the weekly build of testing so it should be pretty up to date (March 30, 2009) so there shouldn't be too many updates to do.

---

### Post by snowpine on 2009-04-13
Hi Jake,
Let me be the voice of reason here. You already have a working Ubuntu setup, and you made it run faster by installing LXDE, but you can't get the network manager to appear. Is that all correct?

All you need to do is open the terminal and type:

```
nm-applet
```

Did the network manager appear on the task bar? Assuming the experiment worked, you can make it permanent by adding nm-applet to your autostarted applications. I am not 100% sure how to do this in LXDE (I don't personally use it) but in Openbox for example, you would do this by editing your ~/.config/openbox/autostart.sh file--can any kind LXDE user help with this?

---

### Post by jake43025 on 2009-04-13
ok that sounds good.ill try it out along with xubuntu and let everyone know how it goes.thanks

---

### Post by jake43025 on 2009-04-13
it was running quicker with lxde but iam wondering since iam using the beta version 9.04 its actually slowing it down?thats why i was thinking of going back too a stable version or just basic debian so i could build up the system how i wanted it.iam in xp right now but once i go back too ubuntu ill try out that command and see if i can get my wifi working.i just didnt see the little wifi icon when i first booted into like i did with gnome or xfce.

---

### Post by jake43025 on 2009-04-14
i ran the nm-applet to load my wifi and it worked fine.only thing is i have too did it everytime i boot into lxde.i searched the board but couldnt find any real answers on how to make it automatically load.can anyone help?

---

