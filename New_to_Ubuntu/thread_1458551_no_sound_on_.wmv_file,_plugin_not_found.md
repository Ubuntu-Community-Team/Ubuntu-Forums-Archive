---
title: "no sound on .wmv file, plugin not found"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by rocka on 2010-04-20
Hi,
 I downloaded a recording of a webinar and I can see the video but not hear the sound. I have tried mplayer and VLC.

Mplayer asks to go look for a suitable plugin and then says:
```

No packages with the requested plugins found

The requested plugins are:

Windows Media Speech decoder
```

I did some googling and found that the problem is likely to do with the proprietary format the webinar was originally recorded in - "G2M3" and the person who is supplying the recording says she has run it through Media Encoder to drop the screen resolution and set the sound to mono in an effort to reduce the file size.


Can anyone please suggest a way to get my system [Ubuntu 9.10 (karmic)] or some way to convert the file to something VLC or mplayer will play?


cheers......

---

### Post by alphacrucis2 on 2010-04-20
> **rocka said:**
> Hi,
 I downloaded a recording of a webinar and I can see the video but not hear the sound. I have tried mplayer and VLC.

Mplayer asks to go look for a suitable plugin and then says:
```

No packages with the requested plugins found

The requested plugins are:

Windows Media Speech decoder
```

I did some googling and found that the problem is likely to do with the proprietary format the webinar was originally recorded in - "G2M3" and the person who is supplying the recording says she has run it through Media Encoder to drop the screen resolution and set the sound to mono in an effort to reduce the file size.


Can anyone please suggest a way to get my system [Ubuntu 9.10 (karmic)] or some way to convert the file to something VLC or mplayer will play?


cheers......

Have you tried installing the w32codecs package from medibuntu?

---

### Post by rocka on 2010-04-20
Hi,
no I hadn't...

I went to [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) and followed the instructions there:

pasted this into a terminal:
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

and this is what I got:
```
merlin@merlin-desktop:~$ sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
[sudo] password for merlin: 
--2010-04-20 20:48:55--  http://www.medibuntu.org/sources.list.d/karmic.list
Resolving www.medibuntu.org... 87.98.242.110
Connecting to www.medibuntu.org|87.98.242.110|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 272 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 272         --.-K/s   in 0s      

2010-04-20 20:48:56 (27.7 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [272/272]

Get:1 http://dl.google.com stable Release.gpg [189B]
Hit http://linux.dropbox.com karmic Release.gpg
Hit http://au.archive.ubuntu.com karmic Release.gpg
Ign http://au.archive.ubuntu.com karmic/main Translation-en_AU
Ign http://au.archive.ubuntu.com karmic/restricted Translation-en_AU
Hit http://archive.canonical.com intrepid Release.gpg
Ign http://archive.canonical.com intrepid/partner Translation-en_AU
Ign http://au.archive.ubuntu.com karmic/universe Translation-en_AU
Ign http://linux.dropbox.com karmic/main Translation-en_AU
Ign http://au.archive.ubuntu.com karmic/multiverse Translation-en_AU
Get:2 http://au.archive.ubuntu.com karmic-updates Release.gpg [189B]
Hit http://linux.dropbox.com karmic Release
Hit http://archive.canonical.com intrepid Release
Ign http://au.archive.ubuntu.com karmic-updates/main Translation-en_AU
Ign http://au.archive.ubuntu.com karmic-updates/restricted Translation-en_AU
Ign http://au.archive.ubuntu.com karmic-updates/universe Translation-en_AU
Hit http://linux.dropbox.com karmic/main Packages
Ign http://au.archive.ubuntu.com karmic-updates/multiverse Translation-en_AU
Ign http://dl.google.com stable/main Translation-en_AU
Hit http://archive.canonical.com intrepid/partner Packages
Hit http://au.archive.ubuntu.com intrepid-backports Release.gpg
Ign http://linux.dropbox.com karmic/main Sources
Get:3 http://dl.google.com stable Release [2,540B]
Ign http://au.archive.ubuntu.com intrepid-backports/main Translation-en_AU
Ign http://au.archive.ubuntu.com intrepid-backports/restricted Translation-en_AU
Ign http://linux.dropbox.com karmic/main Sources
Hit http://archive.canonical.com intrepid/partner Sources
Ign http://au.archive.ubuntu.com intrepid-backports/universe Translation-en_AU
Hit http://linux.dropbox.com karmic/main Sources
Ign http://au.archive.ubuntu.com intrepid-backports/multiverse Translation-en_AU
Get:4 http://dl.google.com stable/main Packages [925B]
Get:5 http://au.archive.ubuntu.com karmic-security Release.gpg [189B]
Ign http://au.archive.ubuntu.com karmic-security/main Translation-en_AU
Ign http://au.archive.ubuntu.com karmic-security/restricted Translation-en_AU
Ign http://au.archive.ubuntu.com karmic-security/universe Translation-en_AU
Ign http://au.archive.ubuntu.com karmic-security/multiverse Translation-en_AU
Hit http://au.archive.ubuntu.com karmic Release
Get:6 http://au.archive.ubuntu.com karmic-updates Release [44.1kB]
Hit http://au.archive.ubuntu.com intrepid-backports Release
Get:7 http://au.archive.ubuntu.com karmic-security Release [44.1kB]
Hit http://au.archive.ubuntu.com karmic/main Packages
Hit http://au.archive.ubuntu.com karmic/restricted Packages
Hit http://au.archive.ubuntu.com karmic/main Sources
Hit http://au.archive.ubuntu.com karmic/restricted Sources
Hit http://au.archive.ubuntu.com karmic/universe Packages
Hit http://au.archive.ubuntu.com karmic/universe Sources
Hit http://au.archive.ubuntu.com karmic/multiverse Packages
Hit http://au.archive.ubuntu.com karmic/multiverse Sources
Get:8 http://au.archive.ubuntu.com karmic-updates/main Packages [201kB]
Get:9 http://au.archive.ubuntu.com karmic-updates/restricted Packages [14B]
Get:10 http://au.archive.ubuntu.com karmic-updates/main Sources [60.0kB]
Get:11 http://au.archive.ubuntu.com karmic-updates/restricted Sources [14B]
Get:12 http://au.archive.ubuntu.com karmic-updates/universe Packages [125kB]
Get:13 http://au.archive.ubuntu.com karmic-updates/universe Sources [29.8kB]
Get:14 http://au.archive.ubuntu.com karmic-updates/multiverse Packages [7,354B]
Get:15 http://au.archive.ubuntu.com karmic-updates/multiverse Sources [4,036B]
Hit http://au.archive.ubuntu.com intrepid-backports/main Packages
Hit http://au.archive.ubuntu.com intrepid-backports/restricted Packages
Hit http://au.archive.ubuntu.com intrepid-backports/universe Packages
Hit http://au.archive.ubuntu.com intrepid-backports/multiverse Packages
Hit http://au.archive.ubuntu.com intrepid-backports/main Sources
Hit http://au.archive.ubuntu.com intrepid-backports/restricted Sources
Hit http://au.archive.ubuntu.com intrepid-backports/universe Sources
Hit http://au.archive.ubuntu.com intrepid-backports/multiverse Sources
Get:16 http://au.archive.ubuntu.com karmic-security/main Packages [95.0kB]
Get:17 http://au.archive.ubuntu.com karmic-security/restricted Packages [14B]
Get:18 http://au.archive.ubuntu.com karmic-security/main Sources [28.1kB]
Get:19 http://au.archive.ubuntu.com karmic-security/restricted Sources [14B]
Get:20 http://au.archive.ubuntu.com karmic-security/universe Packages [50.7kB]
Get:21 http://au.archive.ubuntu.com karmic-security/universe Sources [8,743B]
Get:22 http://au.archive.ubuntu.com karmic-security/multiverse Packages [1,666B]
Get:23 http://au.archive.ubuntu.com karmic-security/multiverse Sources [577B]
Err http://packages.medibuntu.org karmic Release.gpg
  Could not connect to packages.medibuntu.org:80 (88.191.82.11), connection timed out
Err http://packages.medibuntu.org karmic/free Translation-en_AU
  Unable to connect to packages.medibuntu.org http:
Err http://packages.medibuntu.org karmic/non-free Translation-en_AU
  Unable to connect to packages.medibuntu.org http:
Fetched 704kB in 2min 0s (5,848B/s)
Reading package lists...
W: Failed to fetch http://packages.medibuntu.org/dists/karmic/Release.gpg  Could not connect to packages.medibuntu.org:80 (88.191.82.11), connection timed out

W: Failed to fetch http://packages.medibuntu.org/dists/karmic/free/i18n/Translation-en_AU.bz2  Unable to connect to packages.medibuntu.org http:

W: Failed to fetch http://packages.medibuntu.org/dists/karmic/non-free/i18n/Translation-en_AU.bz2  Unable to connect to packages.medibuntu.org http:

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: Duplicate sources.list entry http://linux.dropbox.com karmic/main Packages (/var/lib/apt/lists/linux.dropbox.com_ubuntu_dists_karmic_main_binary-i386_Packages)
Reading package lists...
Building dependency tree...
Reading state information...
E: Couldn't find package medibuntu-keyring
merlin@merlin-desktop:~$
``` 


since I'm a sucker for punishment I tried the next step from that page:
```
sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu
```

and I got:
```
merlin@merlin-desktop:~$ sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package app-install-data-medibuntu
merlin@merlin-desktop:~$ 
```

trying to play the file again, still the same: pic ok, no sound.

---

### Post by alphacrucis2 on 2010-04-20
> **rocka said:**
> Hi,
no I hadn't...

I went to [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) and followed the instructions there:

Looks like it didn't actually install. Note that it timed out trying to connect to the server packages.medibuntu.org. Maybe that server is down at the moment as I can't get a response from packages.medibuntu.org via my browser either:

```
Reading package lists...
W: Failed to fetch http://packages.medibuntu.org/dists/karmic/Release.gpg  Could not connect to packages.medibuntu.org:80 (88.191.82.11), connection timed out
W: Failed to fetch http://packages.medibuntu.org/dists/karmic/free/i18n/Translation-en_AU.bz2  Unable to connect to packages.medibuntu.org http:
W: Failed to fetch http://packages.medibuntu.org/dists/karmic/non-free/i18n/Translation-en_AU.bz2  Unable to connect to packages.medibuntu.org http:
W: Some index files failed to download, they have been ignored, or old ones used instead.
```

I suggest waiting for a while and try again.

---

### Post by rocka on 2010-04-20
ok, thanks for your thoughts.
I'll give it a while, go and eat something and try again.


cheers, :)

---

### Post by alphacrucis2 on 2010-04-20
> **rocka said:**
> ok, thanks for your thoughts.
I'll give it a while, go and eat something and try again.


cheers, :)

Looks like the Medibuntu packages server has just come back up.

---

### Post by rocka on 2010-04-21
Hi,
I'm just home from work now and tried it again, but again it timed out.
I note that it's looking at the AU servers; perhaps the US ones would be more reliable?

How do I tell it to use the US ones instead?

---

### Post by taqkavar on 2010-04-21
Medibuntu servers seem to be down.
You can find workarounds and mirrors in this bug report:

[https://bugs.launchpad.net/medibuntu/+bug/565810](https://bugs.launchpad.net/medibuntu/+bug/565810)

---

### Post by rocka on 2010-04-21
Hi,

I followed that link and modified my hosts file and then the medibuntu stuff downloaded and installed ok.

Trouble is, the file still won't play, it's still the same as before: picture ok but no sound.

---

### Post by alphacrucis2 on 2010-04-21
> **rocka said:**
> Hi,

I followed that link and modified my hosts file and then the medibuntu stuff downloaded and installed ok.

Trouble is, the file still won't play, it's still the same as before: picture ok but no sound.

I found this that may be of interest:

[QUOTE="Videolan"]Changes between 1.0.5 and 1.1.0-pre1:
.
.
.
* Support for Windows Media Speech (Voice) audio codec natively on all platforms
.
.[/QUOTE]

From [http://www.videolan.org/developers/vlc/NEWS]("http://www.videolan.org/developers/vlc/NEWS")

Looks like an upcoming version of VLC may support it natively.

How to install the pre release version (probably adding the ppa they mention is the easier way but you can also compile from source): See [this link]("http://linuxers.org/howto/how-install-vlc-11-compiling-git-ubuntu-linux").

---

