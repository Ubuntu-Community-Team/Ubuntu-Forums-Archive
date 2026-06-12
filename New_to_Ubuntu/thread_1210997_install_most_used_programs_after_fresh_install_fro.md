---
title: "install most used programs after fresh install from command line"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by powel212 on 2009-07-12
Here is a little command line to run after you have installed a fresh copy of Ubuntu. These are my most commonly used, installed programs. I made this little command line install because I help a lot of folks get their first Ubuntu install up and running and this little tool simplifies the process for me.

First make sure you have your system updates up to date with

```
sudo apt-get update && sudo apt-get upgrade
```

Then in a terminal run

```
sudo apt-get -y install ntfs-config system-config-samba compizconfig-settings-manager ubuntu-restricted-extras banshee pysdm devede wine gkrellm smplayer vlc xvidcap soundconverter krita epiphany-browser gmail-notify deluge kflickr digiKam gparted preload libdvdread4
```

Once that is done there is one more step to enable DVD playback

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

If you see anything in the list that is not for you just delete the word/s from the command line. Alternatively you can use synaptic or add/remove. All of these programs are in the repos.

Have fun

Powel

Descriptions;
[B]
ntfs-config[/B] allows you to mount ntfs drives
**system-config-samba** file sharing manager
**compizconfig-settings-manager** manage desktop effects
**ubuntu-restricted-extras** lets you use mp3s and much more
**banshee** music player
**pysdm** mounting volumes tool (edit fstab)
**devede** make your avi movies into dvds
**wine** run windows programs
**gkrellm** system temperature monitor and more
**smplayer** movie player
**vlc** movie player
**xvidcap** screen video capture
**soundconverter** convert wave to mp3 or whatever
**krita** photo editor
**epiphany-browser **light web browser
**gmail-notify** notifies of new email
**deluge** torrent engine
**kflickr** upload to flickr
**digiKam** edit .raw files
**gparted** partition editor
**preload** preload commonly used programs for a faster computer. Great if you have a lot of ram
**libdvdread4** Enable dvd support

---

### Post by powel212 on 2009-07-12
BTW I did not include Virtualbox here because it requires adding Repos but it is absolutely worth taking the extra 3 minutes to install.

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

P

---

### Post by Ji Ruo on 2009-07-13
Thanks for posting this. At the moment I'm installing and configuring kubuntu on PCs for a community group, and this list has been useful to go through.

---

