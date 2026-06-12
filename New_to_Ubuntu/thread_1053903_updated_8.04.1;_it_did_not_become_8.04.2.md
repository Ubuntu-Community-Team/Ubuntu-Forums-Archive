---
title: "updated 8.04.1; it did not become 8.04.2"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by movrshakr on 2009-01-29
I saw in the ubuntu news a press release about 8.04.2 LTS being released.  I did an update online with my Hardy 8.04.1, and it did not become 8.04.2.  Do you have to do a complete reinstall to get 8.04.2?

---

### Post by overdrank on 2009-01-29
> **movrshakr said:**
> I saw in the ubuntu news a press release about 8.04.2 LTS being released.  I did an update online with my Hardy 8.04.1, and it did not become 8.04.2.  Do you have to do a complete reinstall to get 8.04.2?

I updated and now my system shows 
```
:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.2
Release:	8.04
Codename:	hardy

```

---

### Post by movrshakr on 2009-01-29
Now, this is very, very strange.  I ran update manager again and it finds NO updates pending.  So, look at these results:

Running uname -a
Linux maximus 2.6.24-23-generic #1 SMP Thu Nov 27 18:44:42 UTC 2008 i686 GNU/Linux

Running cat /etc/issue
Ubuntu 8.04.1 \n \l

Running /usr/bin/lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.1
Release:	8.04
Codename:	hardy

So, just what the heck is going on?

---

### Post by overdrank on 2009-01-29
Ok have you tried via the terminal
```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by 3rdalbum on 2009-01-29
Ubuntu 8.04.2 might not have made it to your local mirror yet. Go into Software Sources and make it point to the Main Server, reload the package list and you should find some more updates.

---

### Post by movrshakr on 2009-01-29
> **overdrank said:**
> Ok have you tried via the terminal
```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get dist-upgrade
```
No, I have not done that, but will.

Does that suggestion mean that normal upgrade process should not be expected to do it?

One other thought.  During the installation of the pending updates, it detected that menu.lst was 'different.' That was because I had deleted "quiet splash" from the load image line.  I selected a choice to use the distribution manager's version (not the exact words--best guess) thinking that would use "the one coming down" rather than keep my modified one...but maybe it kept my old menu.lst, and that is what is holding me in the old version?  Wait...that can't be because I am now seeing the graphic load bar screen rather that the scrolling text...so my old menu.lst isn't the one being used.

---

### Post by movrshakr on 2009-01-29
.
What is the latest image file that should be loading with 8.04.2?

---

### Post by movrshakr on 2009-01-29
> **movrshakr said:**
> No, I have not done that, but will....

I did those commands, and the first one installed a bunch--following which I was at 8.04.2.  Hooray.

This was done several hours after the previous messages, and I did not re-look at the update manager in the GUI before doing it, so they might have appeared there in the mean-time.  Whatever, it did the upgrade.

Now to reboot and hope to be back!

---

### Post by movrshakr on 2009-01-29
I am back.  During the reboot, it did a 'routine fsck.'  I don't know if the upgrade scheduled that, or if it was just unfortunate happenstance.  

When that completed, the GUI screen and cursor had severe jitters, but was readable.  After another reboot, that went away, so, based on a few minutes observation, it seems OK and is at .2 level.

Thanks for everyone's help.

---

