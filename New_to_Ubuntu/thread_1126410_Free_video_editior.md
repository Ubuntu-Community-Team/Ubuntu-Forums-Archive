---
title: "Free video editior"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by newlinuxuser2008 on 2009-04-15
Is there any good free video editor to use with my exilim camera for ubuntu?

---

### Post by Hospadar on 2009-04-15
There are a couple that I know of, just googling "linux video editors" will turn up some good results.

The biggest is probably cinelerra, which is, as much as I gather, very full featured and stable, although I think it's more targeted towards professionals and people who are real serious about video.  Also you'll have to build it yourself which might be sort of a pain.

Kdenlive comes in the repos and looks somewhat mature, you might want to give that a try first.

Also, depending on how well these tools work, you may want to first use a tool like ffmpeg/mencoder (command line) or avidemux (gui) to convert all your videos to some common format first.  

Except for cinelerra, all the software I mentioned is in the repositories (installable through synaptic)

Edit:
Here's a pretty good layout:
[http://jaypeeonline.net/freeware/free-video-editing-software-linux/](http://jaypeeonline.net/freeware/free-video-editing-software-linux/)

---

### Post by llamabr on 2009-04-15
> **newlinuxuser2008 said:**
> Is there any good free video editor to use with my exilim camera for ubuntu?

```
brock@hops:~$ apt-cache search video editor
kino - Non-linear editor for Digital Video data
gaupol - subtitle editor for text-based subtitle files
gopchop - Fast, lossless cuts-only editor for MPEG2 video files
gstreamer0.10-gnonlin - non-linear editing module for GStreamer
gstreamer0.10-gnonlin-dev - development files of the non-linear editing module for GStreamer
kxgenerator - KDE X Server configuration utility
libmiracle0.2.5 - An open source multimedia framework - Core files
libmlt++-dev - An open source multimedia framework (C++ wrapper)
libmlt++0.2.5 - An open source multimedia framework (C++ wrapper)
libmlt-data - An open source multimedia framework - Core files
libmlt-dev - An open source multimedia framework - Development files
libmlt0.2.5 - An open source multimedia framework - Core files
libvalerie0.2.5 - An open source multimedia framework - Core files
pitivi - non-linear audio/video editor using GStreamer
subtitleeditor - Graphical subtitle editor with sound waves representation
videolink - assembles a DVD video filesystem from HTML pages and video files
avidemux - a free video editor - gtk version
avidemux-cli - a free video editor - command line version
avidemux-common - a free video editor - Internationalization files
avidemux-qt - a free video editor - qt version
openmovieeditor - a simple non-linear video editor
brock@hops:~$ 

```

Anything you find in the repositories will be free, by default.  Give one a try, and let us know if you have any problems.

---

### Post by perspectoff on 2009-05-02
> **Hospadar said:**
> There are a couple that I know of, just googling "linux video editors" will turn up some good results.

The biggest is probably cinelerra, which is, as much as I gather, very full featured and stable, although I think it's more targeted towards professionals and people who are real serious about video.  Also you'll have to build it yourself which might be sort of a pain.

Kdenlive comes in the repos and looks somewhat mature, you might want to give that a try first.

Also, depending on how well these tools work, you may want to first use a tool like ffmpeg/mencoder (command line) or avidemux (gui) to convert all your videos to some common format first.  

Except for cinelerra, all the software I mentioned is in the repositories (installable through synaptic)

Edit:
Here's a pretty good layout:
[http://jaypeeonline.net/freeware/free-video-editing-software-linux/](http://jaypeeonline.net/freeware/free-video-editing-software-linux/)

You don't have to build Cinelerra from scratch. That's silly. You can install it from their repositories.

See the instructions at Ubuntu guide (ubuntuguide.org): [http://ubuntuguide.org](http://ubuntuguide.org)

---

