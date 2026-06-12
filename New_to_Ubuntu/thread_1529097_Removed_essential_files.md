---
title: "Removed essential files"
date: 2010-07-11
forum: New to Ubuntu
---

### Post by nnjond on 2010-07-11
Hi
I've made a bad decision, used symnaptic and removed some essential files from my os. 

libdm-nouveau1-dbg	2.4.18-lubuntu	userspace interface

and

xserver-xorg-video-nouveau	

Now i can only access my home dir data from a live cd. can I re-install the missing files from the live cd? A fresh install will require me to back up all my data wont it ?

Thanks

---

### Post by JustinR on 2010-07-11
Not sure if this is entirely correct but it should work.

So from the live CD mount your hard drive (or what ever you installed Ubuntu to) and figure out where its mounted at eg. /media/UBUNTU.

Then open up a terminal and type in:

```

sudo chroot /media/UBUNTU

```

**Edit: chroot is a command that will basically let you make changes to your existing Ubuntu installation instead of the live CD**

Then just "sudo apt-get install" all of the packages you removed. When done, type exit and restart your computer without the Live-CD and see if everything is well again.

---

### Post by libssd on 2010-07-11
I'm not sure I understand. Can you still boot from the installed system? Can you still start Synaptic? If so, search for "nouveau" and see if they show up. If they don't, try the same search in the Ubuntu Software Center.

On the other hand, if you can only boot from LiveCD, I'm not sure how you would install specific packages on a different drive. 

I have gotten myself into unrecoverable corners so many times that I am a firm believer in restorable system images. Remastersys has saved me many a time.

---

### Post by nnjond on 2010-07-11
Thanks for your interest. I can only boot from a live cd and 1870 MB have been freed up ? So many additional files have been removed as a consequence how will i track them all down?

---

### Post by JustinR on 2010-07-11
Well how many packages did you remove?

You said you removed those 4/5 packages on your first post so just reinstall them.

---

