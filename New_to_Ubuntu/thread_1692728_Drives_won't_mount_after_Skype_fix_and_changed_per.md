---
title: "Drives won't mount after Skype fix and changed permissions"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by duritz on 2011-02-21
Hello all! This is my first post I am a serious noob. Anyhow, I did several things which I shall list below. One of them has messed up the ability of my lovely Maverick Meerkat to mount external drives. I'm using an eee 901, if that helps. When I connect an external drive, it pops up for a moment in the the file browser, but then disappears. If I go to the /media folder in the browser, I can see the drives listed but all other info is listed as unknown.

So, here is what I did...

It all started with this fix for Skype's constant annoying crashing of my system and I went here, employing the fix at the bottom of the thread in response #60:

[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/646862](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/646862)

Namely, I did this:

cd /usr/lib32
sudo chmod ugo-r libpulse.so.0.12.2
sudo chmod ugo-r libpulse-simple.so.0.0.3

This killed my sound, at which point I asked my friend who is an expert how to fix it (he is currently indisposed). I reset the permissions to 644. He instructed me to do this:

 chmod 644 /usr/lib/libpulsecommon*
 chmod 644 /usr/lib/libpulsecore*
 chmod 644 /usr/lib/libpulse-simple.so.0.0.3
chmod 644 /usr/lib/libpulse.so.0.12.2

This worked in so far as my sound has returned. I still am not sure if Skype will crash again... But my main issue is about the non mounting drives.

I'm not really sure when the trouble with the external drives started, but I first noticed when my mp3 player could not be written to. It told me I didn't have permission. So, of course, like the good amateur that I am, I reset the permission of my ARCHOS mp3 player in the /media folder to 644 as well. This only seemed to make things worse. 

So, externals are not mounting.

Any help would be muuuuuuuuuuch apreciated :popcorn:

Cheers!
Dirk

---

### Post by mikewhatever on 2011-02-21
Hm..., you seem to have followed the fix for the 64bit version of Ubuntu, and I rather doubt the eee901 is 64 bit capable. 
for example, /usr/lib32 doesn't exist on a 32 bit Maverick.
Chmod is a very powerful command, and can be dangerous when misused.
To show exactly what was done, can you post the output of the following:

```
history | tail -n50
```

---

### Post by duritz on 2011-02-21
Hello! Thanks so much. Arrrg, didn't realise the 64 bit thing! I messed with the permissions of the ARCHOS again, as seen below, though I don't think it matters at this point. 

Here is the output:

shambal@shambal-901:~$ history | tail -n50
   33  cd/  TeamSpeak3-Client-linux_x86
   34  cd /TeamSpeak3-Client-linux_x86
   35  cd ~/TeamSpeak3-Client-linux_x86
   36  cd /frupple
   37  cd/ frupple
   38  cd ~/frupple
   39  cd /usr/lib32
   40  ls
   41  cd /usr
   42  cd /lib32
   43  cd /lib
   44  sudo chmod ugo-r libpulse.so.0.12.2
   45  ls
   46  sudo chmod ugo-r libpulse.so.0.12.2
   47  cd /lib32
   48  cd
   49  cd /usr
   50  cd /lib
   51  ls
   52  sudo chmod ugo-r
   53  cd
   54  cd /usr/lib
   55  sudo chmod ugo-r libpulse.so.0.12.2
   56  sudo chmod ugo-r libpulse-simple.so.0.0.3
   57  chmod 644 /usr/lib/libpulsecommon*
   58  sudo chmod 644 /usr/lib/libpulsecommon*
   59* 
   60  chmod 644 /usr/lib/libpulse.so.0.12.2
   61  sudo chmod 644 /usr/lib/libpulse.so.0.12.2
   62  sudo chmod 644 /usr/lib/libpulse-simple.so.0.0.3
   63  ls
   64  cd /media
   65  ls
   66  sudo chmod 644 /media ARCHOS
   67  sudo fdisk
   68  sudo fdisk -l
   69  gnome-open /media/disk/
   70  lsub
   71  gconf-editor
   72  lsusb
   73  sudo chmod 764 /media ARCHOS
   74  dmesg
   75  sudo fdisk -l
   76  sudo mkdir /media/external
   77  sudo mount -t vfat /dev/sdc4 /media/external -o uid=1000,gid=100,utf8,dmask=027,fmask=137
   78  lsusb
   79  sudo fdisk -l
   80  sudo mount -t vfat /dev/sda1 /media/external -o uid=1000,gid=100,utf8,dmask=027,fmask=137
   81  sudo umount /media/external
   82  history | tail -n50

---

### Post by mikewhatever on 2011-02-21
Ok, let's see if any of the libs in /usr/lib are unreadable:

```
ls -l /usr/lib/ | grep -wx
```

... and stop chmod`ing stuff.

...also, what's the output of 'ls -ld /media'?

---

### Post by duritz on 2011-02-21
Good advice. I will stick with that!

shambal@shambal-901:~$ ls -l /usr/lib/ | grep -wx
Usage: grep [OPTION]... PATTERN [FILE]...
Try `grep --help' for more information.

and then

shambal@shambal-901:~$ ls -ld /media
drwxrw-r-- 4 root root 4096 2011-02-22 02:51 /media

---

### Post by duritz on 2011-02-22
Any idea what to do here?

---

### Post by mikewhatever on 2011-02-22
I think you need to change the /media permissions back to the original state. It's not executable for anyone other then root, and that's a problem. 
```
sudo chmod 755 /media
```

---

### Post by duritz on 2011-02-22
Thanks, this worked somewhat and my friend helped me to get a few more things resolved:

77  sudo mount -t vfat /dev/sdc4 /media/external -o uid=1000,gid=100,utf8,dmask=027,fmask=137
   78  lsusb
   79  sudo fdisk -l
   80  sudo mount -t vfat /dev/sda1 /media/external -o uid=1000,gid=100,utf8,dmask=027,fmask=137
   81  sudo umount /media/external
   82  history | tail -n50
   83  ls -l /usr/lib/ | grep -wx
   84  ls -ld /media
   85  sphinx
   86  sphinx2
   87  festival
   88  sphinx2-hmm-6k
   89  sudo chmod -R 777 /media/ARCHOS
   90  sudo chmod 755 /media
   91  sudo chown -R shambal /media/ARCHOS
   92  df -h
   93  so ls -l /media/ARCHOS
   94  sudo alsactl restore
   95  /etc/init.d/pulseaudio force-reload
   96  history | tail -n50

So the externals mount and read and write, but I still cant write to the mp3 player, ARCHOS. It simply says that it is a read only. :(

I don't know if this is related, but now every time I click on a folder from the Places menu, Downloads, for example, Rhythmbox opens! Craziness...

---

