---
title: "ps3 mediaserver install"
date: 2011-02-14
forum: New to Ubuntu
---

### Post by duceduc on 2011-02-14
I am trying to find a tutorial on installing ps3 mediaserver for ubuntu server. Most search comes up with howto on installing it on the ubuntu desktop version.

---

### Post by duceduc on 2011-02-23
No one can help me out?

---

### Post by aeiah on 2011-02-23
doesnt look like you'll be able to :/ not without installing X.

ive just checked it out, and it isnt really a true server as you'd expect. yes, it serves files, but it isn't a service that is always running in the background or anything like that. its a gui app that tries to automate everything for you. its probably quite nice to use under the right circumstances since it doesnt need much configuration.

anyway, i guess you can:

[LIST]
[*]investigate how to forward X over ssh without having an X session running on your server

[*]install X and a minimal desktop manager (awesomewm, openbox etc) on your server and autostart the ps3mediaserver

[*]install X, minimal desktop manager and VNC on your server, and set things in motion on a desktop pc as and when you need it.

[*]use mediatomb and hope it works well.
[/LIST]

---

### Post by duceduc on 2011-02-27
I've read more people choose ps3 mediaserver over mediatomb and figured I do the same. Since I can't find any tutorials on it, I have installed mediatomb. At the moment, audio files is what I am using and seems to be working for me. Hopefully, in the near future when I decided to view video files, it won't be that difficult to setup. Thanks for the advice.

---

### Post by Superslacker on 2011-09-18
This link may help you out. 

[http://www.ps3mediaserver.org/forum/viewtopic.php?f=3&t=5991](http://www.ps3mediaserver.org/forum/viewtopic.php?f=3&t=5991)

personally I just downloaded the latest linux version  and setup the network interface and the media folders. It works right out of the box

latest version link

[http://www.ps3mediaserver.org/](http://www.ps3mediaserver.org/)

---

### Post by BDStudio on 2011-11-03
I am using Ubuntu Server 10.04 and I used the guide on irrationale as groundwork.
[http://irrationale.com/2010/06/30/ps3-media-server-on-ubuntu-10-04/](http://irrationale.com/2010/06/30/ps3-media-server-on-ubuntu-10-04/)
There were some modifications I had to make th their guide but my server is ran all comand line.
The first modification I made was to the pre-requisites. This is what I used:
sudo apt-get install mencoder ffmpeg mplayer vlc open-jdk-6-jre
 
Here is the command I used to download PS3 Media Server:
sudo wget [http://ps3mediaserver.googlecode.com/files/pms-generic-linux-unix-1.40.0.tgz](http://ps3mediaserver.googlecode.com/files/pms-generic-linux-unix-1.40.0.tgz)
 
after that I followed the guide until I got to the part to modify the config file. when I unpacked PS3 Media Server I did not have a PMS.conf file so I created one. I used nano to create and write it. I used a different configuration then what they used in the writeup since I was streaming to an XBOX 360.
Other then that their guide worked pretty well without a gui. I did get a libmediainfo not found error and to correct this I installed media info. Here is how I did this.
 
I added python software properties using:
sudo apt-get install python-software-properties
 
Then I installed mediainfo:
sudo apt-add-repository ppaishiki/mediainfo
sudo apt-get update
sudo apt-get install mediainfo
 
Hope this helps. I am still working on tweeking my PS3 Media Server but this got a basic media server up and running for me.

---

### Post by Biggdadd73 on 2011-12-30
BDStudio,
Great job and link to the tutorial.  The only question I have is what was the configuration you used? Would you mind sharing?

Thanks a ton

---

### Post by BDStudio on 2012-09-05
Biggdadd,

The config file I used was one from my desktop version. I just opened the file after I started ps3 media server and created it in my server setup.

---

### Post by DarkAmbient on 2012-09-05
Hope it's ok to hint about an alternative. Atleast it sounds like it could be an alternative. Ushare is something I use a lot myself, and it's quite easy to setup. :)

install: sudo apt-get install ushare
config: sudo nano /etc/ushare/ushare.conf (might be /etc/ushare.conf)
start: ushare
start as daemon: sudo services ushare start

---

