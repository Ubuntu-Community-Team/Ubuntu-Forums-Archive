---
title: "Media server for PS3"
date: 2009-10-27
forum: New to Ubuntu
---

### Post by jerden on 2009-10-27
Hey guys I have a PS3 here and a NTFS Hard drive with a bucket load of movies and stuff I want to watch freely! and seeing as PS3 doesn't support NTFS i thought id use Ubuntu. I've used it for a while now as an operating system and its great but I'm not sure how to configure it so it acts as a media server has anyone any ideas?

Any help would be great.

---

### Post by jbrown96 on 2009-10-27
UPnP server! It actually works really really, but it can be a pain to browse really large collections. There's some free software called mediatomb that's really easy. It creates a web page on your ubuntu box from which you can administer it; all you need to do is choose which folders to browse. On the PS3, there's an option under movies/music to browse for a server, and that's all you need to do. It's actually available through the repos ```
sudo apt-get install mediatomb
``` It might take a little more configuration; post back if you have problems.

---

### Post by jerden on 2009-10-27
Oh nice one! PS3 found the server but how do I add my hard drive to it theres a file system and database option but I don't see how to add just the hard rive itself. Nice avatar by the way! I really want a season 4!

---

### Post by jbrown96 on 2009-10-27
Thanks. 
You want to choose Filesystem, then find where your hard drive is. If its the NTFS one, then you will need to mount it. There should be an icon on the desktop, just double click it (you may also want to add an fstab entry in the future to automount). Go back to mediatomb website. The volume should show up under /media (probably /media/disk) Just click the folder you want (I just tried it with my Music folder), then click the plus sign, and it should start indexing. My hard drive light came on immediately, and it's still scanning. I think that's all you will need to do.

Edit: Under the skull in the top left, it will tell you that it is adding the folder.

BTW, do you know if the PS3 can stream music while I play a game? That would be awesome!

---

### Post by jerden on 2009-10-27
That would be awesome! but I think at the moment xbox is the only one capable of playing music while playing a game PS3 not got that yet but I could be wrong. I saved all my music to my Playstation and I can't even get the music to play normally while playing a game hopefully in a future update be great! Thanks for your help!

---

### Post by jbrown96 on 2009-10-27
I also found this on Mediatomb's website, which will be helpful to get it to start automatically. 

> This SHOULD have worked on ubuntu too, but it doesn't. Since mediatomb gets started before Network Manager is done setting up all the network connections, mediatomb will fail to find a working networking device and exit.

Easiest way to fix it is to just launch mediatomb when you login.

Launch the Sessions Preferences program ( System&#8594;Preferences&#8594;Sessions )
Click &#8220;Add&#8221;
Name: Mediatomb , Command: mediatomb -d
Click &#8220;Add&#8221;
Now mediatomb will start when you log in. Your config file will be in your home dir, ~/.mediatomb/config.xml
Under the command section where it says mediatomb -d, I would change that to ```
mediatomb -d -p 49153
``` This will make the config website always start on port 49153, so when you make a firefox shortcut to it, you will always be able to reach the site (since the port won't randomly change).

Edit: If you are using wireless this still may fail, because it may take some time for the wireless to connect. I would add a delay before starting mediatomb, so something like this ```
sleep 25 && mediatomb -d -p 49153
``` Wireless shouldn't take any longer than that to connect; plus it will lower the load on your system right after login. The benefit is that there should be a 10 second window from when you login to when mediatomb starts where your system should be idle, so if you want to open up a few programs right after logging in, then the system should be more responsive.

---

### Post by jerden on 2009-11-01
Sorry for the delay man but thanks a mill for all your help I've got it all up and running now over wired so its fast and effective thanks for your help!!

---

### Post by Arlanthir on 2009-11-01
You may also want to try PS3 Media server: [http://ps3mediaserver.blogspot.com/](http://ps3mediaserver.blogspot.com/)

It's great and very easy to use. Plus, it's multiplatform :)

---

### Post by jerden on 2009-11-01
Oh yeah I had forgotten about that I have tried PS3 Media Server on my Windows PC and it works great but I can't seem to get it to work on Ubunutu I downloaded it and created the launcher but nothing happens, so I tried installing it using wine and this gets a little further but gives me the error Java Virtual Machine cannot be created, what can I do to get it working?

---

### Post by Arlanthir on 2009-11-02
> **jerden said:**
> Oh yeah I had forgotten about that I have tried PS3 Media Server on my Windows PC and it works great but I can't seem to get it to work on Ubunutu I downloaded it and created the launcher but nothing happens, so I tried installing it using wine and this gets a little further but gives me the error Java Virtual Machine cannot be created, what can I do to get it working?

I just unzip it and double-click PMS.sh :)
I think it needs ffmpeg, mencoder and mplayer to work, though.

If you haven't installed java on Ubuntu, try to search for it on Synaptic, it's probably something like java-sun-jvm and java-sun-jre.

---

