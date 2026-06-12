---
title: "Installing packages from external DVD"
date: 2010-07-07
forum: New to Ubuntu
---

### Post by theraje on 2010-07-07
Hey folks,

I am trying to figure out how to get Software Sources to recognize that the Ubuntu DVD is in an external DVD drive. I used the same drive and DVD to install the system, but now I cannot for the life of me get Synaptic and friends to recognize the DVD as a software source.

The disc mounts fine, I pop it in the drive and it shows up on the desktop. I am able to browse the disc. But, when I go to Synaptic and tell it to install a package, it acts like it's trying to do something, then about a second later it errors out, giving me a "File not Found" error.

The DVD drive is at /dev/sr0 and I tried manually mounting it to /media/cdrom and a few other things, but no dice. Also, the drive does not show up when I use fdisk.

Very confusing! I really need to get my computer to recognize the DVD drive/disc to install Ubuntu software, as I am on dial-up, and it's not really practical to download everything, especially stuff that is already included on the DVD.

Any advice is greatly appreciated!

---

### Post by jerenept on 2010-07-07
open System>Administration>Software Sources
type your pasword.
Check the box next to "CD-ROM with Ubuntu 10.04 'Lucid Lynx"'
That should help, but i think you did that already.
The packages are in the /pool directory on the cd.

---

### Post by theraje on 2010-07-07
Yeah, that's checked. Also, if I go to "Other Source" and click the "Add CD" button, even with the DVD mounted and all, it will prompt me to insert a CD. If I tell it OK, it just says that it can't mount the disc (even though it's already mounted!).

Could this have something to do with the fact that I'm using an external DVD drive? If so, I guess I'm screwed...

---

### Post by theraje on 2010-07-07
Looks like I found the problem. In Synaptic, I went to Repositories and added, in the "Other Sources" tab, a new listing. The apt line:

deb file:///media/apt lucid main restricted

I successfully installed build-essential as a test. Went fine, no hitch. theraje is happy again!

---

