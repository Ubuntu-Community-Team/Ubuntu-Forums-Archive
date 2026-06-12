---
title: "AutoFsck for disk check at shut-down?"
date: 2011-08-05
forum: New to Ubuntu
---

### Post by 2CV67 on 2011-08-05
Hi!

Being frequently irritated by Ubuntu checking disks at start-up (but not wanting to eliminate the checks) I browsed a bit & found I could set different intervals using tune2fs.

I also noticed that there is an application called AutoFsck which apparently runs the checks at a less irritating moment - on shut-down instead of at start-up.
[https://wiki.ubuntu.com/AutoFsck](https://wiki.ubuntu.com/AutoFsck)

Surprisingly, AutoFsck doesn't seem to be available via SynApt or Ubuntu Software Center.

Is there any reason not to use AutoFsck?
Any reason it is not in SynApt?

Any other GUI method for tuning disk check frequency or timing?

Thanks for all tips!

---

### Post by Beacon11 on 2011-08-05
> Any other GUI method for tuning disk check frequency or timing?

It's easy to create a script to run on shutdown, but I don't know of any GUI ways to do it. Let me know if you're okay with the terminal.

---

### Post by sikander3786 on 2011-08-05
Not sure about AutoFSCK but you can change some fsck options by using tune2fs as described here.

[http://ubuntu4beginners.blogspot.com/2011/02/tune-filesystem-check-fsck-on-ext.html](http://ubuntu4beginners.blogspot.com/2011/02/tune-filesystem-check-fsck-on-ext.html)

---

### Post by oldos2er on 2011-08-05
I've used autofsck for a long time; it's safe.

---

### Post by 2CV67 on 2011-08-05
Thanks for your offers Beacon11 & sikander3786 but (see my GUI Fan Club signature) I avoid terminal whenever I can!

I just installed AutoFsck (having to use terminal to do that!!) & will see how it goes.

At least nobody came back with any horror stories yet...

---

### Post by Beacon11 on 2011-08-06
> **2CV67 said:**
> Thanks for your offers Beacon11 & sikander3786 but (see my GUI Fan Club signature) I avoid terminal whenever I can!

Yep, that's why I asked. So sad! (kidding). Glad you're set.

---

### Post by 2CV67 on 2011-08-18
Well - big disappointment!

AutoFsck is now installed & appears in System/Administration as "Periodic Disk Checking" but it is not working at all.

Since installing, I have had 3 cycles of Disk Checking on Start-up & none at Shut-down.
I have tried the option of "Check on Reboot - Recommended" & also "Check on Shut-down" but neither has any effact.
In addition I tried "Check Now" - nothing happened on Shut-down, but all disks were checked on next boot!

Is AutoFsck supposed to work with 11.04?
The Wiki still mentions 8.04...

---

### Post by oldos2er on 2011-08-18
You could try contacting the developers. [http://sourceforge.net/project/memberlist.php?group_id=216366](http://sourceforge.net/project/memberlist.php?group_id=216366)

---

### Post by 2CV67 on 2011-08-18
Yes, thanks for the suggestion.

Just after my previous post, I noticed that the Wiki invites anybody with problems to contact Jonathan Muster, so I did that, mentioning this thread.

Now waiting & hoping...

---

### Post by 2CV67 on 2011-08-19
Jonathan Musther kindly replied to tell me AutoFsck is no longer maintained, so I will give up on that approach.

He says he will put a warning on the Wiki page.

Minor problem now is I can't uninstall it as it does not show in SynApt nor in Ubuntu Software Center...

---

### Post by oldos2er on 2011-08-19
That's a shame it's no longer supported.

To remove it try ```
sudo dpkg -r autofsck
```

---

### Post by 2CV67 on 2011-08-24
Thanks for the offer!

Terminal, like SynApt, thinks it does not exist, though it still figures in the Admin menu & still opens a Config box...

[IMG]http://i838.photobucket.com/albums/zz309/2CV67/terminal.jpg[/IMG]

[IMG]http://i838.photobucket.com/albums/zz309/2CV67/menu.jpg[/IMG]

[IMG]http://i838.photobucket.com/albums/zz309/2CV67/config.jpg[/IMG]

---

