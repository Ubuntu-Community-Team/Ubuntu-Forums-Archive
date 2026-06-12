---
title: "Help! Mounted/mountable drives not showing in &quot;Places&quot;"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by mavaddat on 2009-06-06
For some reason, the extra drives I have don't show up under the *Places* menu. When I mount them, they still don't show up. Is there a way to fix this? I just want to be able to see the drives available so I don't have to always mount them through the Terminal.


In case you're wondering how I mount them currently, please see this post:
[http://ubuntuforums.org/showthread.php?p=7399844#post7399844]("http://ubuntuforums.org/showthread.php?p=7399844#post7399844")

I am running kernel 2.6.24-23-generic x86_64 GNU/Linux on XUbuntu.

---

### Post by JCoster on 2009-06-06
I notice that you're running Hardy Heron...  Is there a reason you haven't upgraded to Jaunty or even Intrepid to see if this solves your problems?

Once mounted are they accessible?  Do they show up on your desktop?

---

### Post by mavaddat on 2009-06-06
> **JCoster said:**
> I notice that you're running Hardy Heron...  Is there a reason you haven't upgraded to Jaunty or even Intrepid to see if this solves your problems? Yes. The reason I use Hardy Heron is that I've found there is more support for versions *just before *the latest. It is also a long term support (LTS), although I'm not sure what that means.

> Once mounted are they accessible?  Do they show up on your desktop?They don't show up on the desktop, but they're accessibly by terminal. In other words, I can *cd *into them and *cp* files and stuff.

---

### Post by chrisod on 2009-06-06
Are you auto-mounting them in fstab? If you do that I believe they will appear in the places menu.

Also, I think if you create a shortcut for the mounted drives (by dragging them into the left column when looking at home in your file manager) that will also get them into the places menu. At least that is the only thing I can ever remember doing and mine show up. I use Ubuntu though - so that may be a Nautilus thing.

However, I had my wife's PC on Xbuntu for a while and I'm pretty sure the network drives were available in the places menu. I was auto mounting with fstab.

---

### Post by mavaddat on 2009-06-06
> **chrisod said:**
> Are you auto-mounting them in fstab? If you do that I believe they will appear in the places menu.I used to be able to see the available drives in the *Places* menu, and then mount them as I chose. I don't want them auto-mounted. It would be nice if I could just see them before mounting them (or automatically have them show after mounting them).

> **chrisod said:**
> Also, I think if you create a shortcut for the mounted drives (by dragging them into the left column when looking at home in your file manager) that will also get them into the places menu. At least that is the only thing I can ever remember doing and mine show up. I use Ubuntu though - so that may be a Nautilus thing.They do show up in the shortcuts when I drag from the mount-point in */media/* and drag to the column on the right. However, the file system doesn't recognize that it's a drive (so it doesn't have the mounting options). I really just want the original interface where it looked like a hard drive (icon) and it would automatically mount only when I clicked on it.

> **chrisod said:**
> However, I had my wife's PC on Xbuntu for a while and I'm pretty sure the network drives were available in the places menu. I was auto mounting with fstab.Even if I auto-mounted, I'm not sure that this would help my problem, since they're still not showing up under places.

---

### Post by JCoster on 2009-06-07
> **mavaddat said:**
> The reason I use Hardy Heron is that I've found there is more support for versions just before the latest

From my experience with Ubuntu I would agree, however updating to a newer release and persevering with any incompatibilities which may be encountered until fixed tends to - in my opinion - be a better solution to switching fully to a working Linux system.

> **mavaddat said:**
> It is also a long term support (LTS), although I'm not sure what that means

Read [this]("https://wiki.ubuntu.com/LTS") as a definition to a release being an LTS-release.

> **mavaddat said:**
> I am running kernel 2.6.24-23-generic x86_64 GNU/Linux on XUbuntu.

This is also an old kernel release...  You could try updating the kernel from Synaptic and see if this works.

---

