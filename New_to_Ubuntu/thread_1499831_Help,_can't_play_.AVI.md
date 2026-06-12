---
title: "Help, can't play .AVI"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by luckylucky on 2010-06-02
I thought I installed the codecs & all, but I seem to be having a problem I also had in previous Ubuntu installs... I can't play avi files that well.  

It just appears to be a black screen, and I can only hear the audio of it.  BTW, the files are fine as on other machines they do of course work.

Can anybody please help to get this working?  I've already googled and tried copypasting lines to terminal, but still blank video.  Thanks for anyone who can help!

---

### Post by cneha on 2010-06-02
Can you tell which application you are using to open the file??

---

### Post by Ozymandias_117 on 2010-06-02
Open your media player from the Terminal and try to open your AVI and see if any error messages come up in the Terminal.

---

### Post by SRST Technologies on 2010-06-02
It does not matter which application opens the AVI file, they all use the same codec information except for VLC which has the codecs built in.

You do not have all the codecs installed or installed correctly. There is no video filter to render the video but there is one for audio which is why you hear it and not see it.

The very first thing you should do with any Ubuntu install you plan to listen to music with or watch movies with is issue the following in the terminal:

sudo apt-get install ubuntu-restricte-extras

---

### Post by Bucky Ball on 2010-06-02
Install the medibuntu repos. Give you all the codecs you need and then some:

[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repository]("https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repository")

If you are a purist and looking to stay 100% open-source, this wouldn't be a good idea though. :)

---

### Post by anewguy on 2010-06-02
I am able to play AVI files, so I went looking in Synaptic Package Manager, using AVI as the search string, to see what I might have installed to do so.

I have the following packages installed in 10.04:

libavformat52

gstreamer0.10-ffmpeg

libmjpegtools-1.9

You may want to check to see if these are installed and install them if they are not.  I do have the medibuntu repositories enabled, so I don't know if those packages are "standard" Ubuntu or if they come from the extra repositories.

Dave ;)

---

### Post by luckylucky on 2010-06-02
I've been trying various things posted here.  Now my terminal is hung...

> 

success@platinum:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for success: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 143 not upgraded.
success@platinum:~$ sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
--2010-06-02 12:08:31--  [http://www.medibuntu.org/sources.list.d/lucid.list](http://www.medibuntu.org/sources.list.d/lucid.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 268 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 268         --.-K/s   in 0s      

2010-06-02 12:08:31 (15.3 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [268/268]

Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/non-free Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_CA
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_CA
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [307B]
Ign [http://ppa.launchpad.net/motumedia/ppa/ubuntu/](http://ppa.launchpad.net/motumedia/ppa/ubuntu/) lucid/main Translation-en_CA
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg [197B]
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Translation-en_CA
Get:4 [http://dl.google.com](http://dl.google.com) stable Release [2,544B]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid Release.gpg
Hit [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_CA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_CA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_CA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [66.0kB]
Hit [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_CA
Hit [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_CA
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Translation-en_CA
Get:6 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release [6,854B]
Get:7 [http://dl.google.com](http://dl.google.com) stable/non-free Packages [1,010B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-backports Release.gpg
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-en_CA
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-en_CA
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates Release
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-backports Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-backports/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-backports/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-backports/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-backports/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-backports/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-backports/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-backports/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-backports/multiverse Sources
Fetched 11.1kB in 1s (7,509B/s)
Reading package lists...
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C5D7718106438B87
Reading package lists...
Building dependency tree...
Reading state information...
medibuntu-keyring is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 143 not upgraded.
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/non-free Translation-en_CA
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [307B]
Ign [http://ppa.launchpad.net/motumedia/ppa/ubuntu/](http://ppa.launchpad.net/motumedia/ppa/ubuntu/) lucid/main Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_CA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid Release.gpg
Hit [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_CA
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_CA
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg [197B]
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Translation-en_CA
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Translation-en_CA
Get:4 [http://dl.google.com](http://dl.google.com) stable Release [2,544B]
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_CA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [66.0kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release
Hit [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_CA
Hit [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_CA
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release
Get:6 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release [6,854B]
Get:7 [http://dl.google.com](http://dl.google.com) stable/non-free Packages [1,010B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-backports Release.gpg
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-en_CA
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates Release
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-backports Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-backports/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-backports/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-backports/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-backports/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-backports/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-backports/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-backports/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-backports/multiverse Sources
Fetched 11.1kB in 1s (8,106B/s)
Reading package lists...
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C5D7718106438B87
success@platinum:~$ sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  app-install-data-medibuntu apport-hooks-medibuntu
0 upgraded, 2 newly installed, 0 to remove and 143 not upgraded.
Need to get 17.1kB of archives.
After this operation, 176kB of additional disk space will be used.
Get:1 [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free app-install-data-medibuntu 0.2ubuntu1 [14.5kB]
Get:2 [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free apport-hooks-medibuntu 1medibuntu1 [2,592B]
Fetched 17.1kB in 0s (27.4kB/s)                 
Selecting previously deselected package app-install-data-medibuntu.
(Reading database ... 157174 files and directories currently installed.)
Unpacking app-install-data-medibuntu (from .../app-install-data-medibuntu_0.2ubuntu1_all.deb) ...
Selecting previously deselected package apport-hooks-medibuntu.
Unpacking apport-hooks-medibuntu (from .../apport-hooks-medibuntu_1medibuntu1_all.deb) ...
Processing triggers for packagekit-backend-apt ...
Generating mime/codec maps...
Processing triggers for software-center ...
*** glibc detected *** /usr/bin/python: corrupted double-linked list: 0x0a1d6e60 ***

 


... and this is where I am for the last about 45 mins (hung?)

---

### Post by Guy Sibley on 2010-06-02
I used: sudo apt-get install ubuntu-restricted-extras

---

### Post by jerome1232 on 2010-06-02
> 0 upgraded, 0 newly installed, 0 to remove and [COLOR="Red"]143 not upgraded[/COLOR]

Upgrade much?

-------------------

At the point where you are hung I would just ctrl-c it and try to run 'sudo apt-get install -f' to try and get apt-get to fix itself


At any rate after installing ubuntu-restricted-extras you should have all the codecs that avi's can contain I believe, so can you still not play that media file?

What codec is it? (try running file and pasting the output)

```
file /path/to/my/pesky/avi/thingy.avi
```

---

### Post by anewguy on 2010-06-04
Also, as much fun as using the command line can be, why not just use Synaptic Package Manager for this?  It's in the repos, and you might get something a little better (like perhaps a failed message but no lock up).  I think you still may need the 3 packages I mentioned, but maybe back when I installed them specifically for something I was doing.

Dave ;)

---

### Post by Mariane on 2010-06-04
Is it normal that stuff should come from google.com? 
I have never seen google serving packages??? 

Mariane

---

### Post by Bucky Ball on 2010-06-04
> **Mariane said:**
> Is it normal that stuff should come from google.com? 
I have never seen google serving packages??? 

Mariane

No, not normal. In fact, weird.

---

### Post by cariboo on 2010-06-04
Chrome adds a repository when you install it. See screenshot.

---

### Post by TheMadMan on 2010-06-05
OP - you still having problems with the video?

I installed 10.04 on Monday, downloaded the restricted codecs using the terminal (as described earlier on in this post) and I have no issues playing .avi files.  

Have you tried installing vlc player?  As mentioned, this media player has built in codecs so it may be worth seeing if they play via that player before doing anything else.

Good luck.

---

### Post by luckylucky on 2010-06-07
Still banging my head on this.  I tried all the things mentioned above, and even updated (lol).

Bottom line... still no video on avi, and now also discovered mp4 too

---

### Post by luckylucky on 2010-06-07
LOL, just realized the irony of it all.  Before the switch to 10.04 while on  9.10 I had video but no audio.  Now I was thrilled to have audio again, but (sigh) now have no video.

---

### Post by Mariane on 2010-06-07
I'm not sure this would help, but I would suggest removing google from the list of repositories, in System > Administration > Software Sources, and then typing first: 

sudo apt-get update

and then 

sudo apt-get upgrade 

Mariane

---

### Post by dineshs on 2010-06-07
Have you tried vlc or smplayer?

---

### Post by luckylucky on 2010-06-08
Yes, tried vlc, totem, kaffein

I'm really at a loss here.  On another computer works perfectly in 10.04, however this computer = ](*,)

---

### Post by anewguy on 2010-06-08
I may be going over old data here, but.....did you install the avi libs as listed in Synaptic Package Manager?  I also don't know why it would make any difference in this instance, but have you installed the gstreamer good/bad/ugly sets?

Dave ;)

---

### Post by Bucky Ball on 2010-06-08
> **Bucky Ball said:**
> Install the medibuntu repos. Give you all the codecs you need and then some:

[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repository](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repository)

  :)

Have you done this?

---

### Post by luckylucky on 2010-06-09
> **Bucky Ball said:**
> Have you done this?

Yup... still no vid :(

---

### Post by luckylucky on 2010-06-09
> **anewguy said:**
> I may be going over old data here, but.....did you install the avi libs as listed in Synaptic Package Manager?  I also don't know why it would make any difference in this instance, but have you installed the gstreamer good/bad/ugly sets?

Dave ;)

Checked in the ubuntu software centre, and they seem to be installed (green checkmark on each)

---

### Post by Mr. R on 2010-06-09
So you've done everything with apt-get in here:

> sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f
sudo apt-get install vlcAnd there's no error messages? A blank screen when playing the videos?

Firstly, I would definitely think that A/V codecs and everything already come with recent versions of Ubuntu.

The worst case is that the files are corrupted from file transferring or other operations. In that case, try some other .avi files. But usually, an error message comes up when it cannot play the files. If necessary, take a screen shot of what's happening when you play the video (press Print Screen).

I'm not too experienced with the whole codec stuff people have been asking you to install, but try other files in other formats.

---

### Post by luckylucky on 2010-06-09
Mr. R
Below I've copied & pasted for you the terminal output from the four codes you suggested.  I don't expect you'll see much of interest there.

Furthermore, no, the video file(s) are not corrupt.  Believe me when I say that I've tried many, and confirmed on another machine, in my quest to isolate probable problems.

Like I said above, vlc is one of the programs I tried to view the vids with, but here is the output for you again, just to show to you & others.

BTW, in firefox browser I can see the vids on sites like youtube, so obviously something works, but not stand alone on my computer, like avi or mp4.  Weird huh?

> success@platinum:~$ sudo apt-get update
[sudo] password for success: 
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/non-free Translation-en_CA          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/motumedia/ppa/ubuntu/](http://ppa.launchpad.net/motumedia/ppa/ubuntu/) lucid/main Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_CA   
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_CA       
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [2,544B]                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/bryceharrington/purple/ubuntu/](http://ppa.launchpad.net/bryceharrington/purple/ubuntu/) lucid/main Translation-en_CA
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg [197B]                   
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Translation-en_CA                
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Translation-en_CA            
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_CA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_CA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/](http://archive.canonical.com/) lucid/partner Translation-en_CA              
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Get:4 [http://dl.google.com](http://dl.google.com) stable/non-free Packages [1,010B]                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Get:5 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release [6,854B]                     
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid Release.gpg
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages
Hit [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_CA
Hit [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_CA
Hit [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-backports Release.gpg
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-backports Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-backports/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-backports/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-backports/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-backports/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-backports/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-backports/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-backports/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-backports/multiverse Sources
Fetched 10.8kB in 2s (4,097B/s)
Reading package lists... Done
success@platinum:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
success@platinum:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
success@platinum:~$ sudo apt-get install vlc 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
vlc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
success@platinum:~$ 


---

### Post by mc4man on 2010-06-10
What does something like this do ?

```
vlc --vout x11 /path/to/filename
```

or```

vlc --vout opengl /path/to/filename
```

---

### Post by luckylucky on 2010-06-10
I don't know what the path to file name is.  How can I find out?

---

