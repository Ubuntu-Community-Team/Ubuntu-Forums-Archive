---
title: "Related wget tools?"
date: 2007-06-17
forum: Networking &amp; Wireless
---

### Post by Dudsmacka2 on 2007-06-17
I've have a group of ubuntu servers hosting several game server which are launched and managed through a series of BASH scripts.

As of now to update the servers I have to update manually.  I am looking for a way for the servers to automatically update themselves between sessions from a "dispatch" machine via a second network and utilities such wget.

I am curious if there exists a command that similar to do a *quick* comparison utility that would compare a remote to a local file, be it md5 hash, timestamps, or whatever.

---

### Post by dreadlord_chris on 2007-06-17
> **Dudsmacka2 said:**
> I've have a group of ubuntu servers hosting several game server which are launched and managed through a series of BASH scripts.

As of now to update the servers I have to update manually.  I am looking for a way for the servers to automatically update themselves between sessions from a "dispatch" machine via a second network and utilities such wget.

I am curious if there exists a command that similar to do a *quick* comparison utility that would compare a remote to a local file, be it md5 hash, timestamps, or whatever.

I'd take a look at **rsync**

---

