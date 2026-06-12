---
title: "Setting up moodle [help please]"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by Aphrodite54 on 2009-11-27
It's been doing this for a long time but it usually works fine if I just force quit from synaptic but if I run "sudo dpkg --configure -a" it works fine until it gets to moodle at which point it stays at:
"Setting up moodle (1.9.4.dfsg-&#920;ubuntu1.1)"

Today, after installing the recommended updates I opened my laptop to this:
[B]
One[/B] **or** **more** **of** **the** **mounts** **listed** **in** /**etc**/**fstab** **cannot** **yet** **be** **mounted**:
(ESC for recovery shell)
 /: waiting for /dev/disk/by-uuid/01cceacc-c363-4295-8e9a-3792c9aa855d
/: tmp waiting for (null)
swap: waiting got UUID=4ef950ca-a29d-49df-a317-5d4ab18951a2

So I clicked ESC and put in:
mount -n -o remount,rw /

After putting that I put in:
sudo dpkg --configure -a

And again it came to the point where it said: "Setting up moodle (1.9.4.dfsg-&#920;ubuntu1.1)"

It's still there.

---

### Post by Sef on 2009-11-28
Moved to ABT.

---

