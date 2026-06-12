---
title: "Grub help needed"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by Don1500 on 2009-11-08
I foolishly deleted a file I didn't mean to. 
it's /usr/share/images/grub
I thought the FILE grub was a directory and tried to move a file into it. But it's a file, one I need. How can I get it off the Karmic live CD?

---

### Post by Don1500 on 2009-11-08
Cherp..Cherp

---

### Post by phillw on 2009-11-08
> **Don1500 said:**
> I foolishly deleted a file I didn't mean to. 
it's /usr/share/images/grub
I thought the FILE grub was a directory and tried to move a file into it. But it's a file, one I need. How can I get it off the Karmic live CD?

Hi,

stay away from sudo !!! :lolflag:

I'm kinda thinking that a refresh of your grub should get you there. 

[http://www.unixnewbie.org/how-to-easily-upgrade-grub-2/](http://www.unixnewbie.org/how-to-easily-upgrade-grub-2/)

However, if you've nuked stuff from your hard-disk you're going to BACKUP your stuff, then mark it for re-install.. there are options within apt to do updates, safe stuff etc.

```
dpkg-reconfigure (packagename)

```

May be of help, but, as you've already done harm, please take the time to read the stuff on apt ..

[http://maketecheasier.com/become-an-apt-guru/2009/02/24](http://maketecheasier.com/become-an-apt-guru/2009/02/24)

A further set of info for grub2 is over here -->  [http://www.vpolink.com/showthread.php?p=3068#post3068](http://www.vpolink.com/showthread.php?p=3068#post3068)   It's near the bottom of the resources link, but the two threads mentioned are the live ones.

Phill.

---

### Post by ranch hand on 2009-11-08
Go to synaptic and reinstall grub2-splashimages.  That should do it.

And it is a folder.  It holds your pictures for your menu background.

---

### Post by Don1500 on 2009-11-08
Thanks, All's right with the world, Grub works fine and I have a good splash screen.

---

