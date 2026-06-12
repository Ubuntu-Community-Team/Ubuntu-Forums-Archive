---
title: "Ubuntu 9.04 / SVN / libldap_r-2.4.so.2"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by sanjaymk on 2009-07-08
Hello All,

I recently upgraded to Ubuntu Ver. 9.04(Jaunty Jackalope).  After the upgrade, I was not able to run SVN on the command line or SVN using tools like Netbean 6.5.  
The error I was getting was

```
/usr/bin///usr/local/lib/libldap_r-2.4.so.2: no version information available (required by /usr/lib/libaprutil-1.so.0)
/usr/bin///usr/local/lib/libldap_r-2.4.so.2: no version information available (required by /usr/lib/libpq.so.5)

```

Doing some googling and mucking around, I fixed the problem using the below steps.

STEP 1:
=======
**sudo nano /etc/ld.so.conf.d/libc.conf**

Commented the existing line ***/usr/local/lib*** and added the line ***/usr/lib***

exit out of the editor

STEP 2
======
**sudo /sbin/ldconfig -v**

after doing the above two steps the SVN and Netbeans stuff started to work.  

My questions are

#1) In terms of linux/ubuntu world what did I do that it started working. :)
#2) Did I break something else in UBUNTU 9.04 by doing this?(which is not apparent right now)

From the output of STEP 2, I'm guessing that I've made the system/OS look for libraries in a different location.  

Any explanations about this behavior is highly appreciated.

Thanks,
Sanjay.

---

