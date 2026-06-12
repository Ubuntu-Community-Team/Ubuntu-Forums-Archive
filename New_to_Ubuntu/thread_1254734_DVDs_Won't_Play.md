---
title: "DVDs Won't Play"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by Sparty26 on 2009-08-31
Hey, I am back again, folks. I can't seem to get DVD's to play on my computer. Everytime I try to open a DVD in Movie Player, it says:

> The required software to play this file is not installed. You need to install suitable plugins to play media files. Do you want to search for a plugin that supports the selected file?

The search will also include software which is not officially supported.

When I search, it comes up with:

> No packages with the requested plugins found

The requested plugins are:

DVD source

I have tried searching through old threads and I haven't found any fixes yet. Any suggestions?

---

### Post by sandyd on 2009-08-31
you need
libdvdcss2

---

### Post by credobyte on 2009-08-31
And ubuntu-restricted-extras ( w32codecs and non-free-codecs from Mediabuntu could be an advantage ).

---

### Post by colau on 2009-08-31
> **Sparty26 said:**
> Hey, I am back again, folks. I can't seem to get DVD's to play on my computer. Everytime I try to open a DVD in Movie Player, it says:

When I search, it comes up with:



I have tried searching through old threads and I haven't found any fixes yet. Any suggestions?

```

sudo aptitude install w32codecs
sudo aptitude install libdvdcss2
sudo aptitude install ubuntu-restricted-extras

```

---

### Post by donkyhotay on 2009-08-31
Here is the link to the [help information](https://help.ubuntu.com/community/RestrictedFormats/) you are looking for. Don't forget google when looking for help as well.

---

### Post by jpeddicord on 2009-08-31
> **colau said:**
> ```

sudo aptitude install w32codecs
sudo aptitude install libdvdcss2
sudo aptitude install ubuntu-restricted-extras

```

The first two will not work without enabling the [Medibuntu]("http://medibuntu.org/") repository.

---

### Post by Sparty26 on 2009-09-01
Thanks for the help, everyone. I have DVDs "playing" now, but the playback is extremely choppy and I can't get to the menu. Any ideas?

---

### Post by SunnyRabbiera on 2009-09-01
> **Sparty26 said:**
> Thanks for the help, everyone. I have DVDs "playing" now, but the playback is extremely choppy and I can't get to the menu. Any ideas?

I say dont use totem (movie player in your menu), instead I might suggest give VLC, SMplatyer or xine-ui a shot.
Them if needed uninstall totem gstreamer and install totem-xine

---

