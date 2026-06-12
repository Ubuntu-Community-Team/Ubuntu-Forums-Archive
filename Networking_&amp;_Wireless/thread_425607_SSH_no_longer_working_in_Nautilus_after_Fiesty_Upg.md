---
title: "SSH no longer working in Nautilus after Fiesty Upgrade"
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by cephlon on 2007-04-27
I just did a fresh install of fiesty. 
I can not get nautilus to display my ssh folders. I keep getting the following error:

Nautiusl cannot display "ssh://root@1.1.1.1:22/".
Please select another viewer and try again. 

winSCP works fine in windows. And Nautilus was working just fine in dapper.

---

### Post by Vil on 2007-04-30
I am getting the same problem. If I try to connect to my 6.10 server from my 7.04 laptop, I get the message:
> Nautilus cannot display "ssh://<username>@abc.def.ghi.jkl".
Please select another viewer and try again.

I can connect from 7.04 -> 7.04 (I tested this by doing ssh://<username>@localhost). This indicates to me that the issue is related to trying to connect from 7.04 to a previous version of Ubuntu, but only in Nautilus have I seen this issue. I can connect via SSH from the command line with no issues (ssh <username>@<server>).

I also know that I can connect to the server from a different 6.10 box.

---

### Post by cephlon on 2007-05-01
I don't have another computer running Ubuntu, I am trying to connect to a CentOS machine. I can also connect no problem from the command line. I found a temp fix using sshfs, but I really would prefer to just use Nautilus.

---

### Post by Erlander on 2007-05-02
Works for me in Feisty.

I just installed the SSH Server and SSH Client and off it went.

Rob

---

### Post by gwm on 2007-06-04
Same problem - now fixed. I wrote a whole essay about it here:

[http://ubuntuforums.org/showthread.php?p=2778127#post2778127](http://ubuntuforums.org/showthread.php?p=2778127#post2778127)

:popcorn:

---

