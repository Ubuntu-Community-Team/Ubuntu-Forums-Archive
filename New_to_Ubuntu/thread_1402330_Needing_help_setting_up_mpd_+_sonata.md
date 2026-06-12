---
title: "Needing help setting up mpd + sonata"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by Dobbie03 on 2010-02-09
Hi.

I want to use MPD and Sonata to listen to music, all my music is on an external hard drive and I am having issues working out what I should be putting in the mpd.conf under "music directory".

My music folder is obviously called music and i put the directory as "/media/music"

Is there anything else I should put in front of that or is there a walk through to set this up.

SOrry to sound so dumb but I just cant work it out.

---

### Post by mcduck on 2010-02-09
If you want to make things easy for yourself, you let MPD run as it's own user (that's the very definition of "daemon" in "Music Player Daemon";)).

..and for that to work, you'll also want to stick to using MPD's default directories. So, what I recommend is that instead of defining your own music directory in mpd.conf, you simply use a symbolic link to link your music directory into MPD's default directory. (you can also link it into a directory *inside* the MPD's music dir, this allows you to link audio files from many locations and many users...)

```
sudo ln -s /media/music /var/lib/mpd/music
```

MPD is really, really easy to setup, most of the settings in the configuration file work out-of-the-box. Usually you don't need to change anything there, apart from possibly editing the sound output settings and characterset to be used to fit your system.

---

### Post by nothingspecial on 2010-02-09
> **MattDobson said:**
> Hi.

I want to use MPD and Sonata to listen to music, all my music is on an external hard drive and I am having issues working out what I should be putting in the mpd.conf under "music directory".

My music folder is obviously called music and i put the directory as "/media/music"

Is there anything else I should put in front of that or is there a walk through to set this up.

SOrry to sound so dumb but I just cant work it out.

You need to create the playlist directory aswell and tell mpd.conf where it is.

---

### Post by Dobbie03 on 2010-02-09
> **mcduck said:**
> If you want to make things easy for yourself, you let MPD run as it's own user (that's the very definition of "daemon" in "Music Player Daemon";)).

..and for that to work, you'll also want to stick to using MPD's default directories. So, what I recommend is that instead of defining your own music directory in mpd.conf, you simply use a symbolic link to link your music directory into MPD's default directory. (you can also link it into a directory *inside* the MPD's music dir, this allows you to link audio files from many locations and many users...)

```
sudo ln -s /media/music /var/lib/mpd/music
```

MPD is really, really easy to setup, most of the settings in the configuration file work out-of-the-box. Usually you don't need to change anything there, apart from possibly editing the sound output settings and characterset to be used to fit your system.

I tried that but this is what came up:

```
ln: creating symbolic link `/var/lib/mpd/music/music': File exists
```

---

