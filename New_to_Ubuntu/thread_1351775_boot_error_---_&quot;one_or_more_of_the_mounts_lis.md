---
title: "boot error --- &quot;one or more of the mounts listed in ... cannot yet be mounted&quot;"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by raequin on 2009-12-10
[solved]

I recently upgraded from 9.04 to 9.10.  The dual-boot laptop has started up in Ubuntu successfully a couple times, but it has also failed to do so a couple times.  On the last attempt I got the following message:

> One or more of the mounts listed in /etc/fstab cannot yet be mounted
Swap: waiting for UUID-becc1ab0-c8b9-42e9-9127-18350f313938
Press ESC to enter a recovery shell

Pressing ESC resulted in nothing but a blank screen.  I got this message once earlier today, but the computer shortly went to continue booting, i.e. it started up allright that time.

Can you help me with this problem?

---

### Post by Ocxic on 2009-12-10
if you can still boot i would find out what that uuid is pointing to. It's possible that the volume or HD it just a little slow for the OS. I've been seeing waiting messages similar to your getting since upgrading  9.10, but my system always boots.

post the output of "sudo cat /etc/fstab"

---

### Post by marshmallow1304 on 2009-12-11
I have had these as well, with no apparent negative effect.  My (somewhat uneducated) guess is that my ext4 / partition is booting a little too fast for my ext3 /home partition.


Edit: Just noticed that the error you got referred to Swap.  Mine referred to /home.  In any case, glad you got it sorted.

---

### Post by raequin on 2009-12-11
This problem is solved.  I followed the instructions of hawthornso23 on this thread ([link]("http://ubuntuforums.org/showthread.php?t=1306009&highlight=9.10+swap+mount+mounted+yet&page=4")).  I.e. opened GParted, found the swap partition, and copied the UUID given in that program into fstab for the UUID under "swap."

I am guessing it worked not only because startup went smoothly (it sometimes worked well before editing fstab), but rather because in GParted the swap partition was inactive before the edit and now it shows up as active.

Thanks everyone.

---

