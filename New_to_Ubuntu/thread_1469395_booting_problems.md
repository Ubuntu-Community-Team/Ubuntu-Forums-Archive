---
title: "booting problems"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by cameronedwards on 2010-05-02
OK, so this is the deal. i dropped my laptop, and now it will only boot into a text-based system type thing. saying something like the filesystem failed to mountall, loading restore shell, click control-D to retry  or something. it sends me to a root account in a black terminal. If i type "mountall" the computer seems to start OK again with the circular ubuntu 9.10 symbol. but then under the logo / symbol is a error message saying: 
/etc/fstab cannot yet be mounted
/: waiting for /dev/disk/by-uuid/8aeb62b2-bfb6-4658-ac09-da9e7d21087
/tmp: waiting for (null)
press ESC to enter recovery shell
i can access my harddrive and all of my documents/ programs through booting into a usb drive with ubuntu on it.
Hope this works.

---

### Post by GSF1200S on 2010-05-02
> **cameronedwards said:**
> OK, so this is the deal. i dropped my laptop, and now it will only boot into a text-based system type thing. saying something like the filesystem failed to mountall, loading restore shell, click control-D to retry  or something. it sends me to a root account in a black terminal. If i type "mountall" the computer seems to start OK again with the circular ubuntu 9.10 symbol. but then under the logo / symbol is a error message saying: 
/etc/fstab cannot yet be mounted
/: waiting for /dev/disk/by-uuid/8aeb62b2-bfb6-4658-ac09-da9e7d21087
/tmp: waiting for (null)
press ESC to enter recovery shell
i can access my harddrive and all of my documents/ programs through booting into a usb drive with ubuntu on it.
Hope this works.
Well, considering you dropped it and now have filesystem errors, you know you have a bad hard drive. I would highly recommend running that USB ubuntu drive and an external hard drive and backing up your data. If that data is important, you want it on a good drive as soon as possible. If you dont have an external, you could do an ssh transfer of all your files to a computer on a local network (assuming its a linux box, use ftp otherwise). I would then go buy a new drive. Im sure you already know this, but I post to make sure you know that its not likely anyone will recommend you try to fix software wise what is caused by hardware.

---

### Post by cameronedwards on 2010-05-02
> **GSF1200S said:**
> you have a bad hard drive.

I don't think i mentioned this but this has happened before and i was able to get my harddrive running fully again by installing ubuntu as a side by side installation. This gave me back all of my files and fixed the old filesystem, so i could load into both. Because my cd-drive broke when i dropped my laptop, i cannot reinstall again. is there some way to create a ubuntu usb installer?

---

### Post by GSF1200S on 2010-05-02
> **cameronedwards said:**
> I don't think i mentioned this but this has happened before and i was able to get my harddrive running fully again by installing ubuntu as a side by side installation. This gave me back all of my files and fixed the old filesystem, so i could load into both. Because my cd-drive broke when i dropped my laptop, i cannot reinstall again. is there some way to create a ubuntu usb installer?

Im glad it worked for you once, and I hope it works for you again, but I strongly suggest you at least back the data up somewhere in case the drive decides it has had enough.

Yes, it is possible- take a look here:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by cameronedwards on 2010-05-02
Ok thanks i'll try that, backing up now!

---

