---
title: "Cannot Get Firefox to Play Videos - YouTube or Otherwise"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by demarshall on 2009-02-10
Even though I've been using Kubuntu for some time, I still consider myself a newbie. Every once in a while I seem to get most things working and then something happens and I have more trouble.

Something has happened in the last couple of days or perhaps the past week because I was able to run videos at least some of the time before but I cannot run any now. Please help me with this.

Thanks in advance for your help.

---

### Post by sumguy231 on 2009-02-10
Could you go to 'about:plugins' in the location bar and paste the output here?

---

### Post by JK3mp on 2009-02-10
Have you tried this. [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by RomeReactor on 2009-02-10
Hi. You have Kubuntu 32 bit, right? Do the videos work in Konqueror (or Opera if you have it installed)?

As mentioned before, enter 
```
about:plugins
```
in Firefox's address bar; if you have Flash installed, it should be the last entry in the page:
> [B]Shockwave Flash

    File name: libflashplayer.so[/B]

If you don't have it, and Flash doesn't work in Konqueror either, close Firefox, open a Konsole and run the following:
```
sudo aptitude purge mozilla-plugin-gnash gnash-common gnash
```
Then:
```
sudo aptitude install flashplugin-nonfree
```
Now open Firefox again and see if Flash works.

---

### Post by demarshall on 2009-02-10
> **sumguy231 said:**
> Could you go to 'about:plugins' in the location bar and paste the output here?


I noticed when I looked there that there are many plugins. Did you want me to past the whole thing or just certain sections? I also noticed that I have a few Flash plugins. Can I clean them out and reinstall the newest one or just delete the older ones?

Thanks for any help in advance.

---

### Post by RomeReactor on 2009-02-10
If you have more than one Flash plugin, try running the commands posted above.

---

### Post by demarshall on 2009-02-10
I tried doing the purge as suggested and in order to attempt to get rid of earlier versions of flashplugin-nonfree, I purged that too. I still have three entries for Flash in my about:plugins:

Shockwave Flash

    File name: libswfdecmozilla.so
    Shockwave Flash 9.0 r999

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Adobe Flash movie 	swf 	Yes
application/futuresplash 	FutureSplash movie 	spl 	Yes


Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 r12

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r124

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

I presume the version 9 files are not supposed to be there. Is that correct? If so, how do I get rid of them?

Thanks again for your help.

---

### Post by demarshall on 2009-02-10
> **JK3mp said:**
> Have you tried this. [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Is there a part of that message that is relevant based on what else I have shared since you posted this message?

---

### Post by RomeReactor on 2009-02-10
> **demarshall said:**
> I tried doing the purge as suggested and in order to attempt to get rid of earlier versions of flashplugin-nonfree, I purged that too. I still have three entries for Flash in my about:plugins:

Shockwave Flash

    File name: libswfdecmozilla.so
    Shockwave Flash 9.0 r999
You need to uninstall **swfdec-mozilla** as well:
```
sudo aptitude purge swfdec-mozilla
```


> Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 r12

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r124

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

I presume the version 9 files are not supposed to be there. Is that correct? If so, how do I get rid of them?

Thanks again for your help.

Yes, you have two versions of Flash installed; not sure if they conflict with each other, but it's likely. Did you install one of them manually--probably Flash 9?

First uninstall swfdec-mozilla and see if Flash works then (remember to restart Firefox afterwards); if not, try uninstalling the version you just installed:
```
sudo aptitude purge flashplugin-nonfree
```
Then run the following to get rid of any libflashplayer.so files left remaining:
```
updatedb; for x in `locate libflashplayer.so`; do rm $x; done
```
And re-install Flash again:
```
sudo aptitude install flashplugin-onfree
```

---

### Post by demarshall on 2009-02-10
I found that I had an Adobe plugin as well and so purged it using:

sudo aptitude purge adobe-flashplugin

YouTube seems to be working now but I will follow what was just written to try to make it so that I just have one Flash plugin but I have to go out for a few hours first.

Thanks so much for your help RomeReactor.

---

### Post by RomeReactor on 2009-02-10
Note this in my previous post :
```
updatedb; for x in `locate libflashplayer.so`; do rm $x; done
```
it should be:
```
sudo updatedb; for x in `locate libflashplayer.so`; do rm $x; done
```

As it seems to be working now, before you try to remove more files enter "about: plugins" in Firefox and see if it only lists one plugin; if so, there's no need to do anything else.

---

### Post by demarshall on 2009-02-11
I have now done what you previously told me to do:

sudo aptitude purge swfdec-mozilla

and

sudo aptitude purge swfdec-mozilla

I get a permission error when I try the following though:

sudo updatedb; for x in `locate libflashplayer.so`; dorm $x; done

Any idea why that would be?

Thanks so much for your assistance with this.

---

### Post by theozzlives on 2009-02-11
Why don't you install the kubuntu-restricted-extras?

---

### Post by demarshall on 2009-02-11
I tried adding another sudo like this and the prompt just came back:

sudo updatedb; for x in `locate libflashplayer.so`; do sudo rm $x; done

Now I don't see any Flash in the About:Plugins page so I'll reinstall the latest and see what happens.

Forgot to mention that when I ran the following command, it uninstalled Gnome:

sudo aptitude purge swfdec-mozilla 

I guess I'll reinstall Gnome now. Any idea how to do that and make it so that I can choose whether Gnome or KDE starts when I log in?

---

### Post by RomeReactor on 2009-02-11
> **demarshall said:**
> 
I get a permission error when I try the following though:

sudo updatedb; for x in `locate libflashplayer.so`; **dorm** $x; done

Are you sure this is not a typo? It should be:
```
sudo updatedb; for x in `locate libflashplayer.so`; **do rm** $x; done
```

> I guess I'll reinstall Gnome now. Any idea how to do that and make it so that I can choose whether Gnome or KDE starts when I log in?
The package you should have is **ubuntu-desktop**, not gnome.

---

### Post by demarshall on 2009-02-11
> **theozzlives said:**
> Why don't you install the kubuntu-restricted-extras?

This might be a silly question but which ones?

---

### Post by RomeReactor on 2009-02-11
The kubuntu-restricted-extras is a metapackage that installs many other useful packages, including Flash.

---

### Post by demarshall on 2009-02-11
Would you recommend installing kubuntu-restricted-extras now that I have videos working in Firefox?

---

### Post by RomeReactor on 2009-02-11
> **demarshall said:**
> Would you recommend installing kubuntu-restricted-extras now that I have videos working in Firefox?

It's really up to you; it won't uninstall flashplugin-nonfree. This is Synaptic's description of **kubuntu-restricted-extras**:
> Commonly used restricted packages
This package depends on some commonly used packages in the Kubuntu
multiverse repository.

Installing this package will pull in support for MP3 playback and decoding,
Java runtime environment, Flash plugin, DVD playback, and LAME (to create
compressed audio files).

Please note that this does not install libdvdcss2, and will not let you play
encrypted DVDs. For more information, see
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs).

Please also note that packages from multiverse are restricted by copyright
or legal issues in some countries. See
[http://www.ubuntu.com/ubuntu/licensing](http://www.ubuntu.com/ubuntu/licensing)
for more information.

The packages it installs are:

* flashplugin-nonfree (Flash)
* icedtea6-plugin (Java plugin for browsers)
* libxine1-ffmpeg (Media codec)
* libavcodec-unstripped-51 (Media codec)
* libdvdread3 ( DVD playback library)
* libk3b-extracodecs (Media codecs for K3B)
* libmp3lame0 (MP3 encoder)
* unrar (non-free version)
* libtunepimp5-mp3 (MP3 Plugin for MusicBrainz tagging library)
* sun-java6-jre (Java runtime environment)
* msttcorefonts (Microsoft fonts)

---

### Post by demarshall on 2009-02-11
RomeReactor, I want to thank you ever so much for all your help. I greatly appreciate it.

Now all I'm hoping for is that I will be able to choose the window manager that I want at login.

---

### Post by RomeReactor on 2009-02-11
> **demarshall said:**
> RomeReactor, I want to thank you ever so much for all your help. I greatly appreciate it.

Now all I'm hoping for is that I will be able to choose the window manager that I want at login.

You're very welcome.

If you installed the ubuntu-desktop package, and have at least one other *-desktop package, such as kubuntu-desktop, xubuntu-desktop, etc., then the option should show up at the login screen.

---

### Post by demarshall on 2009-02-11
> **RomeReactor said:**
> You're very welcome.

If you installed the ubuntu-desktop package, and have at least one other *-desktop package, such as kubuntu-desktop, xubuntu-desktop, etc., then the option should show up at the login screen.

Thanks so much for all your help. You've made the impossible quite simple.

---

