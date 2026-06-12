---
title: "mv:  cannot move `My Book' to `MyBook'"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by waznot on 2009-07-07
Due to corrupted data on a partition on my external hard drive I plan to (hopefully) ddrescue the troubled partition to a new hard drive I bought.

To do this I assume I first have to take the space out of the new hard drives name. 'My Book' to 'MyBook'.

but
```
$ cd /media
$ sudo mv "My Book" MyBook
mv: cannot move `My Book' to `MyBook': Device or resource busy
```The My Book hard drive is mounted and that's all, so I don't know what this 'busy' talk is about.

Is there a way around having to change the name, or, how do I change the name?
Ta

---

### Post by starcraft.man on 2009-07-07
The problem is that you've mounted something to the folder when it's named "My Book" and then you try and change the name while it's still mounted. This isn't going to work. If you want to change the name of the folder, unmount the partition, change the directory name, and then remount it to that directory.

And you can use folder's with spaces in the terminal, it's a bit annoying though. One way is to put quotes around the name (i.e. cd "My Book"). The other way is to use slashes, like "cd My\ Book", take note the slash is opposite the normal direction (i.e. windows way). The slash goes after every word that is followed by the space except the last (i.e. My but not book, if you had 4 words just 3 slashes for first 3).

That should answer your questions, good luck.

---

### Post by waznot on 2009-07-07
Unmounted looks like this?

[U][IMG]http://ubuntuforums.org/attachment.php?attachmentid=120296&stc=1&d=1247018309[/IMG]

[/U]I got this result

```
$ cd /media
$ sudo mv My\Book MyBook
mv: cannot stat `MyBook': No such file or directory
```Am I doing something else wrong?

Thanks for the naming advice starcraft.man.


[IMG]http://ubuntuforums.org/home/warren/Desktop/unmount.png[/IMG]

---

### Post by QIII on 2009-07-07
The backslash is an "escape" character.  You need to still follow it with a space.

The backslash lets the OS know you are not trying to move My into Book, but "My Book" into MyBook.

---

### Post by waznot on 2009-07-07
I tried
```
sudo mv "My Book" MyBook
```and
```
sudo mv My\ Book MyBook
```now with the space, but still got
```
mv: cannot stat `My Book': No such file or directory
```

---

### Post by QIII on 2009-07-07
Type 

dir

in the CLI and post the results.

Edit:  Sorry.  cd to /media first.

---

### Post by sdlynx on 2009-07-07
Your problem isn't solvable by moving the folder, that'll just move your mounted device's files to your Hard Drive at that folder, or have some other undesireable output.

Just right click the External Hard Drive icon from your desktop and select Properties.  From there go to Volume, open the settings thing, and change the mount point to '/media/MyBook/'.  Maybe go to Drive and do that there too.

---

### Post by QIII on 2009-07-07
Dang it, sdlynx, I was just composing a similar message.  Took me a minute to look back up and see that he was looking at a USB device.

---

### Post by sdlynx on 2009-07-07
> **QIII said:**
> Dang it, sdlynx, I was just composing a similar message.  Took me a minute to look back up and see that he was looking at a USB device.

lol well they say great minds think alike

---

### Post by QIII on 2009-07-07
My mind is getting a little slow...

What were we talking about again?

---

### Post by sdlynx on 2009-07-07
changing the mount point for his external HDD.

btw you most likely won't have to change the name if you want to run ddrescue (we seem to have all overlooked that...)

---

### Post by aysiu on 2009-07-07
1. There's no reason to change the name. If you're worried about the space, just use the escape (backslash) character: ```
/media/My\ Book
```

2. dd_rescue generally works off unmounted drives anyway, so it'd probably be something like ```
sudo umount /media/My\ Book
sudo dd_rescue /dev/sdb /media/otherdrive/mybookbackup.img
```

3. If you really do want to rename your My Book, you can install GParted and go to System > Administration > GParted and change the partition label and then click Apply.

---

### Post by waznot on 2009-07-07
Thanx guys i did this
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=120303&stc=1&d=1247022555[/IMG]

and it worked, though it still shows "My Book" on the desktop at this stage - but no matter. I tried to put a "/" at the end but it came up as "_". 

I didn't understand
 > Maybe go to Drive and do that there too.re
> you most likely won't have to change the name if you want to run ddrescueI wanted to change the name to make copy and paste easier for me. I make fewer mistakes the less typing I have to do. :???:

So thanx heaps, I'm now  a happy and more knowledgeable chap.

aysiu, I'll do the ddrescue tonight (my time).  ddrescue is different to dd_rescue isn't it?

---

### Post by aysiu on 2009-07-07
If you find yourself making typing mistakes, you can use tab autocompletion.

For example, if you start typing */media/My* and then hit the **Tab** key, then the terminal should fill in */media/My\ Book* for you, unless there is some other mounted media also called *My*-something-else.

And the naming is a bit confusing with ddrescue. The software package is called *ddrescue*, but the command to use it once installed is *dd_rescue*.

More details at the bottom of this page:
[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

By the way, you may want to check out *gddrescue*. Apparently, it's better than *ddrescue*:
[http://www.atlas-tuesday.com/using-gddrescue-to-save-your-data-part-1](http://www.atlas-tuesday.com/using-gddrescue-to-save-your-data-part-1)

---

### Post by waznot on 2009-07-08
I may not have understood but I don't think I can use gddrescue because I'm using a fat drive.
 
Me and the tab key a going to become very good friends :)

---

