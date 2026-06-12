---
title: "Mounting network drives dependent on user"
date: 2008-10-26
forum: Networking &amp; Wireless
---

### Post by Fitz_the_gap on 2008-10-26
Hi, I've managed to authenticate users via 2003 domain controllers and  mount network drives via pam mount. The issue I now face is connecting different network drives dependent on the user logging in. For example students will have their home drives and a read only share mounted at login while teachers will have their own home folders all of the student home folders as well as a share only available to all staff members. Any help on this issue will be very helpful. 
Cheers
Fitz

P.S We're using Hardy Herron

---

### Post by dmizer on 2008-10-26
You'll need to use autofs for that. I don't have a lot of experience with autofs, but I have managed to make it work. Notes on that in this lengthy thread: [http://ubuntuforums.org/showthread.php?t=337482](http://ubuntuforums.org/showthread.php?t=337482)

Some more good information regarding autofs in the following links:
[http://ubuntuforums.org/showthread.php?t=580989](http://ubuntuforums.org/showthread.php?t=580989)
[https://lists.ubuntu.com/archives/ubuntu-users/2007-April/111855.html](https://lists.ubuntu.com/archives/ubuntu-users/2007-April/111855.html)

---

### Post by Fitz_the_gap on 2008-10-27
Thank you I'll take a look later on today.
Cheers

---

### Post by Fitz_the_gap on 2008-11-06
I've ended up using pam mount to connect network drives dependent on the group they're in. I used the PGRP option in pam mount and setting the primary group option for each user in AD to achieve this.

---

