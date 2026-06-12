---
title: "Sony Vaio X backlight control problem in Ubuntu 11.04"
date: 2011-06-05
forum: New to Ubuntu
---

### Post by MishnayicHacker on 2011-06-05
I recently installed Ubuntu 11.04 on a friend's Sony Vaio X (the exact model number is VPCX131KX).  He told me about a few issues he has found, and I haven't found the solution for them in the forums.  So I'm going to post each one as a separate thread here, in hopes of finding the answer and perhaps helping future searchers with the same issue.

The first issue is that the backlight brightness cannot be adjusted.  He apparently *was* able to adjust it when he first bought it and it apparently had an earlier version of Ubuntu installed, but I did not see that myself.  I am taking his word for it.

The backlight is supposed to be controlled by Fn-F5 and Fn-F6.  Using these key combinations causes an indicator to float in the top right of the screen, showing that the brightness is supposedly being increased or decreased.  It reacts to pressing those key combinations, but nothing changes in the actual brightness.

Would it make sense to install an earlier version, as long as 11.04 is in Beta, in the hopes that it would work?  Or can anyone recommend another solution?

Thanks!

---

### Post by MishnayicHacker on 2011-06-29
So it seems like I will be able to post the answer to my own question,  or at least a work-around that someone else has put together.

In general the problem has been reported frequently and elsewhere.  [Here]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/524967") there is a bug report from last year about the screen brightness functionality on Sony Vaio Y.  And within there is a patch by [Francesco Giudici]("https://launchpad.net/%7Efgiudici") that solved the problem for this Vaio X.  See post #7.

I must mention just for the record that the first thing I tried to do  was roll back the version to 10.10 and then to 9.10, because the friend  who owns the Vaio told me that when he bought it second hand, it had an  earlier version of Ubuntu installed, and then it DID work.  After  installing these earlier versions, though, trying to adjust the screen  brightness with Fn+F5 or Fn+F6 still did not work.

The patch linked to above worked for Ubuntu 9.10.  I then reinstalled  11.04 (technically by upgrading 9.10 to 11.04).  After the upgrade the  patch was no longer working, although as before, an indicator would  float in the top  right of  the screen, showing that the brightness is supposedly being  increased or  decreased, responding to the Fn+F5 and Fn+F6 keys.

I ran the patch again and it worked.  To repeat, this patch is intended for Vaio Y but also works for Vaio X.

To install this patch by Francesco:
Go here and see comment #7: [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/524967](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/524967)
Download the tar
Extract
Read the README
Open a terminal window and sudo install.sh as directed in the README
reboot

---

