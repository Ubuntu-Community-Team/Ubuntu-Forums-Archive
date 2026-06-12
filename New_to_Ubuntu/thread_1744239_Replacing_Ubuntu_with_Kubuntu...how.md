---
title: "Replacing Ubuntu with Kubuntu...how?"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by unknowngal on 2011-04-30
Sorry for starting another thread. ^^;; Just was wondering how this could be done, replacing Ubuntu with Kubuntu. Would I have to remove Ubuntu first, and if so, how? Do I install Kubuntu first, then delete Ubuntu? How would I delete Ubuntu afterwards? Thanks! ^^

---

### Post by 8_Bit on 2011-04-30
Install the package "kubuntu-desktop" from Synaptic or the Software Centre.
Be aware it will remove the package 'ubuntu-desktop' meaning your GNOME apps will disappear.

---

### Post by Legeril on 2011-04-30
Kubuntu is just Ubuntu with KDE instead of Gnome, install KDE and use that - you have Kubuntu easy.

KDE will come with different selection of apps, but I think you will still be able to see and access the Gnome apps you have installed allready

---

### Post by howefield on 2011-04-30
You could install right over your Ubuntu install, select "Something Else" in the partitioning screen of the Kubuntu installation and mount your existing Ubuntu partitions, marking them for format.

Or simply tell the Kubuntu installation to use the whole disk.

Is it only Ubuntu that you currently have on the disk ?

Whatever you decide to do, ensure that you have a safe backup of anything data you wouldn't want to lose.

---

### Post by unknowngal on 2011-04-30
> **howefield said:**
> You could install right over your Ubuntu install, select "Something Else" in the partitioning screen of the Kubuntu installation and mount your existing Ubuntu partitions, marking them for format.

Or simply tell the Kubuntu installation to use the whole disk.

Is it only Ubuntu that you currently have on the disk ?

Whatever you decide to do, ensure that you have a safe backup of anything data you wouldn't want to lose.

Hmm...lemme see if I have this correct: I burn the .iso Kubuntu file onto a CD, and then when I get to the installation, I select "Something Else" in the partitioning screen. That would select the partition I made for Ubuntu? :o So Kubuntu would basically record itself *over* Ubuntu?

Oh, and actually, I have a dual boot setup, it's Ubuntu and Windows 7. *nods*

---

### Post by howefield on 2011-04-30
You've pretty much got it. :)

I am making an assumption that Kubuntu uses the same terminology as Ubuntu as far as selecting the manual partitioning options, but if it doesn't - it should be fairly obvious.

If you get to the partitioning stage and then are unsure as to how to proceed, you can quit the installation without harming your existing install.

I am about to do the same thing, although I have an empty partition to put it on and will use the manual partitioning to select it. Downloading the iso at the minute.

---

### Post by buzzmandt on 2011-04-30
if you don't care to have ubuntu gnome apps and kubuntu kde apps all on the same install then just run
```
sudo apt-get install kubuntu-desktop
```

when it tells you it can only have one active display manager select kdm.


If you don't want the gnome apps any more run the above and finish it off with ```
sudo apt-get remove banshee banshee-extension-soundmenu banshee-extension-ubuntuonemusicstore brasero empathy eog evince evolution evolution-common evolution-exchange evolution-indicator evolution-plugins evolution-webcal gdm gdm-guest-session gedit gnome-codec-install gnome-nettool gnome-screensaver gnome-screenshot gnome-search-tool gnome-session-canberra gnome-system-log gnome-system-tools gnome-terminal gnome-themes-selected gnome-themes-ubuntu gtk2-engines gtk2-engines-pixbuf humanity-icon-theme indicator-applet-session indicator-datetime language-selector-gnome libevolution libsyncdaemon-1.0-1 libubuntuone-1.0-1 libubuntuone1.0-cil light-themes metacity nautilus-sendto nautilus-share notify-osd pitivi screensaver-default-images simple-scan software-center software-properties-gtk ssh-askpass-gnome synaptic system-config-printer-gnome totem totem-mozilla totem-plugins ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-mono ubuntu-sounds ubuntuone-client ubuntuone-client-gnome ubuntuone-control-panel ubuntuone-control-panel-gtk unity unity-asset-pool update-notifier usb-creator-gtk xscreensaver-data xscreensaver-gl xterm zenity gnome-session
```

that's not all of them but it get a pretty good chunk of 'em

---

### Post by buzzmandt on 2011-04-30
it's the same installer, just prettier (blue)

---

### Post by unknowngal on 2011-04-30
Thanks guys! :) I ended up with Linux Mint though, though I might come back to Ubuntu or even try Kubuntu later on. :D *thumbsup!*

---

### Post by buzzmandt on 2011-04-30
you should give linux mint kde version a spin too, I really like it but it's not quite as bleeding edge as (k)ubuntu

---

### Post by matthewbpt on 2011-04-30
Look here for the most complete answer [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde) .

---

