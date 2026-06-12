---
title: "VLC help for guy at end of rope"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by ruffus910 on 2009-11-06
Okay, Im no expert in Ubuntu... I need help.

I dumped Windows completely to go to Ubuntu. Im running 9.10. When I want to play WMV files in VLC, it wont run audio. Yes, I know why it doesnt, but what i dont know is how to fix it. I would either like to make WMV files play audio in VLC, or convert WMV to something like AVI.

Ive been googling for days, and nobody seems to explain it in language that someone who isnt a software engineer could understand, or the info isnt nearly up to date.. Help please?

---

### Post by mjitkop on 2009-11-06
Hi there. Have you tried this?

[https://help.ubuntu.com/9.10/musicvideophotos/C/video-playback.html](https://help.ubuntu.com/9.10/musicvideophotos/C/video-playback.html)

Good luck. :)

---

### Post by GCoffee on 2009-11-06
Hi,

You said you knew why? If so please post why here. Also, check for any volume controls in VLC, and, although it may sound stupid, your volume is on and speakers are working.

If not have you installed the codecs? There under something similiar to "ubuntu extras" in the software centre, i'm not on a ubuntu installation currently, so cant double check.

Cheers,
GCoffee.

---

### Post by Lateralis on 2009-11-06
I don't think this is the problem as you can see the video, but I'll mention it anyway just in case!  

In order to play .wmv files you will need some additional codecs that don't come bundled with Ubuntu by default due to copyright restrictions.  Medibuntu ([http://www.medibuntu.org/](http://www.medibuntu.org/)) will tell you how to install codecs for Windows, if you haven't done that already.

---

### Post by sandyd on 2009-11-06
> **Lateralis said:**
> I don't think this is the problem as you can see the video, but I'll mention it anyway just in case!  

In order to play .wmv files you will need some additional codecs that don't come bundled with Ubuntu by default due to copyright restrictions.  Medibuntu ([http://www.medibuntu.org/](http://www.medibuntu.org/)) will tell you how to install codecs for Windows, if you haven't done that already.
in that case...
@OP
run this in the terminal
```

sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update[FONT=Verdana]

```

for 64bit
```

sudo apt-get install w64codecs ubuntu-restricted-extras
sudo apt-get remove flashplugin-installer
[/FONT]wget -c http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
tar xvfz libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
sudo mv libflashplayer.so /usr/lib/firefox/plugins/libflashplayer.so
rm libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
[FONT=Verdana]
```

for 32bit
```

sudo apt-get install w32codecs ubuntu-restricted-extras

```
[/FONT]

---

### Post by ruffus910 on 2009-11-06
Thx guys. It turns out i just didnt have the codecs... told you i was no expert!

This is exactly why I switched to Linux from Windows. The ability of the community to be able to help you with a problem. Thank you so much.

---

