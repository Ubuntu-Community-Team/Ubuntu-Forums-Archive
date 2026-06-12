---
title: "proftpd,vsftpd - cannot list from Internet with PASV"
date: 2008-02-07
forum: Networking &amp; Wireless
---

### Post by einstein on 2008-02-07
Okay, two days of Googling is enough.

I have ran proftpd for years on my LAN and it worked fine - from my LAN.  More recently, I have arranged a dynamic DNS so that I can access my server from the Internet.  HTTP works fine.  LDAP works fine.  FTP works if I ignore PASV command.  I can always login to my FTP server but things hang forever (no timeouts) waiting for the directory listing.  Everything works fine from within my LAN.

The problem seems to be a networking one as I have identical problems with both proftpd and now vsftpd.  Moreover, the problem appears to have something to do with the passive ports.

I have read the threads the forum thinks I should before posting (as well as dozens of Google results) without success.  It is troubling to find three posts that may be about precisely the same problem and that NONE of the three received a single reply..  One of the posts has nothing to do with my question.

[http://ubuntuforums.org/showthread.php?t=570263](http://ubuntuforums.org/showthread.php?t=570263) [no replies]
[http://ubuntuforums.org/showthread.php?t=412885](http://ubuntuforums.org/showthread.php?t=412885) [no solution here]
[http://ubuntuforums.org/showthread.php?t=287031](http://ubuntuforums.org/showthread.php?t=287031) [no replies]
[http://ubuntuforums.org/showthread.php?t=114649](http://ubuntuforums.org/showthread.php?t=114649) [no replies]
[http://ubuntuforums.org/showthread.php?t=101505](http://ubuntuforums.org/showthread.php?t=101505) [has nothing to do with my question]

My hardware arrangement is Internet->DSL modem->DLink DI-824VUP Router->server.

I have:
[LIST]
[*]Forwarded standard FTP ports on my router to my server.
[*]I have specified passive port ranges for either of the ftp servers I have tried and enabled PASV.
[*]I have forwarded the specified port ranges from my router to my server.
[/LIST]

I sure could use and sure would appreciate some help on this.  As long as I am using a FTP client that will ignore PASV, no problem.  But this is not always the case.

Regards,
           Dennis

---

### Post by einstein on 2008-02-08
Solved.  See [http://ubuntuforums.org/showthread.php?t=692355](http://ubuntuforums.org/showthread.php?t=692355)

BTW, it was networking problem but got solved in the server forum.

Dennis

---

