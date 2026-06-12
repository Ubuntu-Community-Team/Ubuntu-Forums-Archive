---
title: "Reinstalling over the same partition?"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by pyrofyr on 2009-01-01
I've had a few errors, which can be seen in [this]("http://ubuntuforums.org/showthread.php?t=1027047") thread.

Because of it, I'm sure that the easiest path would probably be trying to reinstall it, is it possible to reinstall it over the same partition or kind of wipe it back to how it was out of the package?

I pretty much can't do anything because Nautilus won't load up because /Desktop is missing.

---

### Post by kestrel1 on 2009-01-01
Yes, you should be okay to do that. Just make sure that the drive is formatted during the process. If you want to save anything, first run the live CD & backup any personal data.

---

### Post by pyrofyr on 2009-01-01
IS there a tutorial (Guessing there should be) to go over the process of reinstalling over the same spot? I still have the Live CD which I'm guessing I'll need for this...

---

### Post by kestrel1 on 2009-01-01
look at this:
[http://mybrainrunslinux.com/node/2](http://mybrainrunslinux.com/node/2)
Then just do a fresh install as you did originally.

---

### Post by DublinPCservices on 2009-01-01
> **kestrel1 said:**
> backup any personal data.

And it's best if you backup to external media, like a DVD disk, or a USB key not, because if you backup to another disk on the same machine, you run the risk of blatting your data.

---

### Post by mkvnmtr on 2009-01-01
I have reinstalled on the same partitions many times. It was seldom required to save settings because I was a new user and just going to mess up again. Use tha manual install option and when GParted comes up you should see which partition is which. You will have no need to change anything. You might have to mark the mount "/" or you might not. It seems to depend on which distro you are installing. Then you will need to mark your Ubuntu partition to be formated. Then proceed. There should be nothing else to do and it will proceed with the install. If you need to save settings the guide above is very good.

---

### Post by pyrofyr on 2009-01-01
Yea, I don't care about the data, at all. I have nothing saved on that partition. As long as it doesn't mess with my Vista stuff (I'm dualbooting to try it out :S) I'm fine.

---

### Post by mkvnmtr on 2009-01-01
As long as you don;t change any partitions it should not do any more than reinstall Grub and install over your old Ubuntu. Make sure you know what partition Ubuntu is in. After you have a little experience it is easy to tell but at first it takes some thought. You can always back out up to the point of format. Then you can take a screen shot from the partition editor on the live disk and go to the forum to ask to be sure.

---

### Post by pyrofyr on 2009-01-01
Kay, I'll be doing this now -Pauses usenet downloads- Bleh, another day of downloading, but it's worth it to fix this.

---

