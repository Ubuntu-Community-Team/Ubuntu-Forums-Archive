---
title: "Version and Computer details"
date: 2011-03-13
forum: New to Ubuntu
---

### Post by TheHappyH on 2011-03-13
Hi All 
I am sure that if i search long enough i will find the answers to this question
What i want to do is find out the version of ubuntu that i am running and my computer specs so that when i ask the question about why is my scan not working I can provide reasonable answers. Printer/ scan is a Brother MFC-J615W prints a treat but I can't scan
the happy H

---

### Post by HermanAB on 2011-03-13
Howdy,

The command uname will tell you the kernel version, then you got to look at the release notes to see what version of Ubuntu that was:
$ uname -a

---

### Post by sanderj on 2011-03-13
It's in System -> Administration -> System Monitor, under the tab "System".

And it's also in the file /etc/lsb-release

---

### Post by TheHappyH on 2011-03-13
thank you for your response it answered my first ? so now i can Get on to 2nd thanks

---

### Post by TheHappyH on 2011-03-13
thanks for your response
 it worked now I can ask the ? I wanted

---

### Post by ktmom on 2011-03-16
I don't see any other posts by you, so I wonder if your question regarding scanning from the MFC-J615w is still open. 

There are additional drivers you need to scan from the J615w.  Reference this [thread]("http://ubuntuforums.org/showthread.php?t=1340908") and make sure your use the scanner driver for **brscan3 models**.  You can find the drivers at [Brother's website]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html").

---

