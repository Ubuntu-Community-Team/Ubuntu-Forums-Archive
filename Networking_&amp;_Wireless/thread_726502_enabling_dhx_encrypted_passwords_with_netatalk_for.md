---
title: "enabling dhx encrypted passwords with netatalk for mac clients"
date: 2008-03-16
forum: Networking &amp; Wireless
---

### Post by analogline on 2008-03-16
I'm trying to set netatalk up on my Ubuntu box so I can use it as a file server for this primarily Mac-populated network (and eventually try and push some people to cheap Linux-based file servers who are on Mac client networks).

The only issue I'm running into is that looking over what the netatalk package installed, and reading the documentation at the netatalk website ([http://netatalk.sourceforge.net](http://netatalk.sourceforge.net)) I'm not finding the "uams_dhx_passwd.so" or "uams_dhx.so" libraries (which are the libraries for Diffie-Hellman key exchange).  There are Kerberos libraries, but I'd like to avoid having to deal with Kerberos on top of everything else if possible.  Am I missing something, or does the Ubuntu version just not include them, and I'll need to compile it from source to get it working right?

Thanks in advance.

---

### Post by Gossar on 2008-03-17
> **analogline said:**
> Am I missing something, or does the Ubuntu version just not include them, and I'll need to compile it from source to get it working right?
Exactly, to use password encryption in netatalk/afpd you'll have to recompile.
for the reason/s (it's a license thing)
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=191790]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=191790")
[http://it.slashdot.org/comments.pl?sid=180016&cid=14905489]("http://it.slashdot.org/comments.pl?sid=180016&cid=14905489")

for the solution
[http://ubuntuforums.org/showthread.php?t=347019]("http://ubuntuforums.org/showthread.php?t=347019")
[http://www.damontimm.com/blog/how-to-install-netatalk-afp-on-ubuntu-with-encrypted-authentication/]("http://www.damontimm.com/blog/how-to-install-netatalk-afp-on-ubuntu-with-encrypted-authentication/")

---

