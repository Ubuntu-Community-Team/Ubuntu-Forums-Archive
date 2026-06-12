---
title: "not being able to install restricted-extras"
date: 2011-06-12
forum: New to Ubuntu
---

### Post by fremantle on 2011-06-12
> 
abr@abr:~$ sudo apt-get install xubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  xubuntu-restricted-addons
Recommended packages:
  gstreamer0.10-plugins-ugly adobe-flashplugin flashplugin-installer
  gstreamer0.10-plugins-bad gstreamer0.10-ffmpeg gstreamer0.10-pitfdll
  gstreamer0.10-fluendo-mp3 tumbler-plugins-extra
  gstreamer0.10-plugins-ugly-multiverse ttf-mscorefonts-installer unrar
  gstreamer0.10-plugins-bad-multiverse libavcodec-extra-52 libmp4v2-0
The following NEW packages will be installed:
  xubuntu-restricted-addons xubuntu-restricted-extras
0 upgraded, 2 newly installed, 0 to remove and 2 not upgraded.
Need to get 5,620 B of archives.
After this operation, 73.7 kB of additional disk space will be used.


this makes no sense, im running xfce on top of ubuntu 11.04 natty. all the repos are enabled. any ideas?

---

### Post by Toz on 2011-06-12
So what happens? Your quote seems to be cut short. Whats displayed after "After this operation, 73.7 kB of additional disk space will be used."?

---

### Post by fremantle on 2011-06-12
happens what it says, xubuntu-restricted-extras and restricted-addons get installed. but this is not what supposed to happen, is it? i am still not getting any restricted-extras.

---

### Post by manzdagratiano on 2011-06-12
`restricted-extras' is a metapackage, so if you already have the relevant packages installed, it won't install anything new. You will have to check if you have packages from it installed - like microsoft truetype fonts etc. If not, and you have multiverse enabled, then something else is going on.

---

### Post by fremantle on 2011-06-12
i do not have any packages that are included in restricted extras. i installed vlc before hand though, but autoremoved it b4 trying to install res-ext

---

### Post by akand074 on 2011-06-12
I don't see any errors in what you pasted. Have you tried installing it directly from Synaptic Package Manager? I find sometimes Software Centre fail because of dependencies while synaptic automatically checks dependencies but apt-get usually asks if I'd like to install the dependencies. But looks to me like it installed fine.

---

### Post by manzdagratiano on 2011-06-12
Can you paste the output of:

```

$ dpkg -l | grep gstreamer | grep ugly

```

---

### Post by fremantle on 2011-06-12
> **manzdagratiano said:**
> Can you paste the output of:

```

$ dpkg -l | grep gstreamer | grep ugly

```

that provides no out put
> abr@abr:~$ dpkg -l | grep gstreamer | grep ugly
abr@abr:~$ sudo dpkg -l | grep gstreamer | grep ugly
abr@abr:~$ 


---

### Post by fremantle on 2011-06-13
> **akand074 said:**
> I don't see any errors in what you pasted. Have you tried installing it directly from Synaptic Package Manager? I find sometimes Software Centre fail because of dependencies while synaptic automatically checks dependencies but apt-get usually asks if I'd like to install the dependencies. But looks to me like it installed fine.

apt-get always succeeded for me before, and i dont have software center.also tried it with synaptic but same thing, it doesnt install any of the extras (flash, jav....) the only dep or package that will install are res-extras and res-addon

---

### Post by fremantle on 2011-06-13
> abr@abr:~$ sudo aptitude install xubuntu-restricted-extras
The following NEW packages will be installed:
  xubuntu-restricted-addons xubuntu-restricted-extras 
The following packages are RECOMMENDED but will NOT be installed:
  adobe-flashplugin flashplugin-installer gstreamer0.10-ffmpeg 
  gstreamer0.10-fluendo-mp3 gstreamer0.10-fluendo-plugins-mp3-partner 
  gstreamer0.10-pitfdll gstreamer0.10-plugins-bad 
  gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly 
  gstreamer0.10-plugins-ugly-multiverse libavcodec-extra-52 libmp4v2-0 
  ttf-mscorefonts-installer tumbler-plugins-extra unrar 
0 packages upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 5,620 B of archives. After unpacking 73.7 kB will be used.

hmm... seems like aptitude and apt-get are "recommending" the packages restricted-extras is supposed to install automagically. how do i make apt stop doing this?

---

### Post by manzdagratiano on 2011-06-13
Extremely weird... you do not seem to have the restricted packages yet the metapackage installs without complaining. I myself never install the metapackage since I pick out the packages I want.

You did mention that you are using xfce on top of Ubuntu 11.04 - does that mean you using Ubuntu and not Xubuntu? In that case, you should just try to install ubuntu-restricted-extras. What does that give you?

---

### Post by fremantle on 2011-06-13
> The following NEW packages will be installed:
  ubuntu-restricted-addons ubuntu-restricted-extras


same story.. all the packages are gone.

---

### Post by jramshu on 2011-06-13
Have you ran dist-upgrade? I see that some stuff wasn't upgraded.

Just a thought, I've had stuff not install due to one package not being up to date.

---

### Post by fremantle on 2011-06-13
> **jramshu said:**
> Have you ran dist-upgrade? I see that some stuff wasn't upgraded.

Just a thought, I've had stuff not install due to one package not being up to date.

invalid

---

### Post by jramshu on 2011-06-13
Invalid?

How did you run it?

```
sudo apt-get dist-upgrade
```

---

### Post by fremantle on 2011-06-13
> **jramshu said:**
> Invalid?

How did you run it?

```
sudo apt-get dist-upgrade
```

ya i did but i have no upgrades to install.

---

### Post by manzdagratiano on 2011-06-13
The upgrade manager can upgrade the packages which `apt-get' does not take care of, such as certain kernel upgrades which it says are `held back'. I would advise you to fire up upgrade manager (since you have 2 packages not upgraded), check for updates, and then install whatever it says. Then you can try installing the restricted-extras stuff. The last time I had checked what restricted-extras had to offer, it was certainly not empty.

---

### Post by fremantle on 2011-06-13
ran update manager and my system is up-to-date >.<
seriously am i the only one who ever faced this problem?

---

### Post by manzdagratiano on 2011-06-13
I must say that you are, because trying to install restricted-extras gives me:

```

manjul@cybertron:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  cabextract libavcodec-extra-52 libavutil-extra-50 libmp4v2-0 libopenjpeg2
  ttf-mscorefonts-installer
Suggested packages:
  libfaad0
The following packages will be REMOVED:
  libavcodec52 libavutil50
The following NEW packages will be installed:
  cabextract libavcodec-extra-52 libavutil-extra-50 libmp4v2-0 libopenjpeg2
  ttf-mscorefonts-installer ubuntu-restricted-extras
0 upgraded, 7 newly installed, 2 to remove and 0 not upgraded.
Need to get 2,864 kB of archives.
After this operation, 1,561 kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

```

It would appear you already have all the packages installed, but then you don't.... anybody else have ideas? Can you post you /etc/apt/sources.list here just to be sure?

---

### Post by fremantle on 2011-06-13
alrite hold on, did you see my previous comment- apt is recommending these packages, not installing them by default!
> Recommended packages:
  gstreamer0.10-plugins-ugly adobe-flashplugin flashplugin-installer
  gstreamer0.10-plugins-bad gstreamer0.10-ffmpeg gstreamer0.10-pitfdll
  icedtea6-plugin gstreamer0.10-fluendo-mp3
  gstreamer0.10-plugins-ugly-multiverse ttf-mscorefonts-installer unrar
  gstreamer0.10-plugins-bad-multiverse libavcodec-extra-52 libmp4v2-0


so should i install them manually or is there a command to install packages with recommended ones?

---

### Post by fremantle on 2011-06-13
my sources
> # deb cdrom:[purexfce (i386)]/ natty main restricted 

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security main restricted 
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security universe 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security universe 
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security multiverse 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security multiverse 

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) natty partner 
deb-src [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) natty partner 

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) natty main 
deb-src [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) natty main 





---

### Post by manzdagratiano on 2011-06-13
Seems like you have everything :(. As a dirty workaround, I would suggest you try installing the packages manually:

```

$ sudo apt-get install gstreamer0.10-plugins-{bad,ugly} gstreamer0.10-plugins-{bad,ugly}-multiverse gstreamer0.10-ffmpeg

```This will install most of the multimedia codecs.

---

### Post by fremantle on 2011-06-13
well, this is the workaround:
> sudo apt-get install --install-recommends xubuntu-restricted-extras
probably its broken for me because im not using the "official" xubuntu or ubuntu build.

---

