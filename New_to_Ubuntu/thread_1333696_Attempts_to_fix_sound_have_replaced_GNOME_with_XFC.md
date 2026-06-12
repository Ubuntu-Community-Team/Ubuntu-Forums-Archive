---
title: "Attempts to fix sound have replaced GNOME with XFCE!"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by Darkness Falls on 2009-11-21
Okay, things seem to have gone badly wrong. Following this thread here:

[http://ubuntuforums.org/showthread.php?p=8350080#post8350080](http://ubuntuforums.org/showthread.php?p=8350080#post8350080)

...I uninstalled and reinstalled ALSA, which did seem to fix the main issue with the sound (although its a little fuzzy for some reason now), but didn't restore the headphone support which I previously had working. Since the last thing I did to the sound when it was working fully was to ditch Pulseaudio and install EsounD, I uninstalled and reinstalled it (EsounD), hoping that that might fix the problem. Oh boy was that a bad move.

The package *esound-common* had a whole list of dependent packages, which I took great care to note down for when I was reinstalling it, and are summarised below:

```
alsaplayer-common

 alsaplayer-esd

 anjuta

 compiz

 compiz-gnome

 contact-lookup-applet

 ekiga

 esound

 esound-clients

 evolution

 evolution-data-server

 evolution-exchange

 evolution-indicator

 evolution-plugins

 evolution-webcal

 f-spot

 fast-user-switch-applet

 firefox-3.0-gnome-support

 firefox-gnome-support

 gnome-about

 gnome-alsamixer

 gnome-applets

 gnome-control-center

 gnome-media

 gnome-orca

 gnome-panel

 gnome-pilot

 gnome-pilot-conduits

 gnome-power-manager

 gnome-session

 gnome-user-guide

 gnome-user-guide-de

 gnome-user-guide-en

 gnome-user-guide-es

 gnome-user-guide-fr

 gnome-user-guide-pt

 gnome-utils

 gnumeric

 gufw

 indicator-applet

 indicator-messages

 libbonoboui2-0

 libesd-alsa0

 libgail-gnome-module

 libgnome-media0

 libgnome-pilot2

 libgnome2-0

 libgnome2-perl

 libgnome2.24-cil

 libgnomepanel2.24-cil

 libgnomeui-0

 libgoffice-0-6

 libgtkhtml-editor0

 libgtkhtml3.14-19

 liblpint-bonobo0

 libpanel-applet2-0

 monodevelop

 mousetweaks

 nautilus

 nautilus-share

 python-gnome2

 python-gnome2-desktop

 python-pyatspi

 qemu

 rhythmbox

 seahorse-plugins

 system-config-printer-gnome

 tomboy

 tsclient

 ubuntu-docs

 update-notifier

 vinagre

 vino

 wine

 xulrunner-1.9-gnome-support

 yelp

 
```I have to admit I was fairly doubtful as to why removing *esound-common* necessitated the removal of things like *ubuntu-docs* and *gnome-utils*, since as far as I know, they have nothing to do with the sound working, but Synaptic Package Manager said so, so I dutifully (read: stupidly) removed them, then worked my way down the list carefully and reinstalled them all, and rebooted.

And XFCE had taken over in lieu of GNOME. First I blinked, then I panicked (to get it out of my system), then went back into Synaptic and searched for "gnome", and installed the package. (I'm a little confused as to why it wasn't installed already - it wasn't on the list above, and Synaptic said nothing about removing it.) Then rebooted. Then panicked again, because it's still showing the XFCE desktop.

So, in short, this is a cry for help! I have the following major questions:

1) Why did *esound-common* need to remove so many other packages when I removed it?

2) Why is Ubuntu not using the same packages, given that I reinstalled them immediately following their removal, without even rebooting inbetween? (I figured rebooting without a lot of the packages that sounded pretty important would be a Bad Thing.)

3) How on earth do I get GNOME back? XFCE might work fine, but I'd only just gotten used to GNOME!

Any help you could give would be greatly appreciated!

D.F.

---

### Post by laidback on 2009-11-21
Is it not possble to go to Synaptic and install Gnome again?

---

### Post by Darkness Falls on 2009-11-21
I already have done - at least, I've installed the package *gnome* - but upon reboot, I'm still faced with XFCE. Are there other packages needed? If so, what are their names?

D.F.

---

### Post by fromthehill on 2009-11-21
you should be able to change that before you login

[s]at the login screen click on a user
at the bottom of you screen you should see 'sessions:' with a dropbox next to it.
change it to gnome and log in[/s]

now I see you use ubuntu 9.04
my instructions were for 9.10 ](*,)

see post below me :p

---

### Post by XubuRoxMySox on 2009-11-21
Gnome is prob'ly still there, especially if it shows up in Synaptic. While you're in Synaptic, look for the metapackage called "Ubuntu-desktop." It should be installed.

Perhaps the only problem is the Login manager. Reboot and at Login, select **Options** (at the bottom of the login screen) and **choose Session**, then select **Gnome** and set as **default**.

Xubuntu does not ship with PulseAudio. Perhaps Ubuntu thought you wanted Xubuntu?:) Anyway, if it's installed, you can choose it at login.

-Robin

---

### Post by Darkness Falls on 2009-11-21
Whew! Just tried that, and it's worked; I'm back in GNOME again. Many, many thanks, dixie! (Sorry fromthehill, I should've said I was using 9.04! Thanks anyway, though!)

I looked up *ubuntu-desktop*, but it seems installing that would remove EsounD and replace it with Pulseaudio, which I had some problems getting to work with ALSA properly. Its full list of changes is:

```
To be removed:
esound
To be installed:
linux-headers-generic
pulseaudio
pulseaudio-esound-compat
```

On the other hand, I could start the whole process again in an attempt to get the sound working properly. Might that be helpful, d'you think?

D.F.

---

### Post by kansasnoob on 2009-11-21
The package gnome is actually the wrong package to install. The proper package is ubuntu-desktop.

It may help you to look at this section:

> Playing Around
KDE/Gnome Comparison
Install KDE
Install XFCE
Install IceWM
Pure Gnome
Pure KDE
Pure XFCE
Make your own Ubuntu remix 

of this guide:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by Darkness Falls on 2009-11-21
Awesome! Thanks for that link - I've bookmarked it and will go through it tomorrow in more depth! I think I've done enough amateurish rummaging around in the depths of my laptop for one evening, though. :p

Thanks for all your replies, everyone! You've all been a great help!

D.F.

---

