---
title: "watch youtube in ubunutu 9.04"
date: 2009-08-22
forum: New to Ubuntu
---

### Post by amarumayo on 2009-08-22
Hi all,

Does anyone know how to watch youtube in Ubuntu 9.04?  It tells me I need to install flash player but I cannot get it to work.
Thanks,
Chris

---

### Post by BackwardsDown on 2009-08-22
I allways recommend to install "ubuntu-restricted-extras", you can find it in synaptic or run "sudo apt-get install ubuntu-restricted-extras" in the commandline.

Good luck!

---

### Post by JerichoKru on 2009-08-22
Either download flash from the repos (synaptic is easier, just search for flash)

OR

Go to the adobe site and download the .deb version of flash and install.

---

### Post by dannyboy79 on 2009-08-22
> **amarumayo said:**
> Hi all,

Does anyone know how to watch youtube in Ubuntu 9.04?  It tells me I need to install flash player but I cannot get it to work.
Thanks,
Chris

don't know if the ubuntu-restricted-package or whatever the guy above me says will work but I know that I enable all repositories and then i install adobe-flashplugin and youtube works just fine (all flash websites for that matter) in 9.04 32bit

---

### Post by markharding557 on 2009-08-22
> **dannyboy79 said:**
> don't know if the ubuntu-restricted-package or whatever the guy above me says will work but I know that I enable all repositories and then i install adobe-flashplugin and youtube works just fine (all flash websites for that matter) in 9.04 32bit

ubuntu-restricted-extras is a meta packaage which installs flash,java and codecs and a other stuff

---

### Post by dannyboy79 on 2009-08-25
> **markharding557 said:**
> ubuntu-restricted-extras is a meta packaage which installs flash,java and codecs and a other stuff

yeah, i see that now. aptitude says this:
Package: ubuntu-restricted-extras
State: installed
Automatically installed: no
Version: 31
Priority: optional
Section: multiverse/metapackages
Maintainer: Michael Vogt <michael.vogt@ubuntu.com>
Uncompressed Size: 32.8k
Recommends: gstreamer0.10-plugins-ugly, gstreamer0.10-plugins-ugly-multiverse,
            ttf-mscorefonts-installer, adobe-flashplugin | flashplugin-nonfree,
            unrar, gstreamer0.10-plugins-bad,
            gstreamer0.10-plugins-bad-multiverse, gstreamer0.10-ffmpeg,
            libavcodec-unstripped-52, gstreamer0.10-pitfdll
Description: Commonly used restricted packages
 This package depends on some commonly used packages in the Ubuntu multiverse
 repository. 
 
 Installing this package will pull in support for MP3 playback and decoding,
 support for various other audio formats (GStreamer plugins), Microsoft fonts,
 Java runtime environment, Flash plugin, LAME (to create compressed audio
 files), and DVD playback. 

but i thought installing flashplugin-nonfree was not advised. at least I don't have it installed on my system and my flash works fine.

---

### Post by hubertofliege on 2009-08-25
I've installed flash, but it doesn't work correctly.  Some things work.  I can view certain flash sites, and youtube works, however many others don't.  Its strange.  The symptoms:

-Pandora won't work.  It will load pandora about a third of the way, then it stops and says its done.  Also, pandora looks slightly off, like its not in proper resolution, its very subtle.

-Adults Swim's video player will show videos, but the controls don't seem to work.

-Youtube works, but it also has control problems.  Sometimes I will pause and it won't want to start back up.  I have problems sliding the progress marker to a point I want to watch.

-Some embeded video players, like on theonion.com, simply don't load.

I have the restriced extras package and adobe Flash 10.  Is there some way to uninstall it and try again?

Oh, I'm running Jaunty on a Dell Latitude laptop.

---

