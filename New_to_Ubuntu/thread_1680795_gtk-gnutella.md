---
title: "gtk-gnutella"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by Legeril on 2011-02-03
I've recently downloaded gtk-gnutella and mldonkey, but I can't seem to figure them out at all, when I load the program it just sits there saying 'not connected'. Am I missing something here? Programs like frostwire load very easily and you just search (insert band/song name) these don't seem to be on any network, I've looked through the options / preferences and can't seem to figure it out.

Has anyone gotten these programs working? OR are they bust now? If anyone knows of any p2p programs I would be grateful.

---

### Post by ram4 on 2011-02-03
> **Legeril said:**
> I've recently downloaded gtk-gnutella and mldonkey, but I can't seem to figure them out at all, when I load the program it just sits there saying 'not connected'. Am I missing something here? Programs like frostwire load very easily and you just search (insert band/song name) these don't seem to be on any network, I've looked through the options / preferences and can't seem to figure it out.

Has anyone gotten these programs working? OR are they bust now? If anyone knows of any p2p programs I would be grateful.

You must be using an old version, and it cannot bootstrap to the network.

I'd suggest you grab the sources from SVN and attempt to build the package directly by following the instructions from README.Debian (Ubuntu is Debian-based, so this will work just fine).

Just run:
    svn co [https://gtk-gnutella.svn.sourceforge.net/svnroot/gtk-gnutella/trunk/gtk-gnutella/](https://gtk-gnutella.svn.sourceforge.net/svnroot/gtk-gnutella/trunk/gtk-gnutella/)

If you don't have the "svn" command, run:

    apt-get install subversion

first.

Good luck.

---

