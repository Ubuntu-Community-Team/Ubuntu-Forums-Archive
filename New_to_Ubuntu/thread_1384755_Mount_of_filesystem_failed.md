---
title: "Mount of filesystem failed"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by SwatKat on 2010-01-18
Hi,
So, here's the story. 
I was downloading some videos today- 2 videos simultaneously about 190 mb each ( I think). When I tried to download more, I got an error message which I don't remember very well, but had something to do with not being able to save the video at some location ( I think it asked to check its capacity. I'm not sure, really. It was a 2 line message). All I remember is that the location ended with a .bin .
So I thought  it must be a memory problem ,waited for the videos to finish downloading and rebooted.

Upon reboot, it went to disk check and I got this message

```
Mount of filesystem failed
A maintainence shell will now be started
CONTROL D will now terminate this shell and retry
```I pressed control D and got this

```
root@swat-desktop:~#exit
mountall start / starting
fsck from util-linux-ng 2.16
swapon : /dev/disk/by UUID/2ec0ada-3dea44ad-a6 c0-406b9410840:swapon FAILED:Device or resource busy
mountall : swapon / dev/disk/by UUID/2ec0ada-3dea44ad-a6c0-406b9410840[1132] terminated with status 255
mountall : problem activating swap :  dev/disk/by UUID/2ec0ada-3dea44ad-a6c0-406b9410840

/dev/sda 10 : Superblock last write time is in the future( by less than a day, probably due to bad system clock boot). FIXED

/dev/sda10 contains a filesystem with errors, check forced.

/dev/sda10 : Inodes that were a part of a corrupted orphan  linked list found.

/dev/sda10 :Unexpected inconsistency:Run fsck manually(i.e without -a or -p options)

mountall: fsck / [1131] Terminated with status 4

mountall :Filesystem has errors :/

init : mountall main process(1130) terminated with status 3

Mount of filesystem failed
A maintainence shell will now be started
CONTROL D will now terminate this shell and retry

```I had to write that whole thing down and then type it out, so there might be a few typos and syntax errors.

Anybody know what I should do now?
Any help is greatly appreciated, thanks.

---

### Post by SwatKat on 2010-01-18
Oh, I forgot to mention that simple applications like Htop and CheckGmail stopped working, which was another reason I rebooted. Surprisingly enough, firefox and opera had no problems whatsoever.



EDIT:Ah, nevermind.  fsck in the recovery shell fixed it.

---

