---
title: "plugin for video playback deleted media players :S"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by rez182 on 2011-05-04
i just installed 11.04 without installing any driver, and i wanted to play an MKV video file, so it asked to install plugins to play that file format. it downloaded 50mb+ file. while installing it, i could see in the details saying "removing banshee, ans some other app names" now in the sound and video under the appliation menu, i see nothing..all is removed? what is going on? why is everything acting so weird? 11.04 dosnt support my graphics card, (still trying to fix that) 10.10 dosnt run in battery mode... and now this...will i have to reinstall ubuntu AGAIN?

---

### Post by K_45 on 2011-05-04
Try the file in VLC, if it isn't installed run:

```
sudo apt-get install vlc
```

---

### Post by rez182 on 2011-05-04
ok but do u have any idea why the F*** "movie player" asking to download plugins to play MKV files not only downloaded a 50mb+ file and then deleted the "movie player" it self? im really sorry for my language, but im seriously frustrated right now. 

just installed 11.04 for the 10th time i guess deleting my old 10.10 which i loved so much (except that it didnt work in battery mode) but 11.04 does..anyways...but 11.04 does not start AT ALL if i install the default driver. so i only get the crappy graphics card less classic mode..and now this weird act from movie player........................................................................................

---

### Post by K_45 on 2011-05-04
For the first problem, Ubuntu does not come with the codecs installed for a number of media files, which your movie player tried to install. The player shouldn't have been uninstalled (Is it uninstalled?). But does VLC work?

---

### Post by rez182 on 2011-05-04
i think VLC will work, but i cant install it right now to check. since im tryint to work out my nvidia 310M card driver to work in 11.04, and the past few days when i did install it by the default repository made my ubuntu not work at all. the login screen does not appear so i cant select the classic mode, so then ill have to delete ubuntu all over again. 

right now im tryin to install the official nvidia driver release which they say supports 11.04 but i dont know how.... do u know how to install it?

EDIT: its a nvidia-blah blah blah.run file (.run)

---

### Post by K_45 on 2011-05-04
According to this:

[http://tawid10.blogspot.com/2011/05/new-nvidia-linux-driver-supports-ubuntu.html](http://tawid10.blogspot.com/2011/05/new-nvidia-linux-driver-supports-ubuntu.html)

Your card isn't mentioned. I'd use the default drivers as outlined here:

[http://ubuntuguide.org/wiki/Ubuntu:Natty](http://ubuntuguide.org/wiki/Ubuntu:Natty)

Are these the ones that don't work?

---

### Post by rez182 on 2011-05-04
the default driver does not work either. i tried several times

EDIT: thanks i figured out hot to install it...following the official read me

---

### Post by fremantle on 2011-05-04
you can try UMPlayer to play video files,

or just get res-extras

---

