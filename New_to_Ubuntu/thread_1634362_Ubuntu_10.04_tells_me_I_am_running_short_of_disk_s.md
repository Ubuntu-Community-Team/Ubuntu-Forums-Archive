---
title: "Ubuntu 10.04 tells me I am running short of disk space"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by 10.04newbie on 2010-11-30
The system keeps reporting that I have only 500MB(approx) disk space left, yet when I check the properties of all of the directories in terms of disk space used, the total comes out at 10GB approx , wheras gparted tells me I have used 25GB. How can this possibly be ??

---

### Post by cariboo on 2010-11-30
Could you open an Applications->Accessories->Terminal and type:

```
df -h
```

and paste the output in you next post?

---

### Post by 10.04newbie on 2010-11-30
Here is the output :-

.Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              27G   25G  520M  98% /
none                  371M  348K  371M   1% /dev
none                  375M  300K  375M   1% /dev/shm
none                  375M  328K  375M   1% /var/run
none                  375M     0  375M   0% /var/lock
none                  375M     0  375M   0% /lib/init/rw

---

### Post by ppv on 2010-11-30
It has been used to 25GB...

---

### Post by 10.04newbie on 2010-11-30
[QUOTE][It has been used to 25GB/QUOTE]

I know that's what the system is telling me but it is not borne out by the usage indicated when I check the size of each individual folder in the file system !

---

### Post by akand074 on 2010-11-30
> **10.04newbie said:**
> [QUOTE][It has been used to 25GB/QUOTE]

I know that's what the system is telling me but it is not borne out by the usage indicated when I check the size of each individual folder in the file system !

The usage indicated when you check the size of each individual folder doesn't include hidden folders. Some applications store a lot of data in hidden folders.

---

### Post by lobralleo on 2010-11-30
You could start by cleaning the apt cache; from the terminal, just type:

```
sudo apt-get clean
```

This should make some space available - potentially up to a few GB, depending on how many updates your system has been through.

---

### Post by 10.04newbie on 2010-12-01
[B]Akand074-My preferences are set to show all hidden files.
[/B]

---

### Post by 10.04newbie on 2010-12-01
Apart from the drive activity light flashing for about 15 minutes, sudo apt-get clean did not achieve anything. Usage still showing as 25gb

Apart from the recommended system updates, the only other large package I have installed is Kaffeine. I have not created any data in my home folder .What would you assume the disk usage should be ?

---

### Post by baddnady23 on 2010-12-01
Please try the ```
sudo apt-get clean
```command and repost the output of ```
df -h
```

---

### Post by Zimmer on 2010-12-01
Thumbnails??? do you do a lot of picture processing?
Install Geequi and go edit>preferences>thumbnail maintenance to delete old thumbnails..

Use the disk useage analyzer to check the /home folder

---

### Post by coffeecat on 2010-12-01
> **10.04newbie said:**
> I know that's what the system is telling me but it is not borne out by the usage indicated when I check the size of each individual folder in the file system !

Which individual folders have you checked? Did you check the /root folder? A fairly common cause for this situation is if you have ever deleted files with a root nautilus. They will still be sitting there in root's trash.

---

### Post by 10.04newbie on 2010-12-01
Have already done this, **baddnady23** (see above) and the output of df -h is the same as before.

All folders were checked (root folder has 5gb) and I had already taken this into account.

I don't do picture processing so no problem with thumbnails.

---

### Post by philinux on 2010-12-01
> **10.04newbie said:**
> Have already done this, **baddnady23** (see above) and the output of df -h is the same as before.

All folders were checked (root folder has 5gb) and I had already taken this into account.

I don't do picture processing so no problem with thumbnails.

Check this out. My / partition only has used about 4 gig. It could be backup files or root trash.

[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

Or you've some large files in your home folder.

---

### Post by 10.04newbie on 2010-12-01
Thanks **Coffeecat** - You've hit the nail on the head. My root folder has a cross on it, so I used Nautilus to open it and, sure enough, the trash folder contained over 17GB, which I have now deleted.

---

### Post by akand074 on 2010-12-01
> **10.04newbie said:**
> [B]Akand074-My preferences are set to show all hidden files.
[/B]

Even so. I found out the other day when I had 15GB space left in my 1TB hard drive. I checked all my folders and particularly one folder I have a hidden folder with 175GB of stuff. When I checked properties of the folder that contained that 175GB folder it didn't come up. Only hidden folders that are actually selected are included. So if you have it "show hidden folders" then check the properties of /home, it won't count your hidden files within /home, but if you wen to /home/username/ and highlight everything including hidden files it will count them (but none in the subfolders if you have any hidden there).

Unless you already did that. Well then not sure. Has to be something. Your filesystem (the OS and applications) should really not be more than like 7-9GB. Is your entire hard drive 25G? My 1TB hard drive only has 918GB usable after formatting it. so if you have a 25GB hard drive you'll only have about 21GB usable I'd say.

---

