---
title: "How to remove icons of unmounted partitions from desktop"
date: 2011-06-15
forum: New to Ubuntu
---

### Post by beew on 2011-06-15
I am testing out Xubuntu by installing it in an external hard drive where there are many different partitions. Whenever I boot into Xubuntu all the other partitions would show up on the desktop even though they are not mounted, see attached screenshot. In Ubuntu they only show up when the partitions are mounted.

Since they are not mounted I can't remove the icons by unmounting the partitions like in Ubuntu. How do I get rid of the icons?

Other than this and the rather basic themes so far it feels quite nice.

Thanks.

P.S. Is there a way to configure Ubuntu (Gnome) so that when many partitions are mounted the icons would line up nicely like in the screenshot or in Mint instead of scattering all over the desktop?

---

### Post by jtarin on 2011-06-15
Mount those drives through /etc/fstab (instead of automounting) and define their mount points anywhere besides /media. I think /media puts them on the desktop.

---

### Post by coffeecat on 2011-06-15
> **beew said:**
> I am testing out Xubuntu by installing it in an external hard drive where there are many different partitions. Whenever I boot into Xubuntu all the other partitions would show up on the desktop even though they are not mounted, see attached screenshot. In Ubuntu they only show up when the partitions are mounted.

Since they are not mounted I can't remove the icons by unmounting the partitions like in Ubuntu. How do I get rid of the icons?

I noticed this strange behaviour when I tried Xubuntu Natty in alpha/beta. I was glad to see that automounting of partitions was now easy in Xfce, but didn't like this default behaviour and couldn't find a way of hiding unmounted partitions. I only want to see mounted partitions on a desktop. I'd be interested in any answers you might get.

> **beew said:**
> P.S. Is there a way to configure Ubuntu (Gnome) so that when many partitions are mounted the icons would line up nicely like in the screenshot or in Mint instead of scattering all over the desktop?

Usually they do line up by default. Right-click on the desktop and make sure "Keep Aligned" is ticked. There is a grid that icons will snap to when you tick that.

---

### Post by beew on 2011-06-15
> **coffeecat said:**
> 
Usually they do line up by default. Right-click on the desktop and make sure "Keep Aligned" is ticked. There is a grid that icons will snap to when you tick that.

"Keep Aligned" has always beeen ticked but it doesn't make a difference. See the screenshot. It has been like that since Lucid (when I started Ubuntu) and it doesn't depend on hardware as I got the same behaviour with different hard drives and machines.

I cannot show tthat "Keep Aligned" is checked in the screenshot because I can't take screenshots when any menu is opened in Unity, another bug?

---

### Post by beew on 2011-06-15
> **jtarin said:**
> Mount those drives through /etc/fstab (instead of automounting) and define their mount points anywhere besides /media. I think /media puts them on the desktop.

They are not mounted.

---

### Post by egalvan on 2011-06-15
> **beew said:**
> They are not mounted.

They are not mounted, but they have been discovered,
so they are shown on the desktop for ease of use.

As jtarin stated, mount the in fstab, but use /mnt as a mountpoint, instead of /media.

/media puts icons on the desktop, /mnt does not.

---

### Post by yetiman64 on 2011-06-15
You are right, they aren't mounted even when their icons show on the desktop. Even in thunar the buttons show when they are unmounted unlike nautilus, It certainly is different.

To get rid of all the icons, right click the desktop and in the menus follow Applications > Settings > Settings Manager, look for the icons tab. See the attached pics. :)

This is if you want to remove the icons altogether, they can be mounted and accessed easily in any thunar window side pane.

---

### Post by duckegg12 on 2011-10-01
1. Mounting in fstab means they are permanently mounted. I've got 20 of them and I really don't want them permanently mounted. Furthermore, mounting them in /mnt seems a ridiculously convoluted way to get round what should be a trivial problem. I want to be able to mount them as-and-when needed. At present they represent mere desktop clutter!

2. I'm trying Xubuntu 11.10 beta2 (to escape the web-book interfaces of Unity and Gnome3). In Xubuntu 11.10  there is no "ICONS" tab in <Applications> <Settings> <Settings Manager>. The only treatment of icons here is to adjust their visual aspects, and the only drive controls relate to removable media. 

3. 3 hours of googling the problem has led to nothing else that works. Has anyone else managed to solve this, or should I give-up and join the push to Mint??

---

### Post by QLee on 2011-10-01
> **duckegg12 said:**
> 1. Mounting in fstab means they are permanently mounted. I've got 20 of them and I really don't want them permanently mounted. Furthermore, mounting them in /mnt seems a ridiculously convoluted way to get round what should be a trivial problem. I want to be able to mount them as-and-when needed. At present they represent mere desktop clutter!
...

Usually the moderators prefer that someone open a new thread rather than posting  to an older one but your question (if there is in fact a question) is related pretty closely to this thread.

Can't blame you for not wanting the clutter.  I understand what you mean, however, for most users things are different and they aren't going to have as many volumes as you do. What you want is the old behaviour and it seems that that has been changed in the name of "usability" for novice users, there seems to be that trend in distros these days, aiming at ease of use and no need to learn something new, novice users. It's much easier for new users to find a drive if it is somewhere they can see it and since you know more than that, it shouldn't make things much harder for you.

On the other hand, the solution jtarin gave would give the behaviour you want and it isn't that much different from the old way of doing things. 

I and many other people always used to include our mountpoints in fstab and then we could mount by just specifying the proper device node. (i.e. mount /dev/sda12 and the system parsed the rest of the mount from fstab). If you use the noauto option in your fstab line, it won't be mounted at boot time or until you choose to. Then you would not see the unmounted drives on your desktop and you could mount or unmount as you choose.

---

