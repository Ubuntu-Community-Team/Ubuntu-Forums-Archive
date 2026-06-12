---
title: "VirtualBoxHD not expanding?"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by Xarok on 2009-01-01
So I installed XP in Virtual Box in what I'm sure was a dynamically expanding virtual HD.

XP complains though now that it's critically close to having a full HD.

Will it automatically expand when it becomes full or do I have to do something to make it expand?:confused:

Thanks all, if you have an info.

---

### Post by jboy012000 on 2009-01-01
Hi,

I found this on the VirtualBox Security Tools web site, I think it answers your question. Please see below.

"Finally, VirtualBox asked what kind of virtual drive I wanted. It supports two types that are described in the manual as follows:

    * A dynamically expanding file will only grow in size when the guest actually stores data on its virtual hard disk. It will therefore initially be small on the host hard drive and only later grow to the size specified as it is filled with data.
    * A fixed-size file will immediately occupy the file specified, even if only a fraction of the virtual hard disk space is actually in use. While occupying much more space, a fixed-size file incurs less overhead and is therefore slightly faster than a dynamically expanding file."

Hope this helps.

Cheers

John

---

### Post by lkraemer on 2009-01-01
If you used the DEFAULT 10 Gig setting, which is the MAXIMUM Size,
then installed XP you used approximately 8 Gig, leaving ~2 Gig for
other software.  You'll need to make another larger VDI and re-install
XP to start over.  I've ran into the same size limit, assuming that
it would increase over the 10 Gig initial setting.  I've not found a
way to increase it.  Maybe others have......

lkraemer

---

### Post by Cypher on 2009-01-01
Even with the dynamic virtual HD, you need to provide a maximum size. Open up VirtualBox and go to File->Virtual Media Manager. This will show you the maximum size of your VirtualHD's and how much you are using right now.

If you indeed created a VirtualHD thats too small and running out of space, there are a couple of ways of easily moving your existing installation to another VirtualHD without having to re-install everything.

THe first method is to use DD and the other is [CloneZila]("http://virtualdebian.blogspot.com/2008/03/how-to-resize-virtualbox-virtual-disk.html")..

I would suggest the CloneZilla path as it's going to be more intuitive using the GUI.

---

