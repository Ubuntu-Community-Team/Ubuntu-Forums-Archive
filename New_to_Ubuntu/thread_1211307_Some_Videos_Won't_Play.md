---
title: "Some Videos Won't Play"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by Teasdale on 2009-07-12
I have Ubuntu 9.04, I've done "sudo apt-get install ubuntu-restricted-extras." YouTube vidoes will play, but almost nothing else.

If I try to play a streaming video that says "view in flash," I get a pop-up box with a black screen. The same file will play in my other PC with Ubuntu 8.10.

With an .asx file, I get a screen with a picture of a blank slide (properties say "Totem Browser Plugin 2.26.1 Browser Plugin using GStreamer 0.10.22"); if  I right-click and choose the "play in movie player," option it says "Could not open location; you might not have permission to open the file."

In my Firefox Plug-ins, this is what's installed:

------------------------------------

Default Plugin

Demo Print Plugin for unix/linux

DivX Web Player 1.4.0.233

IcedTea Java Web Browser Plugin 1.4.1

QuickTime Plug-in 7.2.0 ("The Totem 2.26.1 plugin handles video and audio streams")

Shockwave Flash 10.0 r22

Shockwave Flash 9.0 r999 (disabled; I can't find anywhere that it's installed to uninstall it, and Firefox Plugins doesn't have an uninstall option)

VLC Multimedia Plugin (compatible Totem 2.26.1)

Windows Media Player Plug-in (compatible; Totem) ("The Totem 2.26.1 plugin handles video and audio streams")

Xine Plugin 1.0.2; Windows Media Player/Real Player/QuickTime compatible.

------------------------------

In my synaptic package manager, I see listed as installed that look relevant:

firefox-3.0
firefox-3.0-branding
firefox-3.0-gnome-support
firefox-gnome-support
flashpluginin-installer
gnome-codec-install
gnome-media
gnome-media-common
gstreamer0.10 (many files listed)
swfdec-mozilla
totem-common
totem-gstreamer
totem-mozilla
totem-plugins
ubuntu-restricted-extras

---------------------------

My synaptic package manager says these are NOT installed; would any of them help?

flashplugin-nonfree (I do have swf in my FF plugins)
swfdec-gnome
libswfdec-0.6-90
libswfdec-0.7-1 (and other Flash decoder libraries)
gnash (free swf movie player)

------------------------------

When I type into terminal: 
sudo locate libflashplayer.so

This is the response:
/usr/lib/flashplugin-installer/libflashplayer.so
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so

---

### Post by earthpigg on 2009-07-12
lets try this, just to make sure the recommended packages to come with ubuntu-restricted-extras are indeed installed:

```
sudo apt-get install --install-recommends ubuntu-restricted-extras
```

dpkg, apt-get, synaptic, and aptitude all have tools to 'automatically' remove things you dont '*need*' any more.... since 90% of ubuntu-restricted-extras are things listed as '*recommended*' and not '*needed*', one of those tools could have mistakenly removed some stuff that should not have been.

---

### Post by Teasdale on 2009-07-12
```
sudo apt-get install --install-recommends ubuntu-restricted-extras
```

OK, I did that, and this is what came back:

```

Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by nhasian on 2009-07-12
are you running ubuntu 32 bit or 64 bit?  if flash is working in youtube, it should work anywhere.  can you show us a page that is giving you problems?

---

### Post by philinux on 2009-07-12
to find the flash plugin use this.
```

sudo updatedb

then 

locate libflashplayer.so
```

---

### Post by ajgreeny on 2009-07-12
If I were you I would install the w32codecs from [medibuntu]("https://help.ubuntu.com/community/Medibuntu"), get rid of the swfdec-mozilla application you have installed and replace it with adobe-flashplugin.  I would also uninstall totem-mozilla and replace it with either mozilla-mplayer or gecko-mediaplayer, both of which work much better in my experience.  Some people swear by vlc and the mozill-plugin-vlc, but I prefer the others I mention.

Check them out and see if anything is working better.

---

### Post by 1roxtar on 2009-07-12
I'm having a similar problem.  I can view and listen Youtube videos but not Myspace videos or music.  I thought that if I could play flash videos from one place, I should be able to play them on any site. Weird....

---

### Post by 1roxtar on 2009-07-12
> **ajgreeny said:**
> If I were you I would install the w32codecs from [medibuntu]("https://help.ubuntu.com/community/Medibuntu"), get rid of the swfdec-mozilla application you have installed and replace it with adobe-flashplugin.  I would also uninstall totem-mozilla and replace it with either mozilla-mplayer or gecko-mediaplayer, both of which work much better in my experience.  Some people swear by vlc and the mozill-plugin-vlc, but I prefer the others I mention.

Check them out and see if anything is working better.

Removing the swfdec-mozilla app from the Synaptic Package Manager did the trick.  I can now watch and listen to Myspace videos and music.  As always, the Community knows their stuff and I tip my hat to all of you for your generous help.  Thank you!!!

:guitar:

---

### Post by Teasdale on 2009-07-12
> **nhasian said:**
> are you running ubuntu 32 bit or 64 bit?

64 bit.

---

### Post by Teasdale on 2009-07-13
> **ajgreeny said:**
> If I were you I would install the w32codecs from [medibuntu]("https://help.ubuntu.com/community/Medibuntu"), get rid of the swfdec-mozilla application you have installed and replace it with adobe-flashplugin.  I would also uninstall totem-mozilla and replace it with either mozilla-mplayer or gecko-mediaplayer, both of which work much better in my experience.  Some people swear by vlc and the mozill-plugin-vlc, but I prefer the others I mention.


I got rid of swfdec-mozilla and installed adobe-flashplugin from the synaptic package manager. I  uninstalled totem-mozilla and replaced it with gecko-mediaplayer.

I tried mozilla-mplayer first, but all I get is a gray box (I've never seen mplayer do anything else in any PC I've had).

I went to the Medibuntu site, but I didn't download the 32 bit codecs because I have a 64 bit computer. I did download the 64 bit codecs, and it said I already had all of them.

One site now plays (albeit on a tiny thumb-nail sized screen) via gecko-mediaplayer. The other seems like it might work, but I have to wait til they have something live to broadcast again to test it - it appears to be working, but shows nothing because there's nothing to show.

YouTube now shows only a blank white screen.

---

### Post by Teasdale on 2009-07-13
I reinstalled swfdec-mozilla and totem-mozilla, and uninstalled gecko-mediaplayer. I'm back to square one, but YouTube works again.

---

### Post by Teasdale on 2009-07-13
Still playing with it - I installed the vlc-mozilla plugin, but didn't remove anything. And YouTube gave me a blank white screen again. So I uninstalled it, and I can play YouTube again, but not the other videos.

---

### Post by nhasian on 2009-07-14
You said you were using 64 bit ubuntu right?  uninstall all the flash junk you have now because even the adobe flash in the repos installs the 32bit flash plugin with the nswrapper.  go to adobe's website and download the 64 bit alpha adobe flash:

[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz)

unzip the file libflashplayer.so and copy it to /usr/lib/mozilla/plugins/

```
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/libflashplayer.so
```


now give it a try!

---

### Post by vinutux on 2009-07-14
uninstall any of shockwave flash plgins....

both may clash each other.....

---

### Post by Teasdale on 2009-07-14
I did this:

uninstall all the flash junk you have now because even the adobe flash in the repos installs the 32bit flash plugin with the nswrapper. go to adobe's website and download the 64 bit alpha adobe flash:

[http://download.macromedia.com/pub/l...6_64.so.tar.gz](http://download.macromedia.com/pub/l...6_64.so.tar.gz)

unzip the file libflashplayer.so and copy it to /usr/lib/mozilla/plugins/

and I uninstalled everything with the "flash" in it that I could find in my synaptic manager. I had to re-download Adobe Flash. YouTube works, and one of the other sites using an archived .wmv file appears to work but this one still doesn't work. It says I don't have permission to open the file:

[http://energy10.egihosting.com/461624](http://energy10.egihosting.com/461624)

---

### Post by philinux on 2009-07-14
> **Teasdale said:**
> I did this:

uninstall all the flash junk you have now because even the adobe flash in the repos installs the 32bit flash plugin with the nswrapper. go to adobe's website and download the 64 bit alpha adobe flash:

[http://download.macromedia.com/pub/l...6_64.so.tar.gz](http://download.macromedia.com/pub/l...6_64.so.tar.gz)

unzip the file libflashplayer.so and copy it to /usr/lib/mozilla/plugins/

and I uninstalled everything with the "flash" in it that I could find in my synaptic manager. I had to re-download Adobe Flash. YouTube works, and one of the other sites using an archived .wmv file appears to work but this one still doesn't work. It says I don't have permission to open the file:

[http://energy10.egihosting.com/461624](http://energy10.egihosting.com/461624)

Or copy libflashplayer.so to

~/.mozilla/plugins

---

### Post by Teasdale on 2009-07-15
> **philinux said:**
> Or copy libflashplayer.so to

~/.mozilla/plugins

I don't see any folder named .mozilla anywhere.

---

### Post by acimmarusti on 2009-07-15
It's in /home/username/, but it's hidden. To view it, type:

```
ls -a
```

Also, if what you tried doesn't work, I would probably remove the flashplugin-installer packages and install the flashplugin-nonfree one (this one should automatically add the library needed to the .mozilla hidden directory)

Good luck

---

### Post by vinutux on 2009-07-15
> **acimmarusti said:**
> It's in /home/username/, but it's hidden. To view it, type:

```
ls -a
```

Also, if what you tried doesn't work, I would probably remove the flashplugin-installer packages and install the flashplugin-nonfree one (this one should automatically add the library needed to the .mozilla hidden directory)

Good luck

**Ctrl+h** in nautilus....ls -a is in terminal

---

