---
title: "Rkhunter Warnings"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by caffeinated blood on 2009-12-22
When I run Rkhunter I keep getting 2 particular Warnings: 1. /usr/sbin/unhide  and 2. /usr/sbin/unhide-linux26. Both are 20080519 [email]yjesus@security-projects.com[/email]. My question is - Who or what exactly is yjesus? My search found a yago.jesus, but no more info. Is this just some default monitoring of Ubuntu or do I have a security issue? If so, how do I go about fixing it? By the way, chkrootkit shows nothing of concern.

---

### Post by lavinog on 2009-12-23
```

aptitude show unhide
Package: unhide
State: not installed
Version: 20080519-4
Priority: extra
Section: universe/admin
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 1,962k
Suggests: rkhunter
Description: Forensic tool to find hidden processes and ports
 Unhide is a forensic tool to find processes and TCP/UDP ports hidden by
 rootkits, Linux kernel modules or by other techniques.  It includes two
 utilities: unhide and unhide-tcp. 
 
 unhide detects hidden processes using three techniques: 
 * comparing the output of /proc and /bin/ps 
 * comparing the information gathered from /bin/ps with the one gathered from
   system calls (syscall scanning) 
 * full scan of the process ID space (PIDs bruteforcing) 
   
 unhide-tcp identifies TCP/UDP ports that are listening but are not listed in
 /bin/netstat through brute forcing of all TCP/UDP ports available. 
 
 This package can be used by rkhunter in its daily scans.
Homepage: http://www.security-projects.com/?Unhide

```

it looks like it is part of rkhunter

---

### Post by madmax75 on 2009-12-23
I too get some warnings with rkhunter, but I think they probably result from some fairly strict policies that rkhunter is using when scanning for threats. So probably false alarms.

---

### Post by lavinog on 2009-12-23
I am not sure how rkhunter actually works, but it probably needs to hide itself from other processes to ensure they cannot hide from it.  It wouldn't be honest if it didn't report itself as a rootkit I guess.

The sysinternals rootkit scanner for windows will report on legitimate items in windows also, but it doesn't mean that they are malacious.

---

### Post by User3k on 2009-12-23
Don't worry about those >  Warnings: 1. /usr/sbin/unhide and 2. /usr/sbin/unhide-linux26 Do a Scroogle search and you will see that many have those come up with various distros, including myself when I run rkhunter. Nothing to worry about.

---

### Post by doas777 on 2009-12-23
I've gotten these before. the email address is just a developer on the project who handles support.

the unhide applet is used by rkhunter to look for things that may have been hidden by a rootkit, like ports and processes, per the description lavindog provided.

your fine.

---

### Post by caffeinated blood on 2009-12-24
Thanks to all who replied. I didn't think there was anything to it, but the web address listing threw me.

---

