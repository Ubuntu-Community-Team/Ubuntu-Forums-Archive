---
title: "psx segfaults after update to jaunty"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by sentofuno on 2009-04-25
this is what i get from the terminal

 * PulseAudio configured for per-user sessions
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
Segmentation fault

does anyone know how to fix it? 

thanks

---

### Post by TygerFish on 2009-04-25
I wish... this must be a new thing; I was running pSX without issue earlier today before I switched over to Jaunty.

---

### Post by TygerFish on 2009-04-26
BTW, my console output, after much meddling and trying things that should have fixed the 32/64 problem:

```
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so

(pSX:30408): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:30408): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:30408): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:30408): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:30408): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:30408): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:30408): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:30408): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
pad=0
Segmentation fault

```

---

### Post by benmoran on 2009-04-26
The problem is that pSX hasn't been updated to work with Pulse Audio, and there is a problem with it's audio sink method. If you kill Pulse Audio it will load fine. But the better option is using pSX Frontend:

[http://psxemulator.proboards.com/index.cgi?board=news&action=display&thread=1080](http://psxemulator.proboards.com/index.cgi?board=news&action=display&thread=1080)

It automatically kills and restarts Pulse Audio for you, as well as let's you specify a bunch of optional settings. 

-Ben

---

### Post by sentofuno on 2009-04-26
i tried the frontend, thanks for the link.

i'm not sure if its not fixed the problem or i'm doing something wrong, but if i try run psx through the frontend i get asked which language i want. when i select english and ok it it just crashes out again. i don't know how to replicate what the frontend does with the terminal to give you an output for that tho.


sorry should have mentioned, i am running amd64 9.04

---

### Post by TygerFish on 2009-04-26
Thanks for the tip Ben, but killing pulseaudio doesn't change anything for me.

sentofuno, if you want to try running the frontend from the command line, go to the folder where you extracted it and run it like so...
```
cd ~/Desktop/psxfrontendv111linx64
./pSXFrontend
```
If you're also using a fresh copy of Jaunty, you'll probably get the same error that I got:
```
error while loading shared libraries: libpython2.5.so.1.0: cannot open shared object file: No such file or directory
```
I can't find the 2.5 library anywhere.  But I don't think the frontend matters for the purposes of just getting pSX working...

Since these are ELFCLASS/segfault problems, my guess is that pSX is a 32-bit binary and it can't find its 32-bit libraries.  In the past, I've solved those sorts of problems with getlibs or by downloading the 32-bit .deb package and manually putting the 32-bit libraries in /usr/lib32.  In this case, none of that has worked.

---

### Post by TygerFish on 2009-04-26
So, yes, pSX is a 32-bit binary:
```
$ file pSX
pSX: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.9, stripped

```

But all of its libraries appear to be accounted for?
```
$ ldd pSX 
	linux-gate.so.1 =>  (0xf7f15000)
	libGL.so.1 => /usr/lib32/libGL.so.1 (0xf7e3f000)
	libz.so.1 => /usr/lib32/libz.so.1 (0xf7e29000)
	libasound.so.2 => /usr/lib32/libasound.so.2 (0xf7d60000)
	libgtkglext-x11-1.0.so.0 => /usr/lib32/libgtkglext-x11-1.0.so.0 (0xf7d5c000)
	libgdkglext-x11-1.0.so.0 => /usr/lib32/libgdkglext-x11-1.0.so.0 (0xf7d11000)
	libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf7c9f000)
	libXmu.so.6 => /usr/lib32/libXmu.so.6 (0xf7c89000)
	libXt.so.6 => /usr/lib32/libXt.so.6 (0xf7c35000)
	libSM.so.6 => /usr/lib32/libSM.so.6 (0xf7c2c000)
	libICE.so.6 => /usr/lib32/libICE.so.6 (0xf7c14000)
	libpangox-1.0.so.0 => /usr/lib32/libpangox-1.0.so.0 (0xf7c07000)
	libgthread-2.0.so.0 => /usr/lib32/libgthread-2.0.so.0 (0xf7c01000)
	librt.so.1 => /lib32/librt.so.1 (0xf7bf8000)
	libglade-2.0.so.0 => /usr/lib32/libglade-2.0.so.0 (0xf7bdf000)
	libgtk-x11-2.0.so.0 => /usr/lib32/libgtk-x11-2.0.so.0 (0xf782e000)
	libxml2.so.2 => /usr/lib32/libxml2.so.2 (0xf76f2000)
	libgdk-x11-2.0.so.0 => /usr/lib32/libgdk-x11-2.0.so.0 (0xf7665000)
	libatk-1.0.so.0 => /usr/lib32/libatk-1.0.so.0 (0xf764a000)
	libgdk_pixbuf-2.0.so.0 => /usr/lib32/libgdk_pixbuf-2.0.so.0 (0xf7630000)
	libpangocairo-1.0.so.0 => /usr/lib32/libpangocairo-1.0.so.0 (0xf7623000)
	libpango-1.0.so.0 => /usr/lib32/libpango-1.0.so.0 (0xf75e0000)
	libcairo.so.2 => /usr/lib32/libcairo.so.2 (0xf7566000)
	libgobject-2.0.so.0 => /usr/lib32/libgobject-2.0.so.0 (0xf7528000)
	libgmodule-2.0.so.0 => /usr/lib32/libgmodule-2.0.so.0 (0xf7523000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf751e000)
	libglib-2.0.so.0 => /usr/lib32/libglib-2.0.so.0 (0xf7466000)
	libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf7377000)
	libm.so.6 => /lib32/libm.so.6 (0xf7351000)
	libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7342000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf7329000)
	libc.so.6 => /lib32/libc.so.6 (0xf71c5000)
	libGLcore.so.1 => /usr/lib32/libGLcore.so.1 (0xf62ad000)
	libnvidia-tls.so.1 => /usr/lib32/tls/libnvidia-tls.so.1 (0xf62ab000)
	libXext.so.6 => /usr/lib32/libXext.so.6 (0xf629b000)
	libX11.so.6 => /usr/lib32/libX11.so.6 (0xf61ac000)
	libpangoft2-1.0.so.0 => /usr/lib32/libpangoft2-1.0.so.0 (0xf6182000)
	libgio-2.0.so.0 => /usr/lib32/libgio-2.0.so.0 (0xf6114000)
	libfreetype.so.6 => /usr/lib32/libfreetype.so.6 (0xf609d000)
	libfontconfig.so.1 => /usr/lib32/libfontconfig.so.1 (0xf6070000)
	libuuid.so.1 => /lib32/libuuid.so.1 (0xf606b000)
	libpcre.so.3 => /lib32/libpcre.so.3 (0xf6038000)
	/lib/ld-linux.so.2 (0xf7f16000)
	libXrender.so.1 => /usr/lib32/libXrender.so.1 (0xf602e000)
	libXinerama.so.1 => /usr/lib32/libXinerama.so.1 (0xf602b000)
	libXi.so.6 => /usr/lib32/libXi.so.6 (0xf6021000)
	libXrandr.so.2 => /usr/lib32/libXrandr.so.2 (0xf6019000)
	libXcursor.so.1 => /usr/lib32/libXcursor.so.1 (0xf600f000)
	libXcomposite.so.1 => /usr/lib32/libXcomposite.so.1 (0xf600b000)
	libXdamage.so.1 => /usr/lib32/libXdamage.so.1 (0xf6008000)
	libXfixes.so.3 => /usr/lib32/libXfixes.so.3 (0xf6003000)
	libpixman-1.so.0 => /usr/lib32/libpixman-1.so.0 (0xf5fbf000)
	libdirectfb-1.0.so.0 => /usr/lib32/libdirectfb-1.0.so.0 (0xf5f59000)
	libfusion-1.0.so.0 => /usr/lib32/libfusion-1.0.so.0 (0xf5f50000)
	libdirect-1.0.so.0 => /usr/lib32/libdirect-1.0.so.0 (0xf5f3b000)
	libpng12.so.0 => /usr/lib32/libpng12.so.0 (0xf5f15000)
	libxcb-render-util.so.0 => /usr/lib32/libxcb-render-util.so.0 (0xf5f0f000)
	libxcb-render.so.0 => /usr/lib32/libxcb-render.so.0 (0xf5f07000)
	libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf5eed000)
	libXau.so.6 => /usr/lib32/libXau.so.6 (0xf5ee9000)
	libselinux.so.1 => /lib32/libselinux.so.1 (0xf5ecf000)
	libexpat.so.1 => /usr/lib32/libexpat.so.1 (0xf5ea7000)
	libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf5ea2000)

$ sudo getlibs pSX
This application isn't missing any dependencies
```

I'm stumped.

---

### Post by DeathOnJuice on 2009-04-26
I'm getting the same segfault. Killing pulseaudio does nothing (it shows back up in the processes list as soon s I start pSX).

---

### Post by llamabr on 2009-04-26
Off the top of my head, sometimes you have some inconsistencies between versions that you can eliminate by rm'ing and then recreating your config files.  There's probably something like .psx/ in your ~/ that you can rm, and running it again will just recreate those properly.

Just a thought.

---

### Post by DeathOnJuice on 2009-04-26
> **DeathOnJuice said:**
> I'm getting the same segfault. Killing pulseaudio does nothing (it shows back up in the processes list as soon as I start pSX).

I almost forgot: running it under sudo fixes the problem, but I would really rather not do that. Plus I would have to move all my config.

---

### Post by TygerFish on 2009-04-26
> **DeathOnJuice said:**
> I almost forgot: running it under sudo fixes the problem, but I would really rather not do that. Plus I would have to move all my config.


That's incredible!  It works with sudo!

My console output has all of the same errors, except the two which seem to be important:
```
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64

```
and
```
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
pad=0
Segmentation fault

```

It seems like the libcanberra-gtk-module is the one causing the problem.  My system has 32- and 64-bit versions installed:
```
$ locate libcanberra-gtk-module.so
/usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
/usr/lib32/gtk-2.0/modules/libcanberra-gtk-module.so

```
...but as you can see in the output above, when I run pSX as a regular user, it fetches the one at /usr/lib and then complains about the ELFCLASS error.

So how do we get a regular user to specify that library?  And why is root exempt from this problem?

---

### Post by DeathOnJuice on 2009-04-26
I'm not getting any error about libcanberra. Just:

```

[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
Segmentation fault

```

And, when I run with sudo, just:

```

E: core-util.c: Home directory /home/name not ours.
sound: underrun
sound: underrun
sound: underrun
sound: underrun

```

By the way, how did you install it? I'm on a 32-bit system and just got the binary straight from the pSX website. I know there are some .debs floating around out there, but I doubt they would help.

I don't understand why running pSX starts pulseaudio back up after I've killed it, or why sudo can run pSX even with pulseaudio.

---

### Post by DeathOnJuice on 2009-04-27
Bump.

---

### Post by Dougie187 on 2009-04-27
To install it you can use getlibs. I don't have a link, but Im sure if you google for "ubuntu getlibs" you will probably get a howto in the forums.

I still get a seg fault too, but I don't really need psx anyways. I just thought it would be cool to get it to work.

---

### Post by TygerFish on 2009-04-30
I've done a whole lot of research on pSX and PulseAudio in the last few days.  In the meantime, I've been using a script that does "killall pulseaudio" and then launches pSX and then "/etc/init.d/pulseaudio start" all as root.  That's been letting me use pSX with sound relatively painlessly.

That solution means I can't play music while using pSX, but as far as I can tell, due to the way pSX wants to grab ALSA directly, there's no way to get it to share.  (And I thought part of the point of PulseAudio was to make all these applications play nicely with each other...?)

For instances where I want to listen to music while playing a game (with no in-game sound), I just run pSX as root without killing the PulseAudio server first.
(If that doesn't work for you, try killing pulseaudio, restarting it, and then running pSX as root.  For some reason, that seems to let you run it without audio occasionally.)

Does anyone know why running as root solves this problem?  If I knew, I could probably figure out how to fix it.


> **DeathOnJuice said:**
> I'm not getting any error about libcanberra. Just:

```

[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
Segmentation fault

```

And, when I run with sudo, just:

```

E: core-util.c: Home directory /home/name not ours.
sound: underrun
sound: underrun
sound: underrun
sound: underrun

```

By the way, how did you install it? I'm on a 32-bit system and just got the binary straight from the pSX website. I know there are some .debs floating around out there, but I doubt they would help.

I don't understand why running pSX starts pulseaudio back up after I've killed it, or why sudo can run pSX even with pulseaudio.

I also downloaded it from the pSX website.

Also, I also get the following when I run as root:
```

E: core-util.c: Home directory /home/name not ours.

```
And sometimes this too:
```

sound: underrun
sound: underrun
sound: underrun
sound: underrun

```
...but it otherwise runs without a hitch.

It's not surprising that you're not getting any ELFCLASS errors; since you're running a 32-bit OS with 32-bit libraries, the 32-bit binary only has those to reference.  :)  For some reason, it's getting confused on a 64-bit system and is unable to find the 32-bit versions of the libraries, even though I know they're installed.

---

### Post by TygerFish on 2009-04-30
> **Dougie187 said:**
> To install it you can use getlibs. I don't have a link, but Im sure if you google for "ubuntu getlibs" you will probably get a howto in the forums.

I still get a seg fault too, but I don't really need psx anyways. I just thought it would be cool to get it to work.

I've already used getlibs to install the requisite 32-bit drivers (see above, in same code box as the ldd command) and pSX still isn't using them.  :(

---

### Post by DeathOnJuice on 2009-05-01
Bump.

---

### Post by TygerFish on 2009-05-01
> **DeathOnJuice said:**
> Bump.

At this point, it might help to specify or restate the question.  For example:

Why is it that running pSX as a regular user uses the 64-bit libraries even when the 32-bit libraries are installed (causing a segfault), while running pSX as root seems to use the 32-bit libraries and works fine?

(I would also like to know the answer to that question.  :))

---

### Post by DeathOnJuice on 2009-05-01
Well, I'm on 32-bit and have the same problem, so you know it's not a library problem.

---

### Post by DeathOnJuice on 2009-05-03
[http://ubuntuforums.org/showthread.php?p=7202241](http://ubuntuforums.org/showthread.php?p=7202241)

New topic with a bit of new insight (specifically on why sudo works).

---

