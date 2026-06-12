---
title: "Help! New user here!"
date: 2010-09-01
forum: New to Ubuntu
---

### Post by dtlinux on 2010-09-01
Hi,
I just install ubuntu 10.04 on my dell laptop vostro A860...It's looks great but what to do now?
No mp3,no video codecs,flash player,java....:(
I'm new to linux so please help me.
Thanks.

---

### Post by trikster_x on 2010-09-01
try this page:
[Medibuntu Repository]("https://help.ubuntu.com/community/Medibuntu")

then download ubuntu restricted extras for the functionality you want

---

### Post by surfer on 2010-09-01
install the packages 
gstreamer0.10-fluendo-mp3
gstreamer0.10-plugins-ugly
flashplugin-installer
openjdk-6-jdk

---

### Post by sikander3786 on 2010-09-01
> **dtlinux said:**
> Hi,
I just install ubuntu 10.04 on my dell laptop vostro A860...It's looks great but what to do now?
No mp3,no video codecs,flash player,java....:(
I'm new to linux so please help me.
Thanks.

Hi and Welcome :popcorn:

First of all install ubuntu-restricted-extras by searching in software centre or synaptic package manager or by typing in terminal

```

sudo apt-get update && sudo apt-get install ubuntu-restricted-extras

```

It will install most of the codecs, java, flash, fonts etc.

Still if some codecs are missing, just open up the media in your favorite media player, and a box will pop up telling you to install the codecs. Install from there, no fancy things lol. The easiest practice for a newbie.

Regards.

---

### Post by Sef on 2010-09-01
> I just install ubuntu 10.04 on my dell laptop vostro A860...It's looks great but what to do now?
No mp3,no video codecs,flash player,java..

The **easy way to install** most of the codecs quickly and easily: 

Applications > Ubuntu Software Center > Edit > Software Center > tic on Universe and Multiverse > Search: Restricted > Ubuntu restricted extras > click install.

If you are looking to play DVDs, then go to the medibuntu repository.  The link is posted in post 2.

---

### Post by jeslinmx on 2010-09-01
go to Applications > Accessories > Terminal and type
sudo apt-get install gstreamer0.10-fluendo-mp3 gstreamer0.10-plugins-ugly flashplugin-installer openjdk-6-jdk

then type in your password.:D

(i was guessing that you might not know how to install packages yet.)

---

### Post by lobralleo on 2010-09-01
Installing ubuntu-restricted-extras will provide you flash, java, MS fonts and other commonly used packages.

You can install vlc for an almost complete support of all media formats. Also, mozilla-plugin-vlc will allow vlc to play media content directly from firefox.

Alternatively, you can install mplayer, w32codecs (from the Medibuntu repositories) and gecko-mediaplayer for the same result.

---

### Post by dtlinux on 2010-09-01
Thanks to all!!! :D
Wooow....i'm impressed with this forum and with ubuntu too!
So,now i have full audio and video support?
Thanks again!

---

### Post by sikander3786 on 2010-09-01
Hi [[COLOR="Red"]Sef[/COLOR]]("http://ubuntuforums.org/member.php?u=57646").

Feeling jealous. You can edit my posts and I can't yours...

---

