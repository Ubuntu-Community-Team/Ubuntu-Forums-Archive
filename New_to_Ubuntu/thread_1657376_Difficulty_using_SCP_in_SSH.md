---
title: "Difficulty using SCP in SSH"
date: 2011-01-01
forum: New to Ubuntu
---

### Post by amylase on 2011-01-01
Hi, my goal is to send test.tgz which is located on John's computer under /home/john/iphone
over to
John's iphone under the directory
/var/root/Media

John's Ubuntu machine is the local machine. 
John's iphone is the remote machine.
John's iphone IP is 192.168.1.64

I have no problem sending file from Windows machine to the iphone using WinSCP. But when I try to achieve the same using Ubuntu commandline using SSH and SCP, I get the final error message of: No such file or directory.

I went through the lines half a dozen times and cannot see any mistakes. Please tell me why the file is not going through thanks.



john@Ubuntu-EeePC:~/iphone$ ls
gcc-4.0.1-iphone-1.tgz test.tgz

john@Ubuntu-EeePC:~/iphone$ hostname
Ubuntu-EeePC

john@Ubuntu-EeePC:~/iphone$ pwd
/home/john/iphone

john@Ubuntu-EeePC:~/iphone$ ssh root@192.168.1.64
root@192.168.1.64's password:
johns-iPhone:~ root# ls
Library/ Media/

johns-iPhone:~ root# pwd
/var/root

johns-iPhone:~ root# cd Media
johns-iPhone:~/Media root# pwd
/var/root/Media

johns-iPhone:~/Media root# scp /home/john/iphone/test.tgz root@192.168.1.64:/var/root/Media/test.t…
root@192.168.1.64's password:
/home/john/iphone/test.tgz: No such file or directory
johns-iPhone:~/Media root#

:confused:

Thanks.

---

### Post by MrWestwood on 2011-01-01
You're running the command from the iphone shell. Shouldn't you be running it from John's shell? Don't ssh into the iphone first. At the moment it looks like you're telling scp to copy the file from the iphone to the iphone.

john@Ubuntu-EeePC:~$ scp /home/john/iphone/test.tgz root@192.168.1.64:/var/root/Media/test.t…

I think.

---

### Post by Jlayman on 2011-01-01
Agreed with MrWestwood

---

