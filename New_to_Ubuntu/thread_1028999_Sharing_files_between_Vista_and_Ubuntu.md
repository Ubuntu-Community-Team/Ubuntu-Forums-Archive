---
title: "Sharing files between Vista and Ubuntu"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by AccidentProne on 2009-01-02
Hello.
A few days ago i decided to give Ubuntu a try installing it with the help of Wubi (inside Windows), so far its been awesome.

But now i come with a question from an absolute noob(me).

All my music, pictures, files, etc its stored within the Vista partition, what i ask is for a way to use those files on Ubuntu, or share them between the 2 OS.

Thx.

---

### Post by jerome1232 on 2009-01-02
You can access your Windows Vista files under /host (might be /hosts)

Just Click Places->Computer->Filesystem->Host(s?) and browse around.

---

### Post by Ender41 on 2009-01-02
> **AccidentProne said:**
> Hello.
A few days ago i decided to give Ubuntu a try installing it with the help of Wubi (inside Windows), so far its been awesome.

But now i come with a question from an absolute noob(me).

All my music, pictures, files, etc its stored within the Vista partition, what i ask is for a way to use those files on Ubuntu, or share them between the 2 OS.

Thx.


  I've never tried that way, I dual boot vista and linux and mount my vista partition and am able to get files that way. However I do use samba to share files from my son's vista computer so that might be an option, again I haven't ever installed from within windows so could be leading you up the garden path so to speak but suspect it could work. You will need to enable sharing of the appropriate folders within vista though

---

### Post by jerome1232 on 2009-01-02
> **Ender41 said:**
> I've never tried that way, I dual boot vista and linux and mount my vista partition and am able to get files that way. However I do use samba to share files from my son's vista computer so that might be an option, again I haven't ever installed from within windows so could be leading you up the garden path so to speak but suspect it could work. You will need to enable sharing of the appropriate folders within vista though

In a Wubi install the host's c: partition is mounted at /host, any other partition's will be mounted under /media like normal.

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20access%20the%20Windows%20drives?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20access%20the%20Windows%20drives?)

---

### Post by AccidentProne on 2009-01-02
> **jerome1232 said:**
> You can access your Windows Vista files under /host (might be /hosts)

Just Click Places->Computer->Filesystem->Host(s?) and browse around.

Whoa, that was actually pretty easy, thanks a lot. :D

---

