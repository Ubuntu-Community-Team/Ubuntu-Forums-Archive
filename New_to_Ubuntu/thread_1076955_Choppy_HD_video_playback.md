---
title: "Choppy HD video playback"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by Onoskelis on 2009-02-21
I have a lot of 720p/1080p videos, but they all play terribly no matter when video player I use. I have used Mplayer, VLC, Totem, and a few other, but it all resulted in choppy playback and mediocre video quality. HD videos on youtube are also very slow.

I know it's not a hardware issue because they work perfectly in XP and Vista. My videocard is an Nvidia 8800GT, and the CPU is a Core 2 Duo 2.66 GHz.

Does anyone know what the issue is? Thanks.

---

### Post by RomeReactor on 2009-02-21
Hi. Make sure you have the nVidia driver installed in 'System->Administration->Hardware Drivers'.

---

### Post by Onoskelis on 2009-02-21
> **RomeReactor said:**
> Hi. Make sure you have the nVidia driver installed in 'System->Administration->Hardware Drivers'.

Yes I installed the restricted Nvidia drivers already.

---

### Post by RomeReactor on 2009-02-21
Do you have the Medibuntu repositories? If so, make sure you have the following installed:
```
sudo aptitude install gstreamer0.10-fluendo-mpegdemux gstreamer0.10-ffmpeg gstreamer0.10-packagekit gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
```

---

### Post by Onoskelis on 2009-02-21
> **RomeReactor said:**
> Do you have the Medibuntu repositories? If so, make sure you have the following installed:
```
sudo aptitude install gstreamer0.10-fluendo-mpegdemux gstreamer0.10-ffmpeg gstreamer0.10-packagekit gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
```

Oh god I think that made it worse ;)

I guess HD media and Linux don't work very well together.

---

### Post by RomeReactor on 2009-02-21
> **Onoskelis said:**
> Oh god I think that made it worse ;)

I guess HD media and Linux don't work very well together.

I could play 720p videos in a Sempron 2800+ (1.6 Ghz) and a GeForce 6200 in Ubuntu, so that's probably a problem with your configuration.

---

### Post by Onoskelis on 2009-02-21
> **RomeReactor said:**
> I could play 720p videos in a Sempron 2800+ (1.6 Ghz) and a GeForce 6200 in Ubuntu, so that's probably a problem with your configuration.

Well I'm completely new to Ubuntu and Linux, so I don't even know where to start to see if my configuration is correct.

Well thanks anyways. I'll tinker around a bit and try googling it. If all else fails, it's back to Windows I guess.

---

### Post by ramjet_1953 on 2009-02-22
You could try the following as it often helps:

You will need to open a terminal and modify your /etc/X11/xorg.conf file.

This can only be done in sudo mode.

[COLOR="Blue"]Type this into a terminal:[/COLOR]

```
sudo nano /etc/X11/xorg.conf
```

[COLOR="Blue"]Add the following lines in the Device section:[/COLOR]

```
Option "VideoRam" "65536"
Option "CacheLines" "1980"
```

[COLOR="Blue"]Then save the file.[/COLOR]
These lines tell your system to allocate additional RAM to your video.

[COLOR="Red"]NOTE:[/COLOR] It is a good idea to back-up your /etc/X11/xorg.conf file before making any changes. That way if you "stuff-up", you can just recover the original file.

If you don't have the [COLOR="Blue"]nano[/COLOR] editor, you can use another editor, or install it by using the command:

```
sudo apt-get install nano
```

Regards,
Roger :D

---

### Post by binbash on 2009-02-22
My ubuntu was also crap at playing HD files.Install SVN version mplayer and x264, then install gnome-player.It will play fine

---

### Post by cerpin on 2009-02-22
> **Onoskelis said:**
> Yes I installed the restricted Nvidia drivers already.

Well, I don't know about that. I have an Nvidia graphics card and I can view HD content just fine. you just need to make sure you have the right packages installed.

---

### Post by ken22 on 2009-02-22
My video playback was awful, especially for flash until I installed the latest nvidia driver from the nvidia site.

Note that this isn't very straight forward to install and requires recompilation on new kernel releases, but my playback is awesome.

---

### Post by stefangr1 on 2009-02-22
MPEG-4 is an issue as all the decoding work is normally done at just one CPU core and the ffmpeg h264 decoder is not very efficient. When you look at your processor usage, you will probably see this. I find it strange, however, that you also have problems with 720p, on my E6750 CPU usage always remains below 60 or 70%.

The good news is that nvidia has been working on mpeg4 decoding on the GPU, which will enable you to play even 1080p perfectly at only a few percents of CPU usage. It is still in beta phase, but almost all movies that are obtained trough the regular channels play without issues.

You have to install the newest driver 180.29 and download the vdpau patch (be sure to get the newest) for mplayer. If you have a look in the readme / forums it shouldn't be too difficult to get things working.

---

