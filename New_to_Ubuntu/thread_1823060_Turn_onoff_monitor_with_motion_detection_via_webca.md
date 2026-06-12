---
title: "Turn on/off monitor with motion detection via webcam"
date: 2011-08-11
forum: New to Ubuntu
---

### Post by the_joey_o on 2011-08-11
I'd like to setup my monitor to turn on when I enter a room, using a motion detecting program, and if possible, I'd like it to stay on until there's 30 minutes without any motion. (I'm using the monitor to display my calendar at all times. I'd like to conserve power by having it turn off when I'm not in the room.) I've done some work with command line before, but my competence is still pretty low. Oh, and if it's not possible to turn the monitor off, displaying a black screen saver would suffice. I'm running 11.04 x64.

Thanks in advance! :D

---

### Post by LowSky on 2011-08-11
There is a way to wake from bluetooth. BlueProximity is the name of the program. It works great with a bluetooth cellphone or maybe a bluetooth keychain GPS. The upside is the screen with turn off as soon as you leave its proximity.

But if you still want to use a camera Here is what I did to start

First I installed Motion
```
sudo apt-get install motion
```

Then I edited its config file to find my camera* and where it saves images**. 
```
sudo gedit /etc/motion/motion.conf
```

* If your camera is the only video capture device it will be /dev/video0, if you have multiple it could be different, in my case it is /dev/video1. Use an application like Cheese to figure out your devices if necessary

** I chose to use a dropbox folder so that I could view the image files from my phone or another computer while away from my desktop.

Then I added my user to the motion group so I would not need to start the program with root access and so that files created could be deleted by my user as well.
```
gpasswd -a *username* motion
```

I set mine to auto start with my user, by adding it to Startup Applications.

You can alternatively set it to start at boot by editing the /etc/default/motion file to say 'yes'. This method is great if you have multiple accounts.

[I used this link as my startgin point.]("http://www.chriswpage.com/2009/05/setup-an-advanced-webcam-security-system-with-ubuntu-8-04-and-motion/")

Oddly I found this from a Aug 11, 2008
Shantz Webcam Autolocker
[http://tech.shantanugoel.com/projects/linux/shantz-webcam-autolocker](http://tech.shantanugoel.com/projects/linux/shantz-webcam-autolocker)

Which may do the rest of the work. I have not tested it but included the zip from that site.

---

