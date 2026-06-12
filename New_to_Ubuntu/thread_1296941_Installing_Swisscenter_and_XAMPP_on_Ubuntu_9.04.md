---
title: "Installing Swisscenter and XAMPP on Ubuntu 9.04"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by hugha on 2009-10-21
I am trying to install XAMPP, as part of a process to install  and use Swiss Center.  After downloading XAMPP to my desk top I am unable to extract as directed from the XAMPP website. Here's what I tried.

 I completely reinstalled Ubuntu 9.04. (Stand alone not dual install - Intel box)   As per the instruction at XAMPP website for Linux downloaded xampp-linux-1.7.2.tar.gz to my desktop    /home/hugha/Desktop.

AT this point I was a little confused as to terminology Linux shell versus terminal. After downloading simply type in the following commands:

1. Go to a Linux shell and login as the system administrator root:

su

2. Extract the downloaded archive file to /opt:

tar xvfz xampp-linux-1.7.2.tar.gz -C /opt

I then tried su and then sudo su   still not extracting

hugha@hugha-desktop:~$ su
Password:
su: Authentication failure
hugha@hugha-desktop:~$ sudo su
[sudo] password for hugha:
root@hugha-desktop:/home/hugha# tar xvfz xampp-linux-1.7.2.tar.gz -C /opt
tar: xampp-linux-1.7.2.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
root@hugha-desktop:/home/hugha# sudo tar xvfz xampp-linux-1.7.2.tar.gz -C /opt
tar: xampp-linux-1.7.2.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
root@hugha-desktop:/home/hugha#

There has been some mentioned of access permission for various folders, etc...  As a newbie, if this one possible issue, I could use guidance or direction to guidance on terminology and procedures for setting up permissions or access to folders (ie: read, write,  ...)

I'm sure its something simple but...What am I doing wrong?

Hugh

---

### Post by elvisd on 2009-10-21
the problem is that you try to extract from the wrong directory
you are in /home/hugha but the file is in /home/hugha/Desktop

and you can follow every step wuthout doing a
sudo su

simply from terminal:
```
cd /home/hugha/Desktop
```
```
sudo tar xvzf xampp-linux-1.7.2.tar.gz -C /opt
```

this should extract the entire content of the compressed file to /opt

for setting read/write permissions on folder please check chmod manual
```
man chmod
```
and chown
```
man chown
```

---

### Post by elvisd on 2009-10-21
some links

[http://sudocode.blogspot.com/2009/01/installing-swisscenter-on-ubuntu-server.html](http://sudocode.blogspot.com/2009/01/installing-swisscenter-on-ubuntu-server.html)

[http://ubuntuforums.org/showthread.php?t=223410](http://ubuntuforums.org/showthread.php?t=223410)

hope this helps

---

