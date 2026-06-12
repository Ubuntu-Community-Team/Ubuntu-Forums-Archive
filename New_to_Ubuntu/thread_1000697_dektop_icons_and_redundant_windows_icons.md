---
title: "dektop icons and redundant windows icons"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by charlesdb on 2008-12-03
I have 3 questions here.  Gettting to know Ubuntu.  Loving it!

I have installed Ubuntu 8.1 alongside windows, so we can use both, as my wife doesn't want to learn and is happy with windows xp.

Question 1:  Ubuntu has captured all my windows xp pro files, all useless as far as I can tell, except for "my documents and my pictures".  Is this normal to have all these apparently redundant files?  Can they be deleted whilst leaving "my documents" alone.  Or am I stuck with them?

Question 2:  I would like to get the "my documents" folder onto the desktop.  I understand using Nautilus to get stuff onto the desktop, but it only specifies certain items.  I can drag and drop folders I want onto the desktop, but those folders disappear on reboot.  I can make a link, but on reboot the link is always broken. Any ideas?  Thanks.

Question 3:  Open Office for windows xp has a quick link which amongst others includes the "my documents" file.  The Ubuntu version doesn't seem to have one.  Is this correct or is there another package I need to download?

Thanks very much

---

### Post by earthpigg on 2008-12-03
> Can they be deleted whilst leaving "my documents" alone. Or am I stuck with them?
q1: yeah, have at it. none of the files in "Pictures" or "Videos" or any of that are needed at all.

> I can make a link, but on reboot the link is always broken. Any ideas?
q2: right click on desktop. creat launcher. name it whatever you like. command:

```
nautilus /home/username
```

username, of course, needs to be replaced with charlesdb or wahtever your username is.

that will take you to your 'home' folder. if you want to go to, say, your 'Documents' folder:

```
nautilus /home/username/Documents
```

---

