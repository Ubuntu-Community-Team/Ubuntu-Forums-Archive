---
title: "How do I view Quicktime vids?"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by BunnyDee on 2010-10-20
I would like to find a way that would allow me to watch Quicktime videos with Ubuntu, using my Google Chrome browser. I need to be able to 'naturally' click on 'watch video' links etc, and, even when the vid involved is a Quicktime one, only allowing 'other OS' users to watch them, to still do so anyway. How may I be able to do it?

Oh, an example would be the website [http://trailers.apple.com/trailers/summit/red/](http://trailers.apple.com/trailers/summit/red/) where I just tried to watch the trailers they show, and eventually resorted to finding each one of them on youtube, but the question is one I often have, when I try to watch Quicktime videos. For some reason they seem to be quite prominent, even if they don't make things easy for... us, and avoiding the hassle would be wonderful, since I only watch these trailers when I have a few moments to relax...

---

### Post by M!K3_$ on 2010-10-20
Add/Remove

Search for quicktime. there should be some gstreamer codecs. Install them

---

### Post by M!K3_$ on 2010-10-20
i think the gstreamer0.10-plugins-good has the quicktime codecs in it. but i can't remember for sure.

---

### Post by BunnyDee on 2010-10-21
Thank you for the suggestion, but it seems that, when I search for Quicktime in the Software Center, the first two results I get there are GStreamer, indeed, and VLC, but Chrome still refuses to play those videos. Is it possible that they're automatically applies to Firefox or something, and, if so, how would I make them apply to Chrome as well?

---

### Post by wojox on 2010-10-21
Have you installed

```
sudo apt-get update; sudo apt-get install ubuntu-restricted-extras
```

Plays fine for me. Looks like a good movie as well.

---

### Post by BunnyDee on 2010-10-21
UPDATE:
I've just tried viewing the videos in the example-page I gave above through Firefox, and again it prompts me to install Quicktime (although it says there that it's only available free for Mac and... PC - which it seems to assume means 'Windows', huh?, I download the Installer there as prompted, but Archive Manager encounters an error with it.

Output:
```
Archive:  /tmp/QuickTimeInstaller.exe
[/tmp/QuickTimeInstaller.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /tmp/QuickTimeInstaller.exe or
          /tmp/QuickTimeInstaller.exe.zip, and cannot find /tmp/QuickTimeInstaller.exe.ZIP, period.
```

---

### Post by BunnyDee on 2010-10-21
Hmmm, just saw that on replying. Trying it as we speak.

---

### Post by BunnyDee on 2010-10-21
...and, again, same error...

It says that ubuntu-restricted-extras is already the newest version.

---

### Post by wojox on 2010-10-21
Open Firefox and type in 

```
about:plugins
```

You should see QuickTime Plug-in 7.6.6

---

### Post by migs73 on 2010-10-21
> **wojox said:**
> Open Firefox and type in 

```
about:plugins
```

You should see QuickTime Plug-in 7.6.6

+1 Works for me on the links you gave.

---

### Post by BunnyDee on 2010-10-22
I tried. I really tried. Promise. It's just that... well, it doesn't seem to have a QuickTime plugin of any sort. Not in Firefox, where I checked the way you said to, wojox, not in Chrome, whjich I use, nowhere. I just really don't know where to get it from, and how to install it.

(by the way, migs73, love the Saltire-Penguin!)

---

### Post by wojox on 2010-10-22
> **BunnyDee said:**
> I tried. I really tried. Promise. It's just that... well, it doesn't seem to have a QuickTime plugin of any sort. Not in Firefox, where I checked the way you said to, wojox, not in Chrome, whjich I use, nowhere. I just really don't know where to get it from, and how to install it.

(by the way, migs73, love the Saltire-Penguin!)

Open synaptic and search for libquicktime, it should have been installed when you installed ubuntu-restricted-extras, weird.

---

### Post by beew on 2010-10-22
Install Mozplugger.

---

