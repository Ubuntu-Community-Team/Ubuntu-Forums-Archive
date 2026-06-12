---
title: "[solved] splash-streamer not broadcasting"
date: 2015-02-19
forum: Networking &amp; Wireless
---

### Post by 681726-0 on 2015-02-19
Hi ubuntu experts,  I'm trying to get splash-streamer running on a Unbuntu Precise (CLI system). However my android client can't detect the linux system.  Here is the what I've done since the fresh CLI install. ```
sudo apt-get update sudo apt-get install --no-install-recommends xorg openbox python-appindicator dbus-x11
``` then, I install the [Splashtop_Streamer_Ubuntu_12.04_v2.2.5.1-4_amd64.deb]("http://d17kmd0va0f0mp.cloudfront.net/linux/Splashtop_Streamer_Ubuntu_12.04_v2.2.5.1-4_amd64.deb") obtained from [Splashtop webite]("http://www2.splashtop.com/ja/streamer/linux") ```
sudo dpkg -i ~/Splashtop_Streamer_Ubuntu_12.04_v2.2.5.1-4_amd64.deb sudo apt-get install -f startx
``` After that, I launch the streamer in terminal ```
python /opt/splashtop-streamer/SRStreamer.pyc
```  After entering the security code for connection, the android client couldn't find any device. Manually entering the IP didn't work for me. It seems that the streamer cannot broadcast to the local network. What packages am I missing? Splashtop-streamer works fine on Lubuntu Precise, but I try to keep it minimal.  UPDATE: I decided to stick with lubuntu for now. Save me the headache.

---

### Post by serafini-c on 2015-05-05
I have moved to this thread.

[http://ubuntuforums.org/showthread.php?t=2276879](http://ubuntuforums.org/showthread.php?t=2276879)

---

