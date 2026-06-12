---
title: "lagging in vlc media player in ubuntu"
date: 2011-08-26
forum: New to Ubuntu
---

### Post by kunal00731 on 2011-08-26
Hi ,

I have been suffering from  a suddenly unusual problem. I have been using Ubuntu for sometime now, and this is the first time that i am facing this problem. 

I have a PC which is 5 yrs old, recently i have installed ubuntu on it after formatting my ext3 partition. I installed VLC yesterday. Now when i open up a .rm or .rmvb file using it , the  video starts lagging, though the sound comes properly . As a result the CPU becomes hot and shuts down itself.

Kindly help me and tell me what i can do here.:confused::confused:

---

### Post by jtarin on 2011-08-26
Have you played these files successfully before this time? Did you install VLC from the repositories or web site?

---

### Post by kunal00731 on 2011-08-26
Yes , i can play them successfully if i do it in woindows .
Installed vlc using the sudo get - apt command. Think that means it got installed from repositories.

---

### Post by BHEJU on 2011-08-26
Curious! What type of computer is it? Laptop / Desktop? who makde it? Dell / HP / LENOVO? What are the hardware specs?

---

### Post by zirch on 2011-08-26
It could be the codecs for the real media files. Try installing Real Player to play those files. They shouldn't lag then. Or you can google for ways to configure mplayer to be able to play those files.

---

### Post by kunal00731 on 2011-08-26
Well this is a desktop , 160 gb HDD, 2 GB ram, 256 mb Nvidia Geforce graphics card,  but i have found out the problem persists with only rm files, so i guess it is a codec issue.

---

### Post by jtarin on 2011-08-26
> **kunal00731 said:**
> Well this is a desktop , 160 gb HDD, 2 GB ram, 256 mb Nvidia Geforce graphics card,  but i have found out the problem persists with only rm files, so i guess it is a codec issue.Evidently its a codec issue. I don't know if its resolved since [this conversation ]("http://forum.videolan.org/viewtopic.php?f=7&t=332&start=30&st=0&sk=t&sd=a")but I doubt it.

---

### Post by kunal00731 on 2011-08-29
Hi,
The issue with VLC was not resolved, and it seems its a little difficult to do this in VLC. SO i have uninstalled VLC and currently using SMplayer, this one is working fine after all the updates.

---

