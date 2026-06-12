---
title: "VBoxadditions cant run it"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by zarktehzark on 2011-02-15
Hi there, 

this is driving me absolutely mad. 
I have installed on vm VirtualBox Ubuntu server 10.10 hosted on Vista 64
I am attempting to run VBox guest additions and it just wont find the file

heres where i am 

cd /media/cdrom/

i have mounted guest additions in the cdrom ide 2ndary master

i type 'sudo sh VBoxLinuxAdditions-x86.run' and it tells me

sh cant open VBoxLinuxAdditions-x86.run

I have read a few articles and to be honest none of them helped. I just dont get it. The file is located in oracle folder but named VBoxGuestAdditions.iso but i am typing VBoxLinuxAdditions-x86.run .. is this right? 
am i in the wrong cdrom ? 

before i delete the entire thing and lose entire faith can anyone give me a pointer?

thanks

---

### Post by howefield on 2011-02-15
Are you sure about the file name ?

Could it be VBoxLinuxAdditions.run

---

### Post by zarktehzark on 2011-02-15
unfortunately it again says 'cant open'

---

### Post by howefield on 2011-02-15
Try...

```
sudo ./VBoxLinuxAdditions-x86.run
```

Assuming that's the name of the file.

---

### Post by zarktehzark on 2011-02-15
cant open.

the only file i have on disk is called VBoxGuestAdditions.iso

and using that name with .iso doesnt work and neither does .run

i think i should just go back to something easy and logical

---

### Post by csacpt on 2011-02-15
I am running Vbox 4 and if you start your guest VM (XP in my case) there is a dropdown menu under Devices that has Install Guest Additions. That is how I did it with Maverick as the host anyway. Hope this helps.

---

### Post by zarktehzark on 2011-02-15
best clarify Ubuntu 10.10 server edition i386. is this the problem?

---

### Post by zarktehzark on 2011-02-15
> **csacpt said:**
> dropdown menu under Devices that has Install Guest Additions.

i got v4 and under devices i can click install but all that happens is the disc at bottom shows it is mounted but nothing else. Next to the Install Guest Additions it reads 'HOST +D'.

Whats all that about?

---

### Post by csacpt on 2011-02-15
> **zarktehzark said:**
> i got v4 and under devices i can click install but all that happens is the disc at bottom shows it is mounted but nothing else. Next to the Install Guest Additions it reads 'HOST +D'.

Whats all that about?

Just a suggestion since I have very little experience, but try this  forum, they might be able to help. They helped me with some of my  problems anyway. I have not tried to run a Ubuntu VM yet myself. Sorry.
 
 [http://forums.virtualbox.org/](http://forums.virtualbox.org/)

---

### Post by howefield on 2011-02-15
To go back to your first post, when you do

```
cd /media/cdrom/
```

what does the command ls return ?

---

### Post by zarktehzark on 2011-02-16
ah-ha it does nothing. Nothing returned

---

### Post by Joeb454 on 2011-02-16
Have you mounted the .iso image?

If you do, it should appear in the places menu, otherwise it would just be a file on the desktop (or wherever it's saved)

---

### Post by zarktehzark on 2011-02-16
i believe so, if i click devices and highlight cdrom the slide out menu shows additions.iso with a tick next to it and the small disc at bottom next to the harddrive indicator is solid with additions path to c:/ ... oracle/ folder

---

### Post by howefield on 2011-02-16
> **zarktehzark said:**
> ah-ha it does nothing. Nothing returned

You either haven't mounted the iso which seems unlikely or are running the command from the "wrong" place.

Navigate to the mounted iso until an ls shows the list of files in it (something like the list of files in the attached screenshot - don't be put off by the path in my example). Then you can run the command, for me it would be

```
sudo ./VBoxLinuxAdditions.run
```

---

### Post by zarktehzark on 2011-02-16
okey dokey will give it a go. Thanks for pointer

---

### Post by zarktehzark on 2011-02-24
to be honest, i uninstalled all of it. What a waste of time. 
1st experience = horrendous. If constant troubleshooting is required for this, i thought forget it. I didnt install it to be losing hours of my life trying to mount an image for gods sake.
thanks for help though

---

### Post by migs73 on 2011-02-24
I wouldn't give up yet, it usually is easy, honest!

I had a similar problem (toward the end of this thread; [http://ubuntuforums.org/showthread.php?t=1593674](http://ubuntuforums.org/showthread.php?t=1593674)) and it was solved by downloading the Guest additions again, either it was an old version or a bad download.

---

