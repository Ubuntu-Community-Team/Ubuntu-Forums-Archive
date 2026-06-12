---
title: "computer not reading cd or dvd"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by okkie on 2011-06-10
I assume it is after my last update of 10.10.My computer doesn't read any cd I put into the disk drives.I cannot access any information on cd's I put into my disk drives.
Any help will be appreciated.

---

### Post by jtarin on 2011-06-10
Post the output of the command in the terminal of ```
eject -n
```

---

### Post by okkie on 2011-06-10
output as requested thanks eject: device is `/dev/sr0'

---

### Post by jtarin on 2011-06-10
Ok that shows that Ubuntu can see your CD drive.
Does it appear under Places in the menu and in /media in the file manager?
Do you get any error messages at all?

---

### Post by SoFl W on 2011-06-10
I was having strange problems with my DVD/CD also but in 10.4.
With no CD in the drive, go to the terminal and see what is the "/media" directory.

---

### Post by okkie on 2011-06-10
I now lost all three my menus.Places, applications etc

---

### Post by Sidewinder1 on 2011-06-10
Okkie, are you sure you didn't *upgrade* to 11.04? If so, perhaps you're now using Unity, which I don't use; but have heard that "Places", "Applications", etc. disappear. If so, you can boot into Gnome by clicking on your username, at boot, then click "Classic", at least that should get your panels back.
Side

---

### Post by jtarin on 2011-06-10
[http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

---

### Post by okkie on 2011-06-10
Sorry I have got the menus back.I notice if I go to places computer the dvd drive is not detected and in the process to find out what is wrong I now have the normal cd drive open but it still cannot read a cd

---

### Post by jtarin on 2011-06-10
Try the following two commands then check to see if it mounts.

```
sudo mkdir /mnt/cddrive

sudo mount -t iso9660 /dev/cdrom /mnt/cddrive
```This is a temporary workaround to see if we can actually mount it.

Or, if your CD is formatted in UDF:

```
sudo mount -t udf /dev/cdrom /mnt/cddrive
```

---

### Post by SoFl W on 2011-06-10
> **okkie said:**
> Sorry I have got the menus back.I notice if I go to places computer the dvd drive is not detected and in the process to find out what is wrong I now have the normal cd drive open but it still cannot read a cd

Did you try going to the "/media" folder to see if the system already thought something was in there?

---

### Post by okkie on 2011-06-12
tHANKS FOR ALL YOUR TROUBLE.I decided to clean my computer with my airgun,checked all the fittings etc and my problem solved.Amazing what dust over time can do although it appears clean and unsusspicious.This might be a lesson of some sort for the interested.

SOLVED

---

### Post by jtarin on 2011-06-12
That's good...I was gonna suggest a shotgun.:p

---

