---
title: "Not authorized to mount external hard drive?"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by Alex De Duck on 2009-11-30
I'm using an external hard drive to switch files in between Ubuntu and vista. This device is a Maxtor One Touch, is not password protected and is always connected to the computer. 

Now today, when I started up, I noticed it told me that the hard drive could not be mounted, that it wasn't authorized too.

Now I'm wondering how this happened.

---

### Post by Alex De Duck on 2009-11-30
Bringing this back up.

---

### Post by newbuntuxx on 2009-11-30
Can you post the exact error message please.

Sometimes, you need to force mount a drive to work. Or you might need to use the ntf configuration tool.

---

### Post by Alex De Duck on 2009-11-30
There's no error code or anything. Just: 

"Unable to mount "name of drive" in the header bar, 
and then "Not authorized".

---

### Post by Geoff918 on 2009-11-30
What is the file system? You may need to do something of the sort:

sudo mount -t ntfs-3g /dev/sd?? /media/(something you make up, and have already created)

You may find the following information useful:

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

---

### Post by teward on 2009-11-30
Betcha someone who's the admin on your computer said "No, i'm not giving them the rights to access external media."

Saw this on a friends comp.

---

### Post by mkvnmtr on 2009-11-30
I had problems like this on 7.04 through 8.10. Sometimes it would mount and sometimes not. Since 9.04 I have4nt had to mount anything myself. Are you using an older release? If so you will need to creat a mount point and mount it each time you wish to use it. It really was a pain when I had that problem and nobody in the forums could tell me to get it back to normal. Just how to mount it in terminal.

---

### Post by Alex De Duck on 2009-12-01
@Geoff: Will check that out, thanks! 
 
@TrekCaptain: Fat chance, I'm the only one on my laptop.
 
@mkv: It confuses me cause it worked perfect on jaunty jackalope, but now on karmic koala it's being a bitch.

---

### Post by disabled_20220313 on 2009-12-30
Hi,

There has been a workaround posted to the Launchpad bug.

You need to create a file called /etc/gdm/custom.conf

This can be copied from a working system, or I have put a copy of mine on paste bin, [http://pastebin.com/f21a2a657](http://pastebin.com/f21a2a657)

To create the file open gedit using gksudo:
```

gksudo gedit /etc/gdm/custom.conf

```

That should fix your problem.

Good luck,

Ciarán

---

### Post by KoenW on 2010-01-02
For me it seems to be a nautilus-bug. When I install thunar I do not have these problems with permissions anymore (for me it is a USB attached digital camera). 

sudo apt-get install thunar
thunar


Koen

---

### Post by Buuntu on 2010-01-02
Go to System > Administration > Users and Groups.  
Click on properties of your user and go to the "User Privelages" tab.  Make sure everything you want to be able to do is checked and then exit.

---

### Post by BigBen72 on 2010-01-08
> **KoenW said:**
> For me it seems to be a nautilus-bug. When I install thunar I do not have these problems with permissions anymore (for me it is a USB attached digital camera). 

sudo apt-get install thunar
thunar


Koen


This work around worked for me... (not the other ones)

Benoit

---

### Post by keylog on 2010-01-16
> **Buuntu said:**
> Go to System > Administration > Users and Groups.  
Click on properties of your user and go to the "User Privelages" tab.  Make sure everything you want to be able to do is checked and then exit.

I did it with sudo wrights but when i logout and login again, they seems be unchecked again...

what can i do? :S

---

