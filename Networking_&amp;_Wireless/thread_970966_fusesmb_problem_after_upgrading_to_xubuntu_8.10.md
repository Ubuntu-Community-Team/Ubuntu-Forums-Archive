---
title: "fusesmb problem after upgrading to xubuntu 8.10"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by benma on 2008-11-04
Hello.
After upgrading to 8.10 my samba mount crashes after several seconds. trying reaccess the mount gives: Transport endpoint is not connected. umount and running fusesmb /home/.../network mounts again for several seconds and then crashes again.

Please help!


Never had this problem in hardy.

running ls -l gives:

ls: cannot access network: Transport endpoint is not connected
total 48
.
.censored
.
d????????? ? ? ? ? ? network
.
.censored

while running sudo ls -l gives:

ls: cannot access network: Permission denied
total 48
.
.censored
.
d????????? ? ? ? ? ? network
.
.censored

BTW in hardy i followed the tutorial at:
[http://ubuntuforums.org/showthread.php?t=304131](http://ubuntuforums.org/showthread.php?t=304131)
to setup fusesmb.

---

### Post by benma on 2008-11-04
It seems it's a Thunar problem, because if i don't open Thunar and browse /media/network from CLI, nothing happens - fusesmb stays connected.

---

### Post by benma on 2008-11-04
It's an even Debian Lenny problem inherited by ubuntu in multiverse/uniberse.

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=497572](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=497572)


SOLUTION:
Untill fusesmb newest version is fixed:
In the manual don't use fusesmb. install smbnetfs package instead.
All the other directives are fine.

---

### Post by martinbaselier on 2008-11-21
I've been working all evening to fix this problem. And it finally seems to work. At least I am able to access the network, without being thrown out almost immediately. Right now I'm copying a few GB over it, as I was wanted to do in the first place. 

Here's the fix:
I've found the solution in the topic below, although the solution offered there did not work as it was put there, but with a bit of creativity I've changed it to work for me. 
[https://bugs.launchpad.net/ubuntu/+source/fusesmb/+bug/198351](https://bugs.launchpad.net/ubuntu/+source/fusesmb/+bug/198351)
Thank you dmik for showing me the solution.

The problem seems to be related to the new version of libsmbclient. 

Make sure fusesmb is not started yet otherwise you need a reboot. 
*I found this out the hard way*
Step 1:
As suggested there i've downloaded the hardy version of it from 
[http://packages.ubuntu.com/hardy-updates/libsmbclient]("http://packages.ubuntu.com/hardy-updates/libsmbclient") and unpacked it with archive manager and then extracted data.tar.gz

Step 2:
Then I started thunar in root-mode. In the terminal type:
$ sudo thunar 
went to the directory where I downloaded the deb-file, and from there to 
libsmbclient_3.0.28a-1ubuntu4.7_i386/usr/lib
I copied both files and then went to /usr/lib and pasted them there. 

Step 3:
now close thunar and you're back in the terminal. 
$ sudo ldconfig
and now it should be fixed and you can start fusesmb. 

You might check:
$ ls ~/.smb 
to see if it show the following files:
fusesmb.cache  fusesmb.conf

one of the problems was that when it disconnected it showed a file called fusesmb.cached.pid for a very long time. So when i restarted fuse by pkill
fusesmb an starting it again, it either showed no files or I needed to reboot to see the network again for a few seconds, O happy me. 

How many times have I deleted those files and rebooted today. Just to see the problem was still not solved. 

While writing this post I'v copied 2.6 GB of data so it seems to work :-)

by the way the thing not working from the post was using cp to copy the files as suggested by Dmik in the post. When I did that libsmbclient.so.0 was no longer a symbolic link and ldconfig would not work and neither the fix. I would be neater to make the backup as suggested there. But reinstalling smbclient from deb source would also fix that. So why bother.

just to confirm after 3 days my network is still working perfectly.

---

