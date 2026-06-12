---
title: "amarok won't play mp3s"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by Falc7 on 2009-12-03
Amarok won't play mp3s, it just skips right past them, i've already installed kubuntu restricted extras, so i am not sure what the problem is.

And i've already tried
```
sudo apt-get install libxine1-ffmpeg gstreamer0.10-plugins-ugly

```

---

### Post by arochester on 2009-12-03
gstreamer is more a Gnome thing. g(for gnome) - streamer

Have a look at "Comprehensive Multimedia & Video Howto" on [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) and concentrate on the Kubuntu bits.

---

### Post by Falc7 on 2009-12-03
I've done most of the kubuntu parts in that thread, specifically
```
sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree libk3b2-extracodecs libmp3lame0 libtunepimp5-mp3 libxine1-ffmpeg non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar

```

And enabling the medibuntu repository

---

### Post by Islington on 2009-12-03
Try this:

```
 sudo apt-get install kubuntu-restricted-extras

```

---

### Post by Falc7 on 2009-12-03
```
jamie@jamie-kubuntu:~$ sudo apt-get install kubuntu-restricted-extras
Reading package lists... Done
Building dependency tree
Reading state information... Done
kubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

---

### Post by SunnyRabbiera on 2009-12-03
Kubuntu restricted extras might help, but personally I would install songbird as amarok 2 sucks

---

### Post by Islington on 2009-12-03
> **SunnyRabbiera said:**
> Kubuntu restricted extras might help, but personally I would install songbird as amarok 2 sucks

unhelpful.

---

### Post by Islington on 2009-12-03
> **Falc7 said:**
> ```
jamie@jamie-kubuntu:~$ sudo apt-get install kubuntu-restricted-extras
Reading package lists... Done
Building dependency tree
Reading state information... Done
kubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

Are you able to get sound from other players? dragon for example?

---

### Post by desperado665 on 2009-12-03
could it be a file permissions thing? I have had the same issue with amarok over permissions as well.

```
kdsu chown -R username:groupname /path/to/files 
```

---

### Post by Falc7 on 2009-12-03
> **Islington said:**
> Are you able to get sound from other players? dragon for example?

VLC and SMPlayer play the mp3s fine, Dragon dosen't however, it just sort of freezes/crashes

> **desperado665 said:**
> could it be a file permissions thing? I have had the same issue with amarok over permissions as well.

```
kdsu chown -R username:username /path/to/files 
```

I get this
```
jamie@jamie-kubuntu:~$ kdsu chown -R jamie:jamie /home/jamie/Music/[2000] Greatest Hits - Lenny Kravitz
No command 'kdsu' found, did you mean:
 Command 'ksu' from package 'heimdal-clients' (universe)
 Command 'ksu' from package 'krb5-user' (main)
kdsu: command not found

```

But i don't think it is due to ownerships, when i right click the files it says 'jamie' is the owner of the mp3s

---

### Post by desperado665 on 2009-12-03
my bad... its kdesu... plus I'm not sure thats the issue anyway if other player play them fine

---

### Post by Islington on 2009-12-03
> **Falc7 said:**
> VLC and SMPlayer play the mp3s fine, Dragon doesn't however, it just sort of freezes/crashes


hmm. I think we need more facts here..

Run Dragon in a terminal and play the mp3. Run Amarok in terminal and play the mp3.

---

### Post by desperado665 on 2009-12-03
> **islington said:**
> hmm. I think we need more facts here..

Run dragon in a terminal and play the mp3. Run amarok in terminal and play the mp3.

+1

---

### Post by Falc7 on 2009-12-03
```
jamie@jamie-kubuntu:~$ dragon
xine is asking to seek behind the end of the data stream
xine is asking to seek behind the end of the data stream
```

Most of the inf below happens when i start amarok, not when i play the file, the very bottom bit sometimes happens when i try and play the mp3
```
jamie@jamie-kubuntu:~$ amarok
TagLib: ASF: Not an ASF file.
TagLib: ASF: Not an ASF file.
kmimetype filetype guessing failed for /home/jamie/Music/everlong acoustic.flv 
TagLib: ASF: Not an ASF file.                                                  
kmimetype filetype guessing failed for /home/jamie/Music/Aya_Ueto_-_Silence.flv 
kmimetype filetype guessing failed for /home/jamie/Music/Daft_Punk_-_Digital_Love.flv
kmimetype filetype guessing failed for /home/jamie/Music/amaral - kamikaze.flv
TagLib: ASF: Not an ASF file.
TagLib: ASF: Not an ASF file.
kmimetype filetype guessing failed for /home/jamie/Music/foo fighters The pretender
TagLib: ASF: Not an ASF file.
TagLib: ASF: Not an ASF file.
TagLib: ASF: Not an ASF file.
kmimetype filetype guessing failed for /home/jamie/Music/Alizee_-_Jen_ai_marre.flv
TagLib: ASF: Not an ASF file.
TagLib: ASF: Not an ASF file.
TagLib: ASF: Not an ASF file.
TagLib: ASF: Not an ASF file.
amarok:  **********************************************************************************************
amarok:  ** AMAROK WAS STARTED IN NORMAL MODE. IF YOU WANT TO SEE DEBUGGING INFORMATION, PLEASE USE: **
amarok:  ** amarok --debug                                                                           **
amarok:  **********************************************************************************************
jamie@jamie-kubuntu:~$ QDir::exists: Empty or null file name
QPainter::begin: Cannot paint on a null pixmap
QPainter::setRenderHint: Painter must be active to set rendering hints
QPainter::translate: Painter not active
QPainter::save: Painter not active
QPainter::translate: Painter not active
QPainter::rotate: Painter not active
QPainter::restore: Unbalanced save/restore
QPainter::rotate: Painter not active

```

---

### Post by desperado665 on 2009-12-03
try 

```
sudo apt-get install libmad0
```

---

### Post by Islington on 2009-12-03
The dragon error is pointing to a phonon-xine error is phonon-backend-xine installed? Is it testing well?

System Settings>>Sound and Video Configuration>>Audio Output>> Music

do you have pulseaudio?

---

### Post by Falc7 on 2009-12-03
> **Islington said:**
> The dragon error is pointing to a phonon-xine error is phonon-backend-xine installed? Is it testing well?

System Settings>>Sound and Video Configuration>>Audio Output>> Music

do you have pulseaudio?

Phonon-backend-xine is installed, but the phonon-backend-xine-ffmpeg and ......-gstreamer plugins arent.

I do have pulseaudio and its top of the list, but when i press test nothing happens, infact, nothing happens for any of the options listed


> **desperado665 said:**
> try 

```
sudo apt-get install libmad0
```

jamie@jamie-kubuntu:~$ sudo apt-get install libmad0
[sudo] password for jamie:
Reading package lists... Done
Building dependency tree
Reading state information... Done
libmad0 is already the newest version.
libmad0 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

---

### Post by desperado665 on 2009-12-03
Ok, a dumb question, but you are not trying to play .flv files with amarok, right? .flv is flash video and should open with vlc or kaffeine. I assume you have some flash videos mixed in with your mp3 that you do want to play.

You might try moving your vids to a different location and try playing mp3s again.

---

### Post by mc4man on 2009-12-03
Try locating a file named catalog.cache and deleting it, then restarting amarok or any xine based player
Don't use kubuntu but in ubuntu it's located in ~/.xine/catalog.cache

---

### Post by Islington on 2009-12-03
> **Falc7 said:**
> Phonon-backend-xine is installed, but the phonon-backend-xine-ffmpeg and ......-gstreamer plugins arent.

I do have pulseaudio and its top of the list, but when i press test nothing happens, infact, nothing happens for any of the options listed



agh. hmm, the problem is that pulse is somehow letting vlc do its thing. 

A crude try before considering removing pulse:

Close all media programs.
Delete:
/home/user/.kde/share/apps/amarok 
/home/user/.xine 
Restart Amarok.

---

### Post by Falc7 on 2009-12-03
> **desperado665 said:**
> Ok, a dumb question, but you are not trying to play .flv files with amarok, right? .flv is flash video and should open with vlc or kaffeine. I assume you have some flash videos mixed in with your mp3 that you do want to play.

You might try moving your vids to a different location and try playing mp3s again.


Amarok in my experience plays most flv well, i do have some flash videos in with the mp3s, i tried creating a new folder and moving an mp3 to it, and playing that mp3 with amarok, but it didn't play

---

### Post by Falc7 on 2009-12-03
Its working, thanks very much guys! Deleting those files did it :D

---

### Post by Islington on 2009-12-03
> **Falc7 said:**
> Its working, thanks very much guys! Deleting those files did it :D

:D Enjoy.

---

### Post by minisori on 2009-12-22
Hmm i have a similar problem but with dragon and trying to play any kind of video file, neither the previsualization of videos or mp3 works in dolphin. In the other hand amarok seem to be working fine.

The error is the same: xine is asking to seek behind the end of the data stream.

EDIT:
Nvm, just found it is a bug caused by the name of the path, if it contains a # it fails to correctly play any file O_o, dumb bug.

---

### Post by Dikko on 2010-01-14
Thanks so much [Islington]("http://ubuntuforums.org/member.php?u=111629").

I am new to Ubuntu and this was a nightmare till I found your solution..

You rock,

Thanks,

Dikko.

---

