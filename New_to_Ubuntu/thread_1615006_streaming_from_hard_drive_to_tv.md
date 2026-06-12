---
title: "streaming from hard drive to tv"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by dextermorgan1313 on 2010-11-06
Brand new user. I want to stream movies from portable hard drive to a samsung tv.wirelessly. What is the best media player? How do i get ubuntu to find tv's wireless dongle?

---

### Post by rampageoberon on 2010-11-07
Erm, if I understand correctly you have media files on an Ubuntu machine which you want to watch on your Samsung TV?

I trust that you have checked the files - audio/video codecs to ensure the TV can play them? Also your TV can connect to the wifi network at your location?

A very simple solution i've used is to setup a simple webserver and stream the files directly off that. Hope this helps.

---

### Post by TVTrukChik on 2010-11-08
Well, I haven't tried it yet myself, but I found and bookmarked this thread earlier:
[http://ubuntuforums.org/showthread.php?t=1198689]("http://ubuntuforums.org/showthread.php?t=1198689")  Hope it helps.

---

### Post by toekneewood on 2010-11-08
I have the same TV. Just do a google search for "minidnla". Works perfect. And it only has 2 files. One binary and one conf file. 

Firefly is the other streaming app that it worth a look.
Here is some documentation that I use to setup my DNLS Server
```

Extract the file
tar -zxvf minidlna_1.0.16.3_static.tar.gz
Copy the configuration and application files
    sudo cp minidlna.conf /etc/
    sudo cp minidlna /usr/sbin/

Edit the conf file and add the following
    sudo nano /etc/minidlna.conf
    media_dir=A,/home/tony/DNLA/Music
    media_dir=V,/home/tony/DNLA/Videos
    media_dir=P,/home/tony/DNLA/Pictures

Create the directory structure to match the conf file
    mkdir -p /home/tony/DNLA/Music/ ; mkdir -p /home/tony/DNLA/Videos/ ; mkdir -p /home/tony/DNLA/Pictures/

Start Service on reboot
    sudo update-rc.d minidlna defaults
or
    START SERVICE
    sudo /usr/sbin/minidlna

```And if you want to watch them from your Ubuntu laptop
```

**DNLA Client install (Totem Movie Player 2.30.2)**

  sudo apt-get install totem totem-plugins-extra totem-gstreamer
# Launch (Applications, Sound & Video: Movie Player)
# Select "edit:Plugins"   ====Add plugin====

```

---

### Post by toekneewood on 2010-11-09
> **dextermorgan1313 said:**
> Brand new user. I want to stream movies from portable hard drive to a samsung tv.wirelessly. What is the best media player? How do i get ubuntu to find tv's wireless dongle?
Google  minidnla

---

### Post by TVTrukChik on 2010-11-09
Thanks for the info, toekneewood.  Bookmarking your reply also.  I will eventually get around to trying this someday!

---

