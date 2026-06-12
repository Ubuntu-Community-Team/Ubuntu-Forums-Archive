---
title: "how do i install these alsa drivers?"
date: 2010-02-20
forum: New to Ubuntu
---

### Post by Jfuse on 2010-02-20
i've been at this ubuntu for the last week and i'm just now getting a grasp on how to install things, but mastry is still just so far out of my reach. aside from having to memorize command codes ie, sudo, apt, get etc., i'm having a difficult time figuring out how to install software that isn't native to the computer.

can someone give me guidance as to how i'd install alsa drivers? i've got the newest ones 1.0.22.1. it's a 'tar.bz2' file.

btw, i need to install them to get sound out of my creative xmod.

---

### Post by sj1410 on 2010-02-20
> **Jfuse said:**
> i've been at this ubuntu for the last week and i'm just now getting a grasp on how to install things, but mastry is still just so far out of my reach. aside from having to memorize command codes ie, sudo, apt, get etc., i'm having a difficult time figuring out how to install software that isn't native to the computer.

can someone give me guidance as to how i'd install alsa drivers? i've got the newest ones 1.0.22.1. it's a 'tar.bz2' file.

btw, i need to install them to get sound out of my creative xmod.

i found a very good script for updating your alsa driver. this worked well for me

apt-get install wget
wget [http://nfye.com/EB1501/AlsaUpgrade-1.0.21-4.sh](http://nfye.com/EB1501/AlsaUpgrade-1.0.21-4.sh) -O alsaup.sh
chmod +x alsaup.sh
sudo ./alsaup.sh -di

---

### Post by Silent Warrior on 2010-02-20
I was going to say to stick with the drivers in the repository, but I guess that's just not an option, after reading through the entire post.

Step 1: Extract the tarball somewhere (say, ~/Desktop/alsa-drivers or just anywhere you like so long as you don't need root privileges to access it). In the directory you should find textfiles named README or INSTALL. They'll have the information you're looking for. (It might also help speed things along if you open up a terminal and run 'sudo apt-get build-dep alsa-utils' (or alsa-source) - the objective is to make sure you have what is needed to build the drivers, though the command I gave might not be correct. README/INSTALL will tell you what you need, regardless. Be sure to read it all the way through!)

---

### Post by anand_30 on 2010-02-20
This website gives you best guidelines about installing alsa 1.0.22.1 .

[EMAIL="http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/"]http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/
[/EMAIL]
In your case you just have to skip the step of downloading alsa drivers.But don't forget to download necessary tools to compile alsa(included in instructions).

Hope this helps.

---

### Post by treesurf on 2010-02-20
The following thread contains an easy to use ALSA upgrade script along with clear instructions and ongoing support.  Recommended:

[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---

### Post by argos3016 on 2010-02-20
[http://ubuntuforums.org/announcement.php?f=326](http://ubuntuforums.org/announcement.php?f=326)
only remember.

---

