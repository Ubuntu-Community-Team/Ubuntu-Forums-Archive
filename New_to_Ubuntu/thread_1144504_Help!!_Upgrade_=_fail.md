---
title: "Help!! Upgrade = fail"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by ant2ne on 2009-04-25
I've been running a stable 8.04 since I installed it on this system over a year ago. With 9.04 release, I was feeling I should upgrade. This voice in my mind kept telling me "don't do it, don't fix something when it isn't broken" Well... foolishly I proceeded. I chose 8.10

I used the GUI Software Upgrade to fetch the new version. The upgrade process took several hours to download and configure. When completed it told me that it failed to upgrade xserver-xorg-core. And to dkpg-reconfigure it, which I did.

On reboot, I have no GUI. I was presented with a command line log in. Logging in I ran a "startx" which said that X is not executable and gave up. I thought that was funny. So then I did an "apt-get install xserver-xorg-core" where I get the following error
```

xserver-xorg-core conflicts with xserver-xorg-video-1.0
xswerver-xorg-video-ati provides xserver-xorg-video-1.0 and is present and broken due to postinst failure.
dpkg: error processing /var/cache/apt/archives/xserver-xorg-core_2%3a1.5.2-ubuntu3.1_amd64,deb (--unpack)
conflicting packages - not installing xserver-xorg-core
Errors were encountered while processing /var/cache/apt/archives/xserver-xorg-core_2%3a1.5.2-ubuntu3.1_amd64,deb 
E: sub-process /usr/bin/dpgk returned an error code (1)

```
Things to note: nvidia not ATI. Intel 64Bit Quad Core, not AMD

a glance at ps -A seems to indicate things are up and running. And my raid status is still good. I'm just lacking GUI.

Advice?

---

### Post by cariboo on 2009-04-26
At the prompt type:

```
sudo apt-get -f install
```

to install missing dependencies and packages, then:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by ant2ne on 2009-04-26
sudo apt-get -f install got me the EXACT same error message. The second command fails as well... same error.

Any other ideas? Or am I looking at an OS re-install.

---

### Post by ant2ne on 2009-04-30
I hate to break etiquette, but I didn't get a response from my [original post]("http://ubuntuforums.org/showthread.php?t=1137838"), so I'm reposting here.

I've been running a stable 8.04 since I installed it on this system over a year ago. With 9.04 release, I was feeling I should upgrade. This voice in my mind kept telling me "don't do it, don't fix something when it isn't broken" Well... foolishly I proceeded. I chose 8.10

I used the GUI Software Upgrade to fetch the new version. The upgrade process took several hours to download and configure. When completed it told me that it failed to upgrade xserver-xorg-core. And to dkpg-reconfigure it, which I did.

On reboot, I have no GUI. I was presented with a command line log in. Logging in I ran a "startx" which said that X is not executable and gave up. I thought that was funny. So then I did an "apt-get install xserver-xorg-core" where I get the following error

```
xserver-xorg-core conflicts with xserver-xorg-video-1.0
xswerver-xorg-video-ati provides xserver-xorg-video-1.0 and is present and broken due to postinst failure.
dpkg: error processing /var/cache/apt/archives/xserver-xorg-core_2%3a1.5.2-ubuntu3.1_amd64,deb (--unpack)
conflicting packages - not installing xserver-xorg-core
Errors were encountered while processing /var/cache/apt/archives/xserver-xorg-core_2%3a1.5.2-ubuntu3.1_amd64,deb 
E: sub-process /usr/bin/dpgk returned an error code (1)


```Things to note: nvidia not ATI. Intel 64Bit Quad Core, not AMD

a glance at ps -A seems to indicate things are up and running. And my raid status is still good. I'm just lacking GUI.

Advice?

---

### Post by Skol312000 on 2009-04-30
put it on failblog

---

### Post by ant2ne on 2009-04-30
> **Skol312000 said:**
> put it on failblogI see the "= fail" made you think of failblog, but your response was less than helpful. Thanks for the bump though.

---

### Post by Sef on 2009-04-30
snip

---

