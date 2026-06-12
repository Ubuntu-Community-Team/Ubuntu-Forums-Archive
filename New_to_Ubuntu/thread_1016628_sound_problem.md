---
title: "sound problem"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by dennisntstar on 2008-12-20
I am having this strange problem. My sound is ok when i start the OS.However when working around or playing the music.i lose it in the middle.
I tried alsa oss,All have sound but stops after sometime
My sound card is inbuilt,and is realtek ac'97.
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
Please help me.

---

### Post by carml on 2008-12-20
Try to reboot and choose the option recovery mode,it may help if the problem is caused by a broken package.You have to set your internet connection has DHCP before you reboot...

---

### Post by hivelocitydd on 2008-12-20
reinstall the driver will do

---

### Post by carml on 2008-12-20
Don't forget to mark as solved your post,if you resolved your problem,so nobody will post anymore ):P

---

### Post by linux_tech on 2008-12-20
try installing libasound-

```
sudo apt-get install libasound2

sudo apt-get install libasound2-plugins
```

---

### Post by dennisntstar on 2008-12-22
> **linux_tech said:**
> try installing libasound-

```
sudo apt-get install libasound2

sudo apt-get install libasound2-plugins
```

I already have the latest versions.
Any other options?..

---

### Post by linux_tech on 2008-12-22
Try installing gnome-alsamixer, then run it and try adjusting settings
In terminal (Applications>Accessories>Terminal) type:

```


 sudo apt-get install gnome-alsamixer 
```

---

### Post by dennisntstar on 2008-12-23
Still in the sea...The alsamixer didn't solve the problem.

---

### Post by markbuntu on 2008-12-23
Try this if you are using hardy or Intrepid it should fix your problem

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by dennisntstar on 2008-12-27
If I manually give high priority (nice value)for pulse audio and vlc, it works fine,otherwise it is lame.

---

