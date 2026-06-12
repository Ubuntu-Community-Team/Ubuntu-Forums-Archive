---
title: "Can't delete desktop icon"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by purvis on 2010-02-04
I placed an icon on my desktop to link directly to an HD on another  computer I am networked with. This worked fine until I rebooted and then  the icon would not connect to the HD. I receive an error message that  reads:
"Could not display  'x-nautilus-desktop:///networ...ge%20on%20server.volume'. The file is of  an unknown type".
I was (and still am) fine with this and was simply going to delete the  icon and go to the HD using "network" in the menu as I had found it  before. My big problem is that I can not delete the icon now, when I  attempt to I receive an error message that reads:
"Error while deleting. There was an error getting information about  "network storage on server.volume". The specified location is not  supported [cancel] [skip all] [skip] [retry]"
How can I delete this icon form my desktop?

---

### Post by warfacegod on 2010-02-04
Try going to the actual desktop folder and deleting it from there. You may need root privileges:

```
gksudo nautilus
```

---

### Post by purvis on 2010-02-04
There is nothing that shows up in the desktop directory when I do that.

---

### Post by warfacegod on 2010-02-04
Show hiddn files = Ctrl+H

---

### Post by purvis on 2010-02-04
Still nothing displayed in the file browser but I did notice an error message this time. I tried it again and got a different error message, both of which I have listed below. 
Here is the first error message:

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


--- Hash table keys for warning below:
--> inode/directory
--> l2053
--> root

(nautilus:3824): Eel-WARNING **: "unique eel_ref_str" hash table still has 3 elements at quit time (keys above)

(nautilus:3824): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time


Here is what I got when I ran it the second time:

** (nautilus:3849): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:3849): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:3849): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

---

### Post by warfacegod on 2010-02-05
I'm not sure what the top warning means but the bottom one is fairly common. I get it myself when opening nautilus as root. It doesn't seem to hinder anything so I haven't bothered to look into it.

---

### Post by drzoo2 on 2010-02-05
When you do a gksudo nautilus it will open roots home folder. You will have to navigate to yours.

/home/yourhomedirectory/Desktop

One other thing. Open a terminal and type the following...

```

cd ~/Desktop
ls -la

```

List the output

---

### Post by warfacegod on 2010-02-05
> **drzoo2 said:**
> When you do a gksudo nautilus it will open roots home folder. You will have to navigate to yours.

/home/yourhomedirectory/Desktop

Yup, I'm a dope, should've mentioned that.

---

### Post by drzoo2 on 2010-02-05
> **warfacegod said:**
> Yup, I'm a dope, should've mentioned that.

We all have our moments :)

---

### Post by purvis on 2010-02-05
I had been going to the desktop in the file browser so that was not it. Here are the results:
james@backroomdell:~$ cd ~/Desktop
james@backroomdell:~/Desktop$ ls -la
total 20
drwxr-xr-x  3 james james 4096 2010-02-03 21:27 .
drwxr-xr-x 76 james james 4096 2010-02-04 16:56 ..
-rwxr-xr-x  1 james james 2665 2010-02-03 21:27 firefox.desktop
drwxr-xr-x  2 james james 4096 2010-02-03 21:14 Toddler Games
-rwxr-xr-x  1 james james  198 2010-02-03 09:14 tuxmath.desktop

---

### Post by purvis on 2010-02-05
Wondering if someone could take another look at this? Having an unusable icon on the desktop is frustrating.

---

### Post by Leppie on 2010-02-05
can you modify the launcher or check the properties (right click on it)?

---

### Post by audiomick on 2010-02-05
Hi.
The only thing that occurs to me is to try and trick it out. Can you maybe open the icon's properties and point it to something on the computer that it can find?
It sounds like the stumbling block is that the icon can't find what it is looking for.

It surprises me a little that it is not visible in the desktop folder. I just tried creating an icon to test with, and it showed up there.

---

### Post by warfacegod on 2010-02-05
> **audiomick said:**
> Hi.
The only thing that occurs to me is to try and trick it out. Can you maybe open the icon's properties and point it to something on the computer that it can find?
It sounds like the stumbling block is that the icon can't find what it is looking for.

It surprises me a little that it is not visible in the desktop folder. I just tried creating an icon to test with, and it showed up there.

That's what I thought too. I just figured there was some setting I wasn't remembering. Like in Ubuntu Tweak: always show "Network" or "Hard Drives"

---

### Post by Leppie on 2010-02-05
i think the icon may actually be in the gnome configuration folder (.gconf)

---

### Post by rajiii2002 on 2011-04-27
I am fairly new to Ubuntu/Linux, but I am a very advanced Windows tech that was looking to expand my horizons. I registered just to see if anyone has figured out a solution to this Network Icon problem. I also am having the same problem, and I have tried all of the things posted on this forum.

Message when Icon is clicked:
Could not display "x-nautilus-desktop:///v3xx%20original%20on%20server.volume".
The file is of an unknown type

Message when trying to delete:
Error while deleting.
There was an error getting information about "v3xx original on server.volume".
Show more details
The specified location is not supported
Cancel, Skip All, Skip, Retry

The Icon originally came from a Windows Ultimate Shared Network Folder. It does not matter if the folder is still shared or not, I get the same error messages.

Thanks for your future help.

---

### Post by CoffeeRain on 2011-04-27
Haha, it's funny that I have the same problem too. Somehow the hard drive icon is showing up on my desktop, and I can not see it in Terminal or anything else. :(

---

### Post by Leppie on 2011-04-28
how did you guys create the desktop icon?

---

### Post by zensawa on 2012-02-17
Sry for bumping such and old thread. I have just had a similar problem with my Ubuntu machine. I was able to fix the issue by renaming the file via context menu(right click), rename. I then renamed the file to something very short like 2 digits long. Then I went to the command, navigated to the file, then typed :

[CENTER][LEFT]```


sudo rm -r (filename)

```
Hope this helps others ;)[/LEFT]
 [/CENTER]

---

