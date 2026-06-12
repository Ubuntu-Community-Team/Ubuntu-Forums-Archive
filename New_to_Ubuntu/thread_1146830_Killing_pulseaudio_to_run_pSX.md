---
title: "Killing pulseaudio to run pSX"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by DeathOnJuice on 2009-05-03
Ever since the upgrade to Jaunty (and possibly Intrepid, since I never used this program on Intrepid), the pSX emulator called pSX has not been working. Startup brings this error:

```
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
Segmentation fault
```

If I kill pulseaudio as suggested by many, when I start the program again (or any program with sound I think), pulseaudio opens back up so it gets the same error. 

[COLOR="Red"]NOTE: THE FOLLOWING IS CONFUSING ME. pSX works under sudo even when pulseaudio is running sometimes, but sometimes it gives the same error as without sudo until I kill pulse:[/COLOR]

```
However, if I kill pulseaudio then run sudo pSX, it works. I think this is because trying to open pulseaudio with sudo gives an error about how it's not intended to be run by root, so pSX can't reopen it. Regardless, I don't want to run it as sudo, for security and because then I have to use root's home directory.
```

**Does anyone know how to keep pulseaudio from reopening when I run pSX, or make pSX work with pulseaudio?**

One thing that may be useful: I play another game called N through Wine, which was freezing up every few seconds. Turned out that every time it played a sound, it was freezing (an entry popped up in the program paman of ALSA plug-in [wine-preloader] then quickly disappeared). If I kill pulseaudio then open N before doing anything else, it restarts pulseaudio, but the game works. Not sure if I could get a similar effect for pSX. As it is, so I don't have to do that, I have wine using the OSS instead of ALSA plugin.

---

### Post by DeathOnJuice on 2009-05-03
Bump.

---

### Post by DeathOnJuice on 2009-05-03
And again.

---

### Post by DeathOnJuice on 2009-05-03
Bump.

---

### Post by damis648 on 2009-05-03
Try running it with the padsp wrapper:
```
padsp psx
```

---

### Post by DeathOnJuice on 2009-05-03
It returned the following:

```

Segmentation fault

```

---

### Post by DeathOnJuice on 2009-05-14
Bump.

---

### Post by Grishka on 2009-05-15
it looks like pSX is having trouble with soundcard detection. here's how I managed to workaround this on Jaunty amd64. I did have to run pSX with sudo, but only once. here's the deal:

1. kill pulseaudio (sudo killall pulseaudio)
2. run pSX as root (sudo ./pSX)
3. find the "sound" tab in the configuration and switch the "device" setting from "default" to your soundcard (plughw:0,0 in my case). apply. close pSX.
4 open /root/.pSX/psx.ini in a text editor (gksudo gedit /root/.pSX/psx.ini). find the "device" string under [Sound] section (I have "b7d317a4" there).
5. paste this string into the relevant section in ~/.pSX/psx.ini, in place of all zeroes. save. if you don't have this file in your user directory, run pSX and cancel just after choosing language, on the bios selection screen. pSX should save settings then.

now pSX runs fine even after reboot.

---

### Post by TheIdiotThatIsMe on 2009-05-15
> **Grishka said:**
> it looks like pSX is having trouble with soundcard detection. here's how I managed to workaround this on Jaunty amd64. I did have to run pSX with sudo, but only once. here's the deal:

1. kill pulseaudio (sudo killall pulseaudio)
2. run pSX as root (sudo ./pSX)
3. find the "sound" tab in the configuration and switch the "device" setting from "default" to your soundcard (plughw:0,0 in my case). apply. close pSX.
4 open /root/.pSX/psx.ini in a text editor (gksudo gedit /root/.pSX/psx.ini). find the "device" string under [Sound] section (I have "b7d317a4" there).
5. paste this string into the relevant section in ~/.pSX/psx.ini, in place of all zeroes. save. if you don't have this file in your user directory, run pSX and cancel just after choosing language, on the bios selection screen. pSX should save settings then.

now pSX runs fine even after reboot.

Got to step two and it still crashes on me. It mentions PulseAudio, even though I killed it, so it seems to be restarting it anyways.

```
E: core-util.c: Home directory /home/anthony not ours.
E: core-util.c: Home directory /home/anthony not ours.
ALSA lib pulse.c:272:(pulse_connect) PulseAudio: Unable to connect: Connection refused

[src/linux/sound.cpp, line 582]: 'snd_pcm_open(&pcm_handle,dev->info->device_fname,SND_PCM_STREAM_PLAYBACK,0)' returned 'Connection refused'
pSX: pcm_params.c:2259: snd_pcm_hw_refine: Assertion `pcm && params' failed.
Aborted

```

---

### Post by sultanoswing on 2009-05-16
Grishka, your solution worked for me, thanks!! :popcorn:

---

### Post by dragos240 on 2009-05-16
I suggest the following, open up a terminal and c+p this:

sudo apt-get remove pulseaudio

it fixed all my pulseaudio errors!

---

### Post by lkraemer on 2009-05-16
Here are two posts that may help. 

[http://ubuntuforums.org/showthread.php?t=1149634&page=2](http://ubuntuforums.org/showthread.php?t=1149634&page=2)
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

lkraemer

---

### Post by TheIdiotThatIsMe on 2009-05-16
I tried completely ripping out PulseAudio (completely out of my system, and rebooted to ALSA), AND running it as sudo, but I still get the same error :confused:

---

### Post by DeathOnJuice on 2009-05-17
> **lkraemer said:**
> Here are two posts that may help. 

[http://ubuntuforums.org/showthread.php?t=1149634&page=2](http://ubuntuforums.org/showthread.php?t=1149634&page=2)
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

lkraemer

The last step of the second link didn't work (I got the Connection refused error and the fix didn't work), but it still seemed to fix pSX. Thanks so much!

I also apparently should have done a clean install.

---

### Post by sp0tz on 2009-05-23
that fix got pSX running on a non root account, but it still crashes before it can load a game. All the games work fine with root privileges, but whenever I load a disk w/o root, I get the error "CD not usable: Failed to open file"

hm.... never mind, it won't work with root, either. I know this image has worked before. It works with pcsx (but the sound's all choppy)

uh... so... running
/path/to/pSX /path/to/game.bin
runs fine, (flawlessly so far for about about two hours of play) but running 
/path/to/pSX
or just doubleclicking the binary and 'inserting' the 'disk' from there results in that "cd not usable: failed to open file" error. command line:ftw? 
I guess now I just have to make a bunch of launchers?

---

### Post by rafe101 on 2010-03-23
I tried Grishka's fix and it works but I have no sound from pSX now. It's running and opening games at least—which I'm happy about—but it'd be nice to get the sound going.

Does anyone have any idea how to fix this?

---

### Post by Arkanus on 2010-03-31
> **rafe101 said:**
> I tried Grishka's fix and it works but I have no sound from pSX now. It's running and opening games at least—which I'm happy about—but it'd be nice to get the sound going.

Does anyone have any idea how to fix this?
You have to select the analog output in the pSX sound config (mine is plughw:0,0) and you will get sound, once you do the fix you will not need to run pSX as root, just as normal user

---

### Post by rafe101 on 2010-03-31
I did that. It did allow me to run it without having to call it with sudo, but I had no sound. Uninstalling Pulseaudio seems to work fine though.

---

### Post by h0rnman on 2010-06-20
The solution with Lucid (10.04) seems to be a bit different.  Instead of killing the process, I did:

```

sudo kill -STOP <<pid for the pulseaudio application>>

```
to stop the pulseaudio process, then I ran:
```

sudo ./pSX

```

Once that loaded, I went into the configuration and changed the Audio device from 'Default' to the actual audio device being used.  I then existed out of pSX, copied the Device=XXXXXXXX from the /root/.pSX/psx.ini file to the /home/xxxx/.pSX/psx.ini file.  Once that had been done, the pSX executable ran fine, even with pulseaudio restarted.
The only oddity I noticed was a bunch of sound:underrun messages being thrown to the terminal, but everything appears to work correctly.

Hope this helps!

---

### Post by kiiski on 2011-08-04
Thank you guys. This thread helped me a lot!

---

### Post by mikhail21393 on 2012-04-16
> **h0rnman said:**
> The solution with Lucid (10.04) seems to be a bit different.  Instead of killing the process, I did:

```

sudo kill -STOP <<pid for the pulseaudio application>>

```to stop the pulseaudio process, then I ran:
```

sudo ./pSX

```Once that loaded, I went into the configuration and changed the Audio device from 'Default' to the actual audio device being used.  I then existed out of pSX, copied the Device=XXXXXXXX from the /root/.pSX/psx.ini file to the /home/xxxx/.pSX/psx.ini file.  Once that had been done, the pSX executable ran fine, even with pulseaudio restarted.
The only oddity I noticed was a bunch of sound:underrun messages being thrown to the terminal, but everything appears to work correctly.

Hope this helps!
Hey Mister I see that you solved my problem with this one! And I use the latest Ubuntu 11.10 (Latest) with Gnome Classic Theme!

The only thing I have to do all the time is to switch from the Output device from CA0106 (Soundblaster Analog Stereo) to USB Headset Analog Stereo to work, because I think pSX won't work when I switch directly to the Soundblaster and it really works when the I switch the Output to other device .

I hope this tip might help!

Thanks a lot for your advice it was real helpful! ;)

---

### Post by coffeecat on 2012-04-16
This is an old thread, started almost three years ago. If anyone needs help with any of the issues mentioned in this thread, please start a new thread.

Closed.

---

