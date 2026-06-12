---
title: "How to upate antivirus database of Clamav / clamscan?"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by frenchn00b on 2009-12-12
In the manpage it states:

```
            Maximum depth directories are scanned at (default: 15).

EXAMPLES
       (0) Scan a single file:

              clamscan file

       (1) Scan a current working directory:

              clamscan

       (2) Scan all files (and subdirectories) in /home:

              clamscan -r /home

       (3) Load database from a file:

              clamscan -d /tmp/newclamdb -r /tmp

       (4) Scan a data stream:

              cat testfile | clamscan -

       (5) Scan a mail spool directory:

              clamscan -r /var/spool/mail

RETURN CODES
       Note: some 
```

---

### Post by frenchn00b on 2009-12-12
Extra info: To update it from command line, without need of using firefox, seeking, spending time and copying on the /tmp
then to su
then to update it ... long

is there soemthing automatic?

---

### Post by wangsuda on 2009-12-12
> **frenchn00b said:**
> Extra info: To update it from command line, without need of using firefox, seeking, spending time and copying on the /tmp
then to su
then to update it ... long

is there soemthing automatic?If I remember correctly, typing ```
sudo freshclam
```into the terminal should do the trick. Please see [http://ubuntuforums.org/showthread.php?t=1049748&nojs=1#goto_threadtools](http://ubuntuforums.org/showthread.php?t=1049748&nojs=1#goto_threadtools) and [http://ubuntuforums.org/showthread.php?t=1049750&nojs=1#goto_threadtools](http://ubuntuforums.org/showthread.php?t=1049750&nojs=1#goto_threadtools)

---

### Post by 73ckn797 on 2009-12-12
If you install "clamtk", found in Synaptic Package Manager, it is a graphical tool to scan for virus. Under the help tab you can update signatures.

---

### Post by bilalakhtar on 2009-12-12
Simple
```
sudo freshclam
```
Works very well. The program "freshclam" gets installed automatically when you install clamav from apt-get or synaptic. In case it is not there, then enter:-
```
sudo apt-get install clamav-freshclam
```
Cheers:popcorn:

---

### Post by frenchn00b on 2009-12-12
error:

```

  # freshclam 
ERROR: /var/log/clamav/freshclam.log is locked by another process
ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log).
  
```

```
  --------------------------------------
Received signal: wake up
ClamAV update process started at Sat Dec 12 15:44:54 2009
WARNING: DNS record is older than 3 hours.
WARNING: Invalid DNS reply. Falling back to HTTP mode.
Reading CVD header (main.cvd): OK (IMS)
main.cvd is up to date (version: 51, sigs: 545035, f-level: 42, builder: sven)
Reading CVD header (daily.cvd): OK (IMS)
daily.cld is up to date (version: 10156, sigs: 125944, f-level: 44, builder: arnaud)
--------------------------------------
Received signal: wake up
ClamAV update process started at Sat Dec 12 16:44:57 2009
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.95.2 Recommended version: 0.95.3
DON'T PANIC! Read http://www.clamav.net/support/faq
main.cvd is up to date (version: 51, sigs: 545035, f-level: 42, builder: sven)
Downloading daily-10157.cdiff [100%]
daily.cld updated (version: 10157, sigs: 125963, f-level: 44, builder: arnaud)
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Current functionality level = 43, recommended = 44
DON'T PANIC! Read http://www.clamav.net/support/faq
Database updated (670998 signatures) from db.local.clamav.net (IP: 130.59.10.36)
WARNING: Clamd was NOT notified: Can't  
```

---

### Post by 55tptag on 2009-12-21
Hello frenchn00b, I get the same error as you posted:
# freshclam
ERROR: /var/log/clamav/freshclam.log is locked by another process
ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log).

---

### Post by NoaHall on 2009-12-21
> **55tptag said:**
> Hello frenchn00b, I get the same error as you posted:
# freshclam
ERROR: /var/log/clamav/freshclam.log is locked by another process
ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log).

Close every window/terminal running clamav, and run it again.

---

