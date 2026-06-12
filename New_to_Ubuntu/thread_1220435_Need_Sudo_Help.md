---
title: "Need Sudo Help"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by fly360 on 2009-07-22
I'm looking for a sudo command to load a Nvidia driver off the cd drive. I installed a nvidia 6200A graphics card to replace the incompatible ATI card in my desktop. I have the driver on a disk that I retrieved off of my laptop. The Graphics shut down to only shell.

---

### Post by Tibuda on 2009-07-22
I think that CD will have the Nvidia driver for Windows, not for Linux.

Open the root shell from the recovery mode, and run this:
```
dpkg-reconfigure xserver-xorg
```

After this is done, restart and open the Ubuntu driver manager in System > Admin, to download the Nvidia drivers for Linux.

---

### Post by Rocket2DMn on 2009-07-22
If you have restricted drivers installed for your ATI card, you should remove those first:
```
sudo apt-get remove --purge xorg-driver-fglrx
```
Then you can start X again:
```
sudo /etc/init.d/gdm start
```
That should bring up the normal login screen.  Once you're logged in, you can enable the Nvidia restricted drivers.

---

### Post by fly360 on 2009-07-22
It is the Linux Driver that I made a CD using My laptop. Im trying to load it on my desktop utilizing Instructions off a previous post. I did not put the driver on my desktop like the individual did in their write-up. The first command that was givin was "cd Desktop".

---

### Post by fly360 on 2009-07-22
> **Rocket2DMn said:**
> If you have restricted drivers installed for your ATI card, you should remove those first:
```
sudo apt-get remove --purge xorg-driver-fglrx
```
Then you can start X again:
```
sudo /etc/init.d/gdm start
```
That should bring up the normal login screen.  Once you're logged in, you can enable the Nvidia restricted drivers.

I did not install any drivers after I had to re-install 9.04 because of the drivers I installed caused it to crash to a multi-colored screen. I left it to what ever 9.04 did normally.

---

### Post by Crunchy the Headcrab on 2009-07-22
Well the easiest way would be to start gdm again.  Then open the file browser and drag the driver from the cd into the desktop folder.  Typing cd Desktop moves you into your desktop folder on your hard drive, which does no good if the driver isn't in there in the first place.

You could also find the mount location of your cd-rom drive and just copy the file or run it from the disc itself, but I'm not sure where cd-rom drives are mounted in Linux so if I was you I'd just use the first method.

---

### Post by Tibuda on 2009-07-22
> **fly360 said:**
> It is the Linux Driver that I made a CD using My laptop. Im trying to load it on my desktop utilizing Instructions off a previous post. I did not put the driver on my desktop like the individual did in their write-up. The first command that was givin was "cd Desktop".

I see. A link to this "previous post" would help. I would say you should replace "cd Desktop" with "cd /media/cdrom".

---

### Post by Crunchy the Headcrab on 2009-07-22
> **danielrmt said:**
> I see. A link to this "previous post" would help. I would say you should replace "cd Desktop" with "cd /media/cdrom".
Ah, so that's where it mounts.  Good to know.

---

### Post by Rocket2DMn on 2009-07-22
Ok, so I assume the directions you are following said to drag the file to your Desktop, then run some command line stuff from there?  If this is the case, put your CD in the drive, then in your terminal run
```
cd /media/cdrom
ls
```
After running the ls command, you should see the files on the CD.  If not, then perhaps the disc didn't automount.  In that case, run
```
sudo mount -t isso9660 /dev/scd0 /media/cdrom
ls
```
You should see the file(s).  To move the file to your desktop, run
```
mv *filename_here* ~/Desktop
cd Desktop
```
You should then be able to follow your directions from there.

---

### Post by fly360 on 2009-07-22
Will try, thanks. I'll be back in a few to let you know how it went.

---

### Post by fly360 on 2009-07-22
I got it. I had to cheat though, I re-installed the ATI card. I then put the Nvidia driver on the desktop, then put in the Nvidia card back in. I will show the link to the article I was following. [http://ubuntuforums.org/showthread.php?t=990978&highlight=nVidia+latest+drivers](http://ubuntuforums.org/showthread.php?t=990978&highlight=nVidia+latest+drivers)

---

