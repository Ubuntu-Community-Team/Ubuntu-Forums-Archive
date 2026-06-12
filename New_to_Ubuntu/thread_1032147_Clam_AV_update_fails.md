---
title: "Clam AV update fails"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by grewolf on 2009-01-06
I run Ubuntu 8.10 Ibex

I have tried to do sudo freshclam and sudo freshclam -v.  and I receive 2 errors.  I get **_/var/log/clamav/freshclam.log is locked by another process_** and **_Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log)._**

I have found this link and it mirrors my situation ,except only reports the one error, but looks like no solution:
[HTML]http://ubuntuforums.org/showthread.php?t=527480&highlight=problem+internal+logger[/HTML]

Also have a problem with **_rar code not compiled in_** when doing clam scans and read this bug report which hasn't been updated since june of 2008.  

[HTML]https://wwws.clamav.net/bugzilla/show_bug.cgi?id=1050[/HTML]

---

### Post by rburkartjo on 2009-01-06
gre, have you tried sudo clamtk in terminal/cheesemaker

---

### Post by Pidster on 2009-04-26
Had the same problem..   the daemon was running in processes.

had to --->    sudo /etc/init.d/clamav-freshclam stop

then sudo freshclam -v

and it worked for me.

then restart the daemon with

sudo /etc/init.d/clamav-freshclam start

after it was restarted i was able to run the freshclam -v  command with no more porblems.  thinking it might have been locked up..??

---

### Post by binbash on 2009-04-26
stop apparmor, update, then start apparmor

---

### Post by 92fs on 2009-11-10
> **Pidster said:**
> Had the same problem..   the daemon was running in processes.

had to --->    sudo /etc/init.d/clamav-freshclam stop

then sudo freshclam -v

and it worked for me.

then restart the daemon with

sudo /etc/init.d/clamav-freshclam start

after it was restarted i was able to run the freshclam -v  command with no more porblems.  thinking it might have been locked up..??

thx for the tip, worked like a charm.

---

### Post by masroorgilani on 2010-02-06
> **Pidster said:**
> Had the same problem..   the daemon was running in processes.

had to --->    sudo /etc/init.d/clamav-freshclam stop

then sudo freshclam -v

and it worked for me.

then restart the daemon with

sudo /etc/init.d/clamav-freshclam start

after it was restarted i was able to run the freshclam -v  command with no more porblems.  thinking it might have been locked up..??

@Pidster. Thanks a lot, it works like a magic.

---

### Post by windowsconvert09 on 2011-07-21
> **Pidster said:**
> Had the same problem..   the daemon was running in processes.

had to --->    sudo /etc/init.d/clamav-freshclam stop

then sudo freshclam -v

and it worked for me.

then restart the daemon with

sudo /etc/init.d/clamav-freshclam start

after it was restarted i was able to run the freshclam -v  command with no more porblems.  thinking it might have been locked up..??

This worked great! Thanks!

---

### Post by kiwi_steve on 2012-07-31
Fixed it for me as well... saved me rebooting.  Thanks

> **Pidster said:**
> Had the same problem..   the daemon was running in processes.

had to --->    sudo /etc/init.d/clamav-freshclam stop

then sudo freshclam -v

and it worked for me.

then restart the daemon with

sudo /etc/init.d/clamav-freshclam start

after it was restarted i was able to run the freshclam -v  command with no more porblems.  thinking it might have been locked up..??

---

### Post by wildmanne39 on 2012-07-31
Hi, this is an old thread so it has been closed, thanks for sharing.

---

