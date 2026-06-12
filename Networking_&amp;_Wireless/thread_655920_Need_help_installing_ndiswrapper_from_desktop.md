---
title: "Need help installing ndiswrapper from desktop"
date: 2008-01-01
forum: Networking &amp; Wireless
---

### Post by Pointswest on 2008-01-01
I have been trying to get my airlink 101 wireless USB adapter to work with ndiswrapper and the win drivers but none of the command lines I seem to use have worked.  I have managed to get the Ndiswrapper to the desktop but dont know how to use the commands to open it and install the win drivers.  

Any help with this would be appreciated.  I have been trying suggestions from lots of posts the last couple of months but I always get stuck on the first or second command.  I must be leaving out something in the command lines.  Thank you for any assistance.
I don't have easy access to the internet, so if this can be done from the desktop it would really help. I have really struggled to get this far. 

Thanks again.

Pointswest

Ubuntu 7.10

---

### Post by mouseboyx on 2008-01-02
What don't you understand?

First you type ```
ndiswrapper -i file.inf
```

the -i meaning input file
the file.inf is the windows driver usually found on a CD that came with your wireless device.

read everything carefully in this if you already havent:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by Pointswest on 2008-01-02
I used the command 'ndiswrapper -i file.inf' but it said ndiswrapper is not installed.  Another message said to use 'sudo apt-get install ndiswrapper-common.  Used this command and the 7.10 disk.  The last message on the screen said unpacking and setting up.

---

