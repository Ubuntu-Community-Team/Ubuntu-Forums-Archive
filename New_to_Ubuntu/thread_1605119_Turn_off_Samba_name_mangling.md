---
title: "Turn off Samba name mangling?"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by ofb on 2010-10-24
Long filenames are mangled when I drag them over to the client.

I'm running ext4 and ext3. I don't want Windows compatibility -- I want Ubuntu<->Ubuntu compatibility. Finding that miscellaneous filenames have been borked after directory moves is an unhappy experience.

I'm reading 'man smb.conf', and now I've got the general idea of why this is happening.

What's the most direct way to turn off mangling? (Which I /think/ is what I want, anyway.)

---

### Post by amauk on 2010-10-24
If you're not sharing with windows, the best thing to do is not use samba
Use NFS instead

---

### Post by ofb on 2010-10-24
amauk -- maybe next weekend? ;)

With Lucid the nice NFS GUIs have been ripped out, and I'm noticing a lot of posts about NFS trouble after upgrading to Meerkat. And just right now for the moment I'd like to get some work done, and pause having filesharing adventures. (It's been a week getting this far, due to other troubles.)

---

