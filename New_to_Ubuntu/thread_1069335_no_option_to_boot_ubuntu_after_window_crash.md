---
title: "no option to boot ubuntu after window crash"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by brandon.sifford on 2009-02-13
I had to recover windows vista a few months back. now after forgetting that i installed 7.10 some time ago when i went to install 8.04 from the cd the partition step says there is the old version 7.10. ok let me clearify, when i put the 8.04 cd in and start the install and get to step 4(i think) to partion the hard drive, when i slide the bar to the right to split equaly the left side says ubuntu 7.10 and the right says 8.04. ok got that, but where is my windows vista partion? i cant seem to find 7.10 to do the upgrade to 8.04. during start up the computer boots straight to vista. please help.

---

### Post by logos34 on 2009-02-13
from the live cd run this on a terminal and post it:

sudo fdisk -l

You could try restoring grub (if 7.10 is still there, that is)--see link my signature.

---

