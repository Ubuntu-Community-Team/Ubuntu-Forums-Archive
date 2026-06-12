---
title: "Problem Running RC 10.10 From Disk"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by Ron Carson on 2010-10-03
I've downloaded (via Torrent) RC 10.10 and burned to CD.

I tried running the CD on my Ubuntu laptop but received an error stating:

"(initramfs) mount: mounting /dev/loop0 on //filesystem.squashshfs failed: Input/output error
Can not mount...."

Thinking I had a bad CD, I downloaded and burned a new ISO.  Experienced the same error.

Thinking it was problem with my laptop, I tried the CD on an older desktop, but receive the error again.

As a last resort, I checked the MD5 hash which is correct.

So, what gives??  Why can't I run this CD?

Thanks!

---

### Post by Lo0mis on 2010-10-03
I have the same exact problem. Just downloaded 10.04.1 last night (32bit desktop), verified the MD5, and burned it (Win7 built-in .iso burner). Booted it up, the Unbuntu spash screen appears for a bit, then it dumps out with the same error that you have. Tried a different PC, same deal. Which instantly makes me think bad disk or .iso, but if the MD5 is good, doesnt that mean the .iso is good?
 
 
(initramfs) mount: mounting  /dev/loop0 on //filesystem.squashfs failed: Input/output error
 
Can not mount /dev/loop0(/cdrom/Casper/filesystem.squashfs) on //filesystem.squashfs

---

### Post by Lo0mis on 2010-10-03
OK, I got it working. I burned another disk using the tool recommended on the Ubuntu download page, [Infra Recorder]("http://infrarecorder.org/"). 

I guess that, in my case at least, the Win7 .iso burning tool just, well,  *does it wrong*...

---

### Post by Ron Carson on 2010-10-03
Surely it can't be the CD burning software.  I use Brasero which is the same program I used for burning Ubuntu 10.4.

---

### Post by Ron Carson on 2010-10-04
Any suggestions?

---

