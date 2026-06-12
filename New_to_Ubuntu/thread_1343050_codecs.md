---
title: "codecs"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by anupsg on 2009-12-01
re how to install codec.... automatically its not downloadin the required codecs ............ even when i go to >applications>ubuntu software center> sounds and video > then if i click to vlc player ..... it shows that current data not available......... i cant even play any media files........

---

### Post by LowSky on 2009-12-01
do you have an internet connection?

---

### Post by Hospadar on 2009-12-01
if you install the "ubuntu-restricted-extras" package from synaptic or the command line it'll pull in everything you need.

---

### Post by ukripper on 2009-12-01
Why multiple threads for same thing?

[http://ubuntuforums.org/showthread.php?t=1343055](http://ubuntuforums.org/showthread.php?t=1343055)

[http://ubuntuforums.org/showthread.php?t=1342985](http://ubuntuforums.org/showthread.php?t=1342985)

---

### Post by Alex Libman on 2009-12-01
One of the first things I do when I install a new (K)ubuntu desktop is add [the Medibuntu repository]("https://help.ubuntu.com/community/Medibuntu"):

```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update
```Then I add [other repositories]("http://linuxpoison.blogspot.com/2009/04/list-of-repositories-for-ubuntu-904.html") I consider essential for a decent Ubuntu experience:

```
sudo add-apt-repository ppa:chromium-daily
sudo add-apt-repository ppa:firefox-smooth-scaling  # fixes an issue with my Nvidia drivers
sudo add-apt-repository ppa:deluge-team/ppa

# etc, based on what you need ...  then:

sudo synaptic &
```Then, though this can be done via command-line, I usually use [Synaptic]("http://en.wikipedia.org/wiki/Synaptic_%28software%29") to find all the packages I need, so that I could leave it running a batch install process while I do other stuff.  I usually:


[LIST=1]
[*]Go to Settings menu -> Repositories.
[*]In the "Ubuntu Software" tab, I make sure the four upper check-boxes (main universe, restricted, multiverse) are checked, and then click the drop-down box after "Download from", choose other, and use the "Select Best Server" feature, which pings all of them and picks the fastest one for you.
[*]In the "Other Software" tab, I confirm that everything is checked (unless I know I don't want it).
[*]In the "Updates" tab, I make sure the upper four boxes are checked.
[*]I then close the "Software Sources" window, click the "Reload" button on the Synaptic toolbar, and then click the "Mark All Updates" button.
[*]I then click "Origin" on the bottom-left of the Synaptic window, go through the repositories I added myself ("*[medibuntu]("http://en.wikipedia.org/wiki/Medibuntu")*" and "*[launchpad]("http://en.wikipedia.org/wiki/Launchpad_%28website%29")*" will appear in several variants), and select everything unless I know why I don't want it.
[*]I then click the "Search" button (not the "Quick search" text-box), select to look in "Name" (without description), and search for the items I want to install, select matching packages as appropriate, and repeat this step for all the packages I want to get.  To make sure I get the ideal media player experience without worrying about codecs, I usually search for "[gstreamer]("http://en.wikipedia.org/wiki/GStreamer")", "[xine]("http://en.wikipedia.org/wiki/Xine")", "[ffmpeg]("http://en.wikipedia.org/wiki/FFmpeg")", "[totem]("http://en.wikipedia.org/wiki/Totem_%28media_player%29")", "[mplayer]("http://en.wikipedia.org/wiki/MPlayer")" and/or "[vlc]("http://en.wikipedia.org/wiki/VLC_media_player")" and install all all of the add-ons / plug-ins available.  Note that the former two are libraries that are used by other players - you'd usually use one or the other.
[*]Finally I hit the "Apply" button and spend the next few minutes doing something else (typically Firefox add-ons & other settings).
[/LIST]

---

