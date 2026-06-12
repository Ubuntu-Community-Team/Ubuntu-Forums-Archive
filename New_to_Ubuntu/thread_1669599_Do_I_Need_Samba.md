---
title: "Do I Need Samba?"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by KlytusLord on 2011-01-17
Hello,

I have been doing research on networking with Ubuntu, and everything I have found refers to "Windows Shares" and the use of Samba.

However, I am just want to share folders between my Ubuntu desktop (version 9.04) and my Ubuntu laptop (version 10.04).

I can do this right now using the Samba/Windows Share method, but compared to the speed at which Windows machines access each other, my two Ubuntu machines are very, very slow in displaying the directory structure. Moving files is fine in terms of speed; the slow part is when they are retrieving the file list from a remote computer.

In Windows (seven and server) browsing the Ubuntu machines is very fast; just not the other way around. So, is there some native way for two Ubuntu computers to network with the same speed and performance that Windows machines do with each other?

It does not matter to me if the Ubuntu machines lose the ability to communicate with the Windows machines. If I can get fast browsing between the two, I'll be happy. 

Thanks for the help!

---

### Post by bodhi.zazen on 2011-01-17
You can share file in many ways.

An alternate to samba is nfs.

You can also use ssh (scp and sshfs).

Or, on a LAN, FTP or http (http is one way).

I would start with nfs.

---

### Post by KlytusLord on 2011-01-18
Thanks for the help.

Got everything working nicely using SSH.

---

