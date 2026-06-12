---
title: "Dysfunctional &quot;Mount&quot;"
date: 2010-11-14
forum: New to Ubuntu
---

### Post by Spright on 2010-11-14
Hi all,

It seems like something went very wrong with my "mount" (Ubuntu 10.10):

1. When I insert a CD, it doesn't refresh in Nautilus. The previous CD name is displayed, and the only thing to do is restart Ubuntu.

2. When I insert a USB stick, it appears twice: once as "usb0" and once as the stick's name ("SanDisk Cruz", e.g.). I then can't perform any write or delete on files on the stick. Just nothing happens. My workaround for that is using "gksu nautilus" from the terminal.

3. I can't unmount the stick: "unmount: /media/usb0 is not in the fstab (and you are not root)". Even with "gksu nautilus" I can't: "Could not display "computer:///." Nautilus cannot handle "computer" locations".

4. I reinstalled the mount and unmount packages in Synaptic, to no avail.

5. And perhaps unrelated: sometimes I don't have permission to copy files from a CD. These are CDs that were burnt on a Windows system, but should this make a difference? The only workaround is again "gksu nautilus".

Thanks in advance!

---

### Post by Spright on 2010-11-15
Hmmm, nobody has a clue? I was somehow sure this was a simple issue for Ubuntu experts... Anyone?

---

