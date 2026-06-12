---
title: "Best Method for Secure File Transfer?"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by IMSargon on 2008-10-31
SFTP - 2.6MB/s for large file, 2.6MB/s for many small files
SCP - 11.5MB/s for large file, can't do many small files at once
SSHFS - 9.5MB/s for large file, 6.5MB/s for many small files

Clearly, some methods of file transfer are faster than others. SFTP integrates very nicely with my workflow, as I can mount a folder right from Gnome and manage files as I would locally - except, more slowly. SCP goes about as quickly as my connection can handle, but I can't seem to find any way to use it besides copying files, one at a time, from the command line.

Are there better ways to use SCP? Are there other protocols with as strong security? 

Features I want:
-Public Key Authentication
-Ability to manage files via Nautilus
-Strong encryption during transfer
-Reasonably fast
-User friendly once implemented

---

### Post by tgalati4 on 2008-10-31
sudo sshfs you@yourremotemachine:remotedirectory localmountpointthatalreadyexists

cat /etc/mtab

Make note of the new mount details and add them in /etc/fstab

sudo nano /etc/fstab

---

### Post by IMSargon on 2008-11-10
How's the URI version of sshfs supposed to be formatted? I had it working before, but now I can't seem to remember. I'd like to be able to mount from GNOME (Places -> Connect to Server... -> Custom Location). It works fine from the command line.

sshfs://user@hostcompy/home/user

something like that. Not quite, though. I keep getting "location is not mountable"



Also, could someone explain why SSHFS is faster than SFTP?

---

