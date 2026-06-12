---
title: "alien error 127"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by ibelton on 2009-12-22
I am having problems running alien to make a deb package from an rpm package.
 
I am typing
 
sudo alien iprint.rpm
 
I see:
 
error: incorrect format: unknown tag
Warning: Skipping conversion of scripts in package: iprint: postinst postrm
Warning: Use the --scripts parameter to include the scripts
Packkge build failed: Here's the log:
dh_testdir
make : dh-testdir:Command not found
make: *** [build] Error 127
find: 'iprint': no such file or directory
 
I am trying to create a deb file so I can install the novell iprint client for linux.
 
Any help greatly appreciated.
 
Cheerz
IanB

---

### Post by howefield on 2009-12-22
The command used here might help. (your error is telling you to use the --scripts parameter)


[http://www.novell.com/communities/node/4208/using-iprint-with-ubuntu](http://www.novell.com/communities/node/4208/using-iprint-with-ubuntu)

---

### Post by ibelton on 2009-12-22
> **howefield said:**
> The command used here might help. (your error is telling you to use the --scripts parameter)
 
 
[http://www.novell.com/communities/node/4208/using-iprint-with-ubuntu](http://www.novell.com/communities/node/4208/using-iprint-with-ubuntu)
 
 
Thanks for the pointer.
 
I get the same error when I run:
 
sudo alien -d --scripts novell-iprint-xclient.i586.rpm
 
:O(
 
Cheerz
IanB

---

### Post by ibelton on 2009-12-23
> **ibelton said:**
> Thanks for the pointer.
 
I get the same error when I run:
 
sudo alien -d --scripts novell-iprint-xclient.i586.rpm
 
:O(
 
Cheerz
IanB
 
 
I worked around the problem by installing alien on a SUSE linux workstation and the .deb package was created no problems.
 
Cheerz
IanB

---

### Post by Bergpartisan on 2010-01-06
> **ibelton said:**
> I worked around the problem by installing alien on a SUSE linux workstation and the .deb package was created no problems.
 
Cheerz
IanB

Hi ibelton,
I do not have SUSE and I like to ask you if I can get your .deb package to install iprint on my Ubuntu. This would help me a lot, thanks!

---

### Post by ibelton on 2010-01-07
> **Bergpartisan said:**
> Hi ibelton,
I do not have SUSE and I like to ask you if I can get your .deb package to install iprint on my Ubuntu. This would help me a lot, thanks!
 
Yes it did install after conversion.  I am having an issue with the iprint client - it was generating invalid syntax errors during installation of printers  - I have been told I need to use v5 of the linux client - which I am about to convert to a deb package and try again....
 
Regards
IanB

---

