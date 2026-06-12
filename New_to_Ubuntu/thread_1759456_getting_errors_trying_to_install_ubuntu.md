---
title: "getting errors trying to install ubuntu"
date: 2011-05-15
forum: New to Ubuntu
---

### Post by Jeffrey Kang on 2011-05-15
Popped in the ubuntu CD boot helper, rebooted from the CD, and 95% of the way finished, I get an error saying:
An error occurred:
Permission denied
For more information, please see the log file:c:\docume~1\jeff\locals~1\temp\wubi-11.04-rev211.log

What's this?

---

### Post by dcsoldschool53 on 2011-05-15
Are you are trying to dual boot with a windows operating system using a wubi installer to install ubuntu?

---

### Post by Jeffrey Kang on 2011-05-15
Yes and No.

I've tried both options. Booting from the CD to try it out and installing over windows. I got the same error message.

---

### Post by bcbc on 2011-05-16
> **Jeffrey Kang said:**
> Popped in the ubuntu CD boot helper, rebooted from the CD, and 95% of the way finished, I get an error saying:
An error occurred:
Permission denied
For more information, please see the log file:c:\docume~1\jeff\locals~1\temp\wubi-11.04-rev211.log

What's this?

Open Windows explorer. Enter %temp% in the address bar. Open up the log file mentioned above.

If you tried booting from CD and it failed, it seems like it could be a bad CD. But post the logile and we can see what the issue is.

---

### Post by Wim Sturkenboom on 2011-05-16
You should not get the error when installing over Windows (implying removing Windows) as there will no longer be a 'c:'.

I've never done a wubi install (that is what the error message seems to refer to) but that will not install over Windows but inside Windows.

---

### Post by dcsoldschool53 on 2011-05-16
Do this only if you are planning on getting rid of windows altogether. Do not use wubi. Goto Ubuntu releases (placing a link underneath). Click on Ubuntu Maverick 10.10 or Lucid 10.04. People are still having problems with natty, so don't use that version for now. Underneath "Select an image", you will see Desktop CD. Click the one that you want, and download it. Burn it to a CD. 

Releases Ubuntu:
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

I hope this helps you:D Good luck!

---

