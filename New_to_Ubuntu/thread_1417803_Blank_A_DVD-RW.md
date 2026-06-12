---
title: "Blank A DVD-RW"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by Martin Marshalek on 2010-02-27
I finally finished this project I've been working on all day and have the final product saved as an .iso. I need to take a DVD I have and burn it now. I took one of my many used DVD-RW's and used the Blank Disc option in Brascero, the right-click context menu, and GnomeBaker which results in a message of success. When I try to place the disc back in my computer though, nothing mounts and I can't do anything with it. What is going on here?

---

### Post by Martin Marshalek on 2010-02-27
bump

---

### Post by hansdown on 2010-02-27
Hi Martin Marshalek.

I've been seeing similar problems.

Perhaps a bug report is in order.

Edit: There are a number of bug reports, going back a while.

[http://www.google.ca/search?q=Blank+A+DVD-RW+in+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=Blank+A+DVD-RW+in+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by Martin Marshalek on 2010-02-28
I would be curious to see whether this is GNOME issue or a *buntu issue though. If this is the fault of some of the software in GNOME then I will switch to Kubuntu if necessary as this is quite important to me and I shouldn't have to use my old Windows XP comp from 2003 to do this.

---

### Post by Teber on 2010-02-28
did you try the brasero option "burn image to disk"? i never have any problems with that one...

hope this helps.

---

### Post by Martin Marshalek on 2010-02-28
Well, I wanted to erase all of the useless stuff on the disc first so I erased it. Now the computer won't even recognize it so Brascero does nothing.

---

### Post by Paddy Landau on 2010-02-28
I suggest that you install [K3b]("apt:k3b") from the repositories (System > Administration > Synaptic Package Manager).

When you start K3b, go to Tools > Format DVD-RW.

If that doesn't work, perhaps your DVD has been KO'd. Try another DVD to find out whether it works.

---

### Post by hansdown on 2010-02-28
I think it is a mount issue, because I can see the blanked disk on my friend's windows 7 laptop.

I tried

```
sudo mount /media/cdrom0/ -o unhide

```
and got this error message...

---

