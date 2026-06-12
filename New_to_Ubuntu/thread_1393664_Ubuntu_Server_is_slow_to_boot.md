---
title: "Ubuntu Server is slow to boot"
date: 2010-01-29
forum: New to Ubuntu
---

### Post by sandyc on 2010-01-29
Hi there

After grub kicks-off, nothing much happens for a couple of minutes (I see a blank screen with  a blinking cursor).

There is a brief flash of a  'no such drive' error just after grub starts and before the screen clears.

How can I tell what's taking so long?  I thought it might be fsck, but I set the appropriate flags to zero in fstab, and the boot was still slow.

Any tips gratefully received.

Thanks

Sandy

---

### Post by cenzorrll on 2010-01-30
there's some good info in here [http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

near the bottom there's a section of bugs and known workarounds, sounds like you might have the "hangs at boot" one.

i also believe if you hold shift, you'll be able to select the "safe mode" kernel (I forget what it's actually called, should be the second selection) and it should give you a verbose boot.

---

