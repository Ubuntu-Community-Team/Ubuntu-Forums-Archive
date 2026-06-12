---
title: "Weird NFS and Firefox 3 interaction bug"
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by bce on 2008-06-22
I'm having a weird problem with an interaction between Firefox 3 and NFS.
I've just upgraded from Ubuntu 6 LTS to 8 LTS on my intel desktop box.

I have a Sun Ultra 10 that's running Solaris 9 that I use as a general purpose server, including NFS.  My home directory is on this machine, and is accessed via an auto.home entry - resulting in my home directory on beast: being automounted every time I logged into linux.

I noticed some weirdness when I was using 6.04.  I couldn't use administrative applications for example, but when I used the dedicated admin account I set up with a local home dir, they worked fine.

Now I've upgraded to 8 LTS the firefox 3 browser basically doesn't work.  The back and forward buttons are permanently greyed out, regardless of where you've been.  Entering a URL into the address bar has no effect, and the bookmarks failed to come over too.  Completely unusable.

Then I noticed that Firefox worked fine from the admin account.  The only difference is NFS mounted homedirectory (my account) vs locally mounted home directory.

Just for laughs I tried installing Firefox-2.  This works fine - as it always did.  Therefore it's something to do with the combination of Firefox 3 and an NFS mounted filesystem.  (and probably the fact that I'm using a Solaris server)

The NFS side of things appears to be mostly working correctly.  Most applications seem to be able to load & save files just fine.  File ownerships & permissions are set correctly.  I've got the passwd and group files on the server sync'ed with the local ones in terms of usercodes and uids matching.

Any hints/clues/guides/things to try would be gratefully accepted!

Brian.

---

### Post by bce on 2008-06-23
I figured this one out.  Turned out to have nothing to do with Ubuntu at all.  It was the misbehaving Solaris NFS server.  Turns out that the Ubuntu desktop was expecting a rpc.lockd to be present on the NFS server.  For some reason it doesn't get installed along with the rest of the Solaris NFS server software.

Go figure!

I resolved the problem by giving up on the Sun as a NFS server, bought a new hard drive, and copied everything over.  All is now working perfectly.

---

