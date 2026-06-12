---
title: "Does Ubuntu Automount?"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by RoflHaxBbq on 2010-12-04
I'm having trouble with Kubuntu 10.10, as I cannot get it to mount a game CD.

I want to switch to Ubuntu in the hope that it will fix the problem.

My question is, In Ubuntu 10.10, when you insert a game CD, will it automatically come up on the desktop or in the file browser, like it does with a USB flash drive?

Thanks,
-RoflHaxBbq

---

### Post by oldos2er on 2010-12-05
Install the widget 'device notifier', it's very configurable.

---

### Post by RoflHaxBbq on 2010-12-06
I believe that is already installed, and configuring it has had no effect.

When I insert a DVD, it mounts every time.

When I insert a CD, it only mounts about 1% of the time.

So if I insert a CD, and it doesn't mount automatically, it takes about 20 reinserts before it decides to mount, and an error message shows when I try and mount manually via terminal, so I believe it is a bug with KDE.

But is there a bug similar to this is GNOME/Ubuntu?

---

### Post by HermanAB on 2010-12-06
Hmm, I haven't had auto-mount issues in Linux for the past 5 years or more.

---

### Post by john77eipe on 2010-12-06
U have any other OS on your system? 

Maybe it could be a problem with the drive.

---

### Post by QLee on 2010-12-06
[QUOTE=RoflHaxBbq]...
So if I insert a CD, and it doesn't mount automatically, it takes about 20 reinserts before it decides to mount, and an error message shows when I try and mount manually via terminal, so I believe it is a bug with KDE.
...[/QUOTE]

If you want to increase your chances of getting useful answers, post the exact error message you receive.

In addition, post the name of the game you mention in the first post.

---

### Post by oldos2er on 2010-12-06
> **RoflHaxBbq said:**
> So if I insert a CD, and it doesn't mount automatically, it takes about 20 reinserts before it decides to mount, and an error message shows when I try and mount manually via terminal, so I believe it is a bug with KDE.

But is there a bug similar to this is GNOME/Ubuntu?

I haven't had any automount problems in KDE (or Gnome either, FWIW) such as you describe. Are you sure it's not a problem with the CD itself?

You can search [https://launchpad.net/](https://launchpad.net/) for bugs, if you haven't already.

---

### Post by RoflHaxBbq on 2010-12-06
Thanks for the replies.

Another member of these forums told me to enter the CD and mount it by opening terminal and typing: mount /media/cdrom0
This returns an error of: Can't find /media/cdrom0 in/etc/fstab or /etc/mtab
I also tried: mount /media/cdrom
Which returns an error of: Can't find /media/cdrom in/etc/fstab or /etc/mtab

And I am *sure* that the CD is fine, it is unscratched, and I managed to install the game perfectly on the one time that it decided to mount itself.

---

