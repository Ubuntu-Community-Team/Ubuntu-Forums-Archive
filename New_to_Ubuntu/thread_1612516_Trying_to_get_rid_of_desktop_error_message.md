---
title: "Trying to get rid of desktop error message"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by 10.04newbie on 2010-11-03
This is a minor problem which has been bugging me and I can't seem to find a way of solving it.

A short while ago, I copied a windows partition folder to my ubuntu  10.04 desktop, then decided that i did not after all need it and deleted it. However, every time that I now boot to Ubuntu, an error message appears on my desktop, saying that the folder in question cannot be found. I have tried carrying out a search with Grep, using the string name of the folder but no result is returned.

Can anyone suggest a solution, please ?

---

### Post by Peter09 on 2010-11-03
Might be worth looking in Syslog to see if there is a more informative error message there.

---

### Post by 10.04newbie on 2010-11-03
Thanks Peter - I had already tried System log viewer as my first option but no joy.

---

### Post by Peter09 on 2010-11-03
Try
 
```
sudo mount -a
```
 
this just remounts all your defined 'mount points' see if you get an error from that. (Shooting in the dark here)

---

### Post by BugBuster on 2010-11-03
Could you post the error message here? ...I know sometimes it just zips through it, but try to get as much as you can and post it here. That will help better.

Also after ubuntu starts, press Ctrl+Alt+F1. This will give black terminal without a gui, and see if you can locate the error there. Sometimes the virtual terminal has a screenfull of messages that we see during boot.

And just in case, go get back to the ubuntu gui, press Ctrl+Alt+F7

---

### Post by Boondoklife on 2010-11-03
You might also check your startup items, maybe you added one that ran something from there.

---

### Post by Gremlinzzz on 2010-11-03
> **10.04newbie said:**
> This is a minor problem which has been bugging me and I can't seem to find a way of solving it.

A short while ago, I copied a windows partition folder to my ubuntu  10.04 desktop, then decided that i did not after all need it and deleted it. However, every time that I now boot to Ubuntu, an error message appears on my desktop, saying that the folder in question cannot be found. I have tried carrying out a search with Grep, using the string name of the folder but no result is returned.

Can anyone suggest a solution, please ?

you know hidden folders and at the bottom there's like files with no folders.read em see if your problem folder is on a list.edit it if its there

---

### Post by 10.04newbie on 2010-11-03
The system boots normally, showing the desktop and its contents but also includes a white rectangular message box, having a red circle with a white line across the middle and the following words :-

'Could not find "/media/windows/datafiles "
Please check spelling and try again'

The suggestion of "sudo mount -a " yields no result
There is nothing in startup manager which points to this problem
Ctrl+alt+f1 does not produce any dialogue other than a login prompt

????

---

### Post by CharlesA on 2010-11-03
Sounds like you mounted the windows drive to /media/windows

Is it still mounted?

---

### Post by 10.04newbie on 2010-11-03
No - the windows partition is not mounted. I can mount/unmount it though.

---

### Post by CharlesA on 2010-11-03
Something is pointing to /media/windows/datafiles, and if it's not mounted, it won't find it.

---

### Post by 10.04newbie on 2010-11-03
Yes, Charles   and that is precisely what I am trying to trace but unless I am doing something wrong, grep does not find the search string "datafiles"

---

### Post by CharlesA on 2010-11-03
Is there a launcher on the desktop or places menu that is pointing there?

---

### Post by Peter09 on 2010-11-03
Try opening Nautilus and see if you have a shortcut or bookmark defined there in the left hand panel.

---

### Post by 10.04newbie on 2010-11-03
No, no launcher was created nor shortcut. I origially COPIED the folder to the desktop from the windows partition and subsequently deleted same.

---

### Post by mgmiller on 2010-11-03
With your desktop showing, hit Ctrl-h to show any hidden folders or files that may be there.   Assuming nothing and assuming you do not want to mount this folder, and it's not in fstab, etc.  First, unmount the windows directory as you said you can do, then take a look in your /media folder to see if it's mentioned there.  If it is, in order to get access to delete it, open a terminal and type ```
gksu nautilus
``` give it your password when prompted and then browse to the media folder and delete what you don't want.  **BE Very Careful.**  You are running nautilus with root permissions and you can severely bork your system if you delete or modify the wrong things.  When you are done, exit nautilus and close the terminal.  You don't wnat to leave a root file browser open any longer then is absolutely necessary.

I also realize this can be done entirely from the command line, but without knowing exactly whats in his /media directory, I can't give him the correct syntax.  At least in the GUI he can look around easily and delete what he needs to.

---

### Post by mgmiller on 2010-11-03
Deleted a double post.

---

### Post by 10.04newbie on 2010-11-04
Thanks MGM. However, I had already previously set my folder preferences to show all hidden folders/files and nothing  pointing to this problem was showing.

As suggested, I opened the /media folder but all that was showing, were the usual ie floppy, cdrom, windows partitions and the file .created_by_python-fstab, the latter confirming the windows partitions.

I would have thought that a string search, using grep across the whole of the file system, should have identified a file containing the word 'datafiles' but perhaps I did not use the correct command ( I used grep -lrh 'datafiles')

---

### Post by mgmiller on 2010-11-04
Take a look at what is attempting to mount from /media/windows.  If it mentions /datafiles try removing that.  Similarly, look in the file .created_by_python-fstab and see if it mentions /windows/datafiles and edit accordingly.

Beyond that, I'm kind of stuck.  I don't think I have ever seen a hidden file in /media.

---

### Post by 10.04newbie on 2010-11-04
As I said, no mention in any of those files of the folder (datafiles).

Guess I'll have to live with the error message.

Thanks, all, for trying.

---

### Post by Peter09 on 2010-11-04
One of the things you could try is deleting or renaming the .gconf directory in your home folder. This holds  your gnome configuration data. If you log out and back in again gnome will recreate it with defaults. It could be that the desktop settings(including mounted directories) are logged in there.

---

### Post by 10.04newbie on 2010-11-05
Thanks Peter but all that this did was to remove items that were on my desktop and the error message was still there. Fortunately, I had renamed the original .gconf folder and was able to recover my desktop items by reinstating the original.

If only I could carry out a proper search across the whole of the file system, to locate what is generating the error message. Grep doesn't do it for me, for some reason

---

