---
title: "DVDs will not play and I've tried everything"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by fordguydude on 2010-06-02
Title says it all. 

I've installed libdvdread4. I've installed restricted extras package. I've ran this--

 sudo /usr/share/doc/libdvdread4/install-css.sh

and get this

```
--2010-06-01 23:07:50--  http://packages.medibuntu.org/dists/lucid/free/binary-amd64/Packages
Resolving packages.medibuntu.org... 88.191.82.11
Connecting to packages.medibuntu.org|88.191.82.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8080 (7.9K) [text/plain]
Saving to: `/tmp/dvdcss-QkQcpD/Packages'

100%[======================================>] 8,080       --.-K/s   in 0.1s    

2010-06-01 23:07:51 (55.3 KB/s) - `/tmp/dvdcss-QkQcpD/Packages' saved [8080/8080]

--2010-06-01 23:07:51--  http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb
Resolving packages.medibuntu.org... 88.191.82.11
Connecting to packages.medibuntu.org|88.191.82.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 38080 (37K) [application/octet-stream]
Saving to: `/tmp/dvdcss-QkQcpD/libdvdcss.deb'

100%[======================================>] 38,080      86.5K/s   in 0.4s    

2010-06-01 23:07:52 (86.5 KB/s) - `/tmp/dvdcss-QkQcpD/libdvdcss.deb' saved [38080/38080]

(Reading database ... 149943 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.10-0.3medibuntu1 (using .../dvdcss-QkQcpD/libdvdcss.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.10-0.3medibuntu1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

I've tried using VLC player and that won't play. I've installed xine, that won't play it. I am out of ideas and Google just brings me back to everything that I've already done. When I put in a DVD, movie player opens but won't start the dvd. All I get is a blank screen, no error message. 

Any help would be great.

---

### Post by 4Orbs on 2010-06-02
In these forums, in the Multimedia and Video section is a sticky post titled "[Comprehensive Multimedia and Video HowTo]("http://ubuntuforums.org/showthread.php?t=766683")" and it has worked for me for any Ubu,Xubu,Kubuntu I've ever tried. I recommend following it from top to bottom for your specific version of Ubuntu. Don't worry about it accidentally installing something again that you've already installed.

---

### Post by nhasian on 2010-06-02
it sounds like you did it right to me.  when you insert the dvd into the drive, is the disc detected? does it show the title of the disc?

---

### Post by fordguydude on 2010-06-02
Thanks for your reply.

I've just put in 

```
sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs ia32-sun-java6-bin icedtea6-plugin libmp3lame0 non-free-codecs openjdk-6-jre unrar
```

I'll reboot once it's finished and see if it works.  

*crosses fingers*

---

### Post by fordguydude on 2010-06-02
This just came up--

[img]http://img248.imageshack.us/img248/9901/uhohu.png[/img]

I can't press enter or anything to get out of it and accept. 

How do I ok it?

---

### Post by 4Orbs on 2010-06-02
You use the right and left arrow keys on the keyboard to highlight your choice then hit enter.

This is only the first step in the How-To, and this isn't the step that gets your dvd working.

---

### Post by Ozymandias_117 on 2010-06-02
Try tab

---

### Post by fordguydude on 2010-06-02
Thanks. License accepted. I wish I would of read it on the how-to page. It told me how! *smacks head*

I think it's done. It now says---

```
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

---

### Post by 4Orbs on 2010-06-02
Some of those steps take a little while to complete. When each one is finished the terminal will stop at: yourname@whatever:~$ at which point you move on to the next step. The how-to will get all your multimedia and flash and java stuff working well.. so long as you don't make a mistake somewhere along the line. Like, don't stop the terminal while it's still running something.

---

### Post by fordguydude on 2010-06-02
Okay. 

Update--
I don't know what I did except follow the steps and troubleshooting and reboot, but it now works--only halfway. 

The previews were very "salty and grainy" but the DVD menu works great. When I try to go to a screen selection, it just freezes. I've tried it in VLC, and it won't show picture but it will play audio. 

Slowly....making....progress

[img]http://img688.imageshack.us/img688/1392/moviess.png[/img]

---

### Post by 4Orbs on 2010-06-02
I'm assuming you have already activated the driver for your computer's graphics card (if there is one available for your card) in the Ubuntu menu System>> Administration>> Hardware Drivers? And if you have activated the driver, you might now trying turning off the desktop effects before playing a video System>> Preferences>> Appearance>> Effects tab.

EDIT: And in the how-to under the DVD Playback and Ripping section you read the part about disabling interlacing in VLC?

---

### Post by fordguydude on 2010-06-02
Both the drivers are activated. I disabled the effects. Still the same. 

[img]http://img688.imageshack.us/img688/1392/moviess.png[/img]

---

### Post by 4Orbs on 2010-06-02
And it looks the same in either movie player? You say both the drivers are activated... do you mean the graphics driver and the wireless driver? Or have you activated two different video drivers?

---

### Post by fordguydude on 2010-06-02
Thanks for the reply.

When I said both I should of been clearer. I have a graphics card and a wireless card.

It does look the same in both VLC and Totem. 

What I don't understand is that to play DVD's on my desktop (I'm on my laptop now) I just run totem-xine. I can't seem to get that on this computer. My desktop is 9.04.

---

### Post by 4Orbs on 2010-06-02
When you followed the how-to did you see the part about adding the xine bits? The how-to says it's not necessary, but for some it is necessary. I'm not sure that is your problem, however.

EDIT: disregard, I just saw the answer in your first post.

---

### Post by Legendary_Bibo on 2010-06-02
Look up the Medibuntu repository (on google). Find the 'PPA' and add it into your software sources then go to synaptic and look for 'libdvdcss' and install it. See if that helps.

---

### Post by mc4man on 2010-06-02
Try going into home folder and deleting the .dvdcss folder, then try vlc again. 

(.dvdcss is a hidden folder, if you don't see then go view -> show hidden files or Ctrl+h 
see screen - note - you should add your screenshots as attachments - plus you'll find Alt+Prnt Scrn useful to capture only a window

If still no good, open a terminal and use this to test a different video output

```
vlc --vout x11 dvd://
```

---

### Post by gandaran on 2010-06-02
hi, 
go to vlc preferences and change the video output driver to x11 or xv, one of them should work fine.
you can also do the same for totem by typing in terminal *gstreamer-properties*

---

### Post by Jakiejake on 2010-06-02
Use VLC
EDIT: I should read the previous threads LOL
Good Luck!

---

### Post by fordguydude on 2010-06-02
> **mc4man said:**
> Try going into home folder and deleting the .dvdcss folder, then try vlc again. 

(.dvdcss is a hidden folder, if you don't see then go view -> show hidden files or Ctrl+h 
see screen - note - you should add your screenshots as attachments - plus you'll find Alt+Prnt Scrn useful to capture only a window

If still no good, open a terminal and use this to test a different video output

```
vlc --vout x11 dvd://
```

You, my friend, are brilliant. 

THANK YOU!!!!!! I deleted the folder and everything is now crystal clear in VLC. 

Thank you to everyone else who responded as well. I _sincerely_ appreciate it.

---

### Post by Jakiejake on 2010-06-02
> **fordguydude said:**
> You, my friend, are brilliant. 

THANK YOU!!!!!! I deleted the folder and everything is now crystal clear in VLC. 

Thank you to everyone else who responded as well. I _sincerely_ appreciate it.

AWESOME
Enjoy

---

