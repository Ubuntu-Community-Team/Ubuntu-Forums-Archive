---
title: "Accessing C: drive"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by Alex56 on 2009-02-22
Good evening everyone! I installed Xubuntu this morning with the Wubi-Installer and I love it! And I was told a could access my C:\ on my Windows by going into the "host" folder. But that took me to my D:\ drive, which was the hard drive I installed it on. Is there any way I can access my C:\ in Xubuntu? Thanks!

---

### Post by Alex56 on 2009-02-22
Anyone?

---

### Post by Panzor on 2009-02-22
I've never used Wubi, but I know that if you boot into ubuntu and go to Places>>(the name of the device the c drive is on), it should automount and you have access to your files.

The real way to do it is
```
$sudo fdisk -l
```
Figure out which device your windows partition is (it should be an ntfs or fat32 type, I'd assume). It'll look something like "/dev/sda1" or "/dev/hda1"

Then,
```
$sudo mkdir /mnt/windows
$sudo mount /dev/sda1 /mnt/windows
```
***replace "/dev/sda1" with what you found in the previous step***Then if you look inside /mnt/windows/ you'll see your C: drive. =)

---

### Post by Alex56 on 2009-02-23
Wow! That's the first time I used Terminal and something good happened as a result. :p Thanks for your help!

And just a quick question.... do I have to run that command each time I boot up or will it mount automaticly?

---

### Post by Metallion on 2009-02-23
To mount it automatically type this command:
```
sudo mousepad /etc/fstab
```

Your text editor should pop up showing the fstab file. In this file all of the drives that are mounted on boot are configured. Now add the following lines on the end of this file:
```

#windows C drive
/dev/sda1  /mnt/windows    ntfs    defaults,umask=007,gid=46 0       1
```

Save the file and close the text editor. Now your C drive should be mounted at boot.

---

### Post by Alex56 on 2009-02-23
When I try to save it, I get a message saying: Can't open file to write.
Any ideas?

---

### Post by bodhi.zazen on 2009-02-23
> **Metallion said:**
> To mount it automatically type this command:
```
sudo mousepad /etc/fstab
```Your text editor should pop up showing the fstab file. In this file all of the drives that are mounted on boot are configured. Now add the following lines on the end of this file:
```

#windows C drive
/dev/sda1  /mnt/windows    ntfs    defaults,umask=007,gid=46 0       1
```Save the file and close the text editor. Now your C drive should be mounted at boot.

You should use gksu for graphical applications.

Try gksu mousepad /etc/fstab and or install gedit.

---

### Post by Alex56 on 2009-02-23
I believe that gedit is for GNOME desktops, not Xfce. And even while using gksu, it still gives that error.

---

### Post by bodhi.zazen on 2009-02-24
> **Alex56 said:**
> I believe that gedit is for GNOME desktops, not Xfce. And even while using gksu, it still gives that error.

Yes but ....

Linux is "modular" and Xubuntu already uses a ton of gnome applications.

gedit installs I believe in 2 or 3 packages, so quite small. gedit has a few features lacking in mousepad as well.

You can also install single KDE apps in Gnome or Xubuntu. for example I personally like K3b. Also Virtualbox has a number of KDE dependencies.

Last, if you can not save the changes it sounds as if your permissions are off.

Can you show the output of ```
ls -la /etc | grep fstab
```

Otherwise my guess are you are either putting in the wrong command (which I doubt) or you are not in the admin group ? Just a guess.

---

### Post by Metallion on 2009-02-24
It can't open the file for writing? That's very strange if you used sudo or gksu. It's a bit ugly but you could get around it this way:
```
sudo chmod 666 /etc/fstab
```
Don't worry, this command won't summon the devil. It will just assign both read and write permissions for everyone to fstab. Now you can try the commands from my previous post again.

Leaving the file writable by everyone isn't a good idea so make sure to put the old permissions back when you're done.
```
sudo chmod 644 /etc/fstab
```

---

### Post by redseventyseven on 2009-02-24
> Wow! That's the first time I used Terminal and something good happened as a result.  Thanks for your help!


...and I'm sure it won't be the last. Nice one!

---

### Post by Alex56 on 2009-02-24
Sorry for the long time before a reply. Long day...

Anyway, I switched to the Ubuntu Wubi install just to try to fix this, I did the same thing that I did in the first few posts. Same error. I also tried to change the permissions. I think it worked. Did it again. And yep, you guessed it, same error. I'll run that one command in a second. Again, thanks for your help. :KS

EDIT: Here's the response (if that's the term)...
```
-rw-rw-rw-   1 root root       424 2009-02-24 14:25 fstab
```

And I also thought that I might add that when I opened fstab, it was blank. Is that normal?

---

### Post by bodhi.zazen on 2009-02-24
Well I presume you typed the path wrong ...

```
gksu mousepad /etc/fstab
```

You need to change the permissions of fstab back.

I am sorry, but changing permissions of system files is IMO bad advice and totally unnecessary. It is a bad habit and may cause system breakage.

```
sudo chmod 644 /etc/fstab
```

---

### Post by Alex56 on 2009-02-25
I changed the permissions back.

I got mad at terminal so I went out in search of the actual file. It wasn't that hard to find. I opened it. It wasn't empty like the terminal version. :o So I copied in the code that mounts my C: and rebooted. It worked! :lolflag: Anyway, I have no idea why it wasn't working. But it's working now! Thnaks for your help.

---

