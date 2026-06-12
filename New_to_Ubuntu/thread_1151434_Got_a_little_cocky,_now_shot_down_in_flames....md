---
title: "Got a little cocky, now shot down in flames..."
date: 2009-05-06
forum: New to Ubuntu
---

### Post by Jim Ryans on 2009-05-06
Hello all... I was doin" really good, had the new Ubuntu all installed configured and everything working great, it even detected my laptop's usb wireless adapter, the first distro I've tried that did right off the bat, and I've tried many !!! Well like I said, been using it proudly for all of one day when I got to the point of wanting to install a good mp3 player that would use my favorite skins from Winamp, and I found one, installed it just fine, and got to the part where I needed to copy a skin folder to usr\shared\Audacious\skins but I didn't haver permission to put it there, even though I'm in admin group. Well I jacked around with it, trying to make my userid as powerful as root, so I compared the two and changed mine from like home\jimbo to \root , 
restarted- well that was the last time I saw my new os, now I can't login any more, buncha error messages about security and you can't do this and can't do that, then a featureless orange screen with nothing on it, can't do anything now but rebuild !!! I should have left well enough alone !!! But hey, I sure know a quick way to screw up an ubuntu machine. Just seems ironic that I had enough power to screw up the os, but not enough power to move a dern folder !!! Argh !!!
Thanks for listening, Jimbo...

---

### Post by Dngrsone on 2009-05-06
[IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/rollin.gif[/IMG]

I'm laughing with you, Jimbo.

Ubuntu is designed with root hidden and you cannot normally log in as root.  This is a security measure to keep the newbies from really screwing things up unintentionally.

When yo want to move folders around and such, then go to Applications>Accessories>Terminal.  A command-line interface terminal should pop up.  You then want to enter the following command:

```
sudo nautilus
```

and hit the return (enter) key.  This tells the system to open up a copy of the nautilus browser as root, and you will be able to manipulate the folders and files to your heart's content.  Just be careful what you do.

You will have to enter your password before it will open up the browser, of course.

Any time you use the sudo command, you are telling the system to treat the following command as if you are root.  The terminal will remember that you put your password in for something like five minutes.  After that, you will be prompted for the password again.

---

### Post by Ms_Angel_D on 2009-05-06
umm sorry I can't tell you how to fix the current issue, but just FYI

next time hit alt+f2 and run ```
gksu nautilus
``` this will let you run the file manager as an admin so you can copy your files, but I wouldn't run it all the time, maybe just long enough to copy over some files.

---

### Post by Ms_Angel_D on 2009-05-06
Doh Dngrsone must have been typing the same time as me ;)

---

### Post by thraxsa on 2009-05-06
> **Dngrsone said:**
> [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/rollin.gif[/IMG]

I'm laughing with you, Jimbo.

Ubuntu is designed with root hidden and you cannot normally log in as root.  This is a security measure to keep the newbies from really screwing things up unintentionally.

When yo want to move folders around and such, then go to Applications>Accessories>Terminal.  A command-line interface terminal should pop up.  You then want to enter the following command:

```
sudo nautilus
```

and hit the return (enter) key.  This tells the system to open up a copy of the nautilus browser as root, and you will be able to manipulate the folders and files to your heart's content.  Just be careful what you do.

You will have to enter your password before it will open up the browser, of course.

Any time you use the sudo command, you are telling the system to treat the following command as if you are root.  The terminal will remember that you put your password in for something like five minutes.  After that, you will be prompted for the password again.

sudo -i will give you a root login at a terminal - only recommend using this if you have to be root@.......  99% of the time sudo <command> should be adequate....

---

### Post by starcannon on 2009-05-07
Most of the time you will not need to be root in order to do ordinary tasks; with that in mind, don't try to turn your user account into an all powerful root account, it pretty much nullifies much of your security. As mentioned earlier just run a filebrowser with super user powers as needed, not all the time.
```
gksu nautilus
```
Then move your files where they need to go, then close the su nautilus window.

---

### Post by freeman2000 on 2009-05-07
As they all have said, you must watch how you play with your new toy.  Not lecturing, just laughing along with you (great title).  Since you've only played with it for a day, you don't have much time & effort involved yet, so the easy solution is to just reinstall Ubuntu.  Good luck.

---

