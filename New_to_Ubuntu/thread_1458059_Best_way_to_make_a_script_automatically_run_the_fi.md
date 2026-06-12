---
title: "Best way to make a script automatically run the first time the system boots...?"
date: 2010-04-19
forum: New to Ubuntu
---

### Post by brucewagner on 2010-04-19
What's the best way to make a script automatically run the first time the system boots... and then never again ( in Ubuntu ) ?

For example, I can place an executable script in the /usr/local/bin directory...  called "myownsoftareinstallscript"  That way it can be run from Terminal... Then what?

Should I create an entry in the "Strartup Applications"?

What should the entry be...? Just the name of the script as the "command"?    Like:  Command:  myownsoftareinstallscript

Can the last line of the script then turn that OFF so that it only runs ONCE (the first time the system boots)...?

If so... What is the script (command) line to turn something OFF (uncheck it) in "Startup Applications"?

---

### Post by LowSky on 2010-04-19
Sorry but can I ask what your script is doing?

I would say the best option is to have the script run and then delete itself if you never need it to run again.

---

### Post by brucewagner on 2010-04-19
Sure, thanks.

The script is doing:

```
sudo apt-get update
sudo apt-get -y install wallpaper-tray
sudo apt-get -y install edubuntu-desktop
sudo apt-get -y install mp3wrap mp3splt
sudo apt-get -y install easytag
sudo apt-get -y install libid3-3.8.3-dev
sudo apt-get -y install ffmpeg
sudo apt-get -y install parcellite
sudo apt-get -y install gwibber
sudo apt-get -y install thunderbird
sudo apt-get -y install xchat
sudo apt-get -y install xchat-gnome
sudo apt-get -y install gnucash
sudo apt-get -y install gnucash-docs
sudo apt-get -y install pitivi
sudo apt-get -y install kino
sudo apt-get -y install audacity
sudo apt-get -y install audacity-data
sudo apt-get -y install lame
sudo apt-get -y install lame-doc
sudo apt-get -y install openoffice.org-base
sudo apt-get -y install dvdstyler
sudo apt-get -y install dvdstyler-data
sudo apt-get -y install blender25
sudo apt-get -y install gtk-recordmydesktop
sudo apt-get -y install p7zip-full
sudo apt-get -y install p7zip-rar
sudo apt-get -y install p7zip
sudo apt-get -y install scribus-doc
sudo apt-get -y install scribus-template
sudo apt-get -y install avidemux
sudo apt-get -y install avidemux-plugins
sudo apt-get -y install ekiga
sudo apt-get -y install twinkle
sudo apt-get -y install xarchiver
sudo apt-get -y install blueman
sudo apt-get -y install cheese
sudo apt-get -y install emesene
sudo apt-get -y install filezilla
sudo apt-get -y install gtg
sudo apt-get -y install giver
sudo apt-get -y install gnome-do
sudo apt-get -y install banshee
sudo apt-get -y install oggconvert
sudo apt-get -y install kruler
sudo apt-get -y install googleearth
sudo apt-get -y install googleearth-data
sudo apt-get -y install boxee
sudo apt-get -y install gizmo5
sudo apt-get -y install virtualbox-3.1
sudo apt-get -y install celtx
sudo apt-get -y install ifreebudget
sudo apt-get -y install mypaint
sudo apt-get -y install lives
sudo apt-get -y install glabels
sudo apt-get -y install glabels-data
sudo apt-get -y install kompozer
sudo apt-get -y install kompozer-data
sudo apt-get -y install freemind
sudo apt-get -y install freemind-doc
sudo apt-get -y install freemind-browser
sudo apt-get -y install freemind-plugins-script
sudo apt-get -y install freemind-plugins-help
sudo apt-get -y install freemind-plugins-svg
sudo apt-get -y install frostwire
sudo apt-get -y install fotoxx
sudo apt-get -y install namebench
sudo apt-get -y install tellico
sudo apt-get -y install tellico-data
sudo apt-get -y install tellico-scripts
sudo apt-get -y install gimp-save-for-web
sudo apt-get -y install gimp-plugin-registry
sudo apt-get -y install tucan
sudo apt-get -y install ogmrip*
sudo apt-get -y install bookwrite
sudo apt-get -y install bashare
sudo apt-get -y install pdfmod
sudo apt-get -y install invulgotracker
sudo apt-get -y install fotowall
sudo apt-get -y install ignuit
sudo apt-get -y install smile*
sudo apt-get -y install gambas2*
sudo apt-get -y install wikidpad
sudo apt-get update
exit

```

:)

I don't know that it's important that it erase itself when it completes successfully, but...  How could it do that?

Also, how do I make it run once... upon first boot?

And how do I prevent an error upon subsequent boots... if it's been erased?

---

### Post by Boondoklife on 2010-04-19
Well the only thing that comes to mind at the moment would be to put a link to the script in the /etc/rc.local file and then use sed at the end of your script to cut out the link from rc.local.

This would allow it to run on first boot, as root (needed since you are doing apt-get's), and then not run again. I dont have access to my box to play with the sed scripts but just google sed and there are quite a few tutorials out there that should serve as a base.

---

