---
title: "OS X Feisty File sharing"
date: 2007-07-06
forum: Networking &amp; Wireless
---

### Post by Mantis2600 on 2007-07-06
I just got a shiny new macbook, and I need to pull some files over from my Ubuntu box.   I don't know where to begin and my google/forum searching seems to be in vain.  My files are currently in my home directory on my linux box, and I need to get them to the macbook.  Help would be greatly appreciated!

---

### Post by dougfractal on 2007-07-06
GUI  : fuse/sshf     [http://www.ubuntux.org/fuse-sshfs](http://www.ubuntux.org/fuse-sshfs)
CLI :  scp                  example$  scp -r /home/[ubuntu]/[folder] [user]@[macboc]:/Users/[user]/

ssh enabled on mac networking   and ubuntu

Install
$ sudo apt-get install sshfs
$ sudo adduser yourlocalusername fuse
(log out and back in so that it recognizes me as a member of the group "fuse")

Mounting is as easy as:
$ sshfs yourremoteusername@remotehost: mountpoint

To unmount:
$ fusermount -u mountpoint

---

