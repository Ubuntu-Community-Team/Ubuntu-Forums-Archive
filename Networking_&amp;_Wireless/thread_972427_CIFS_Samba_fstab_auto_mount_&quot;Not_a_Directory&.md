---
title: "CIFS Samba fstab auto mount &quot;Not a Directory&quot; on file save"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by nexusnode on 2008-11-05
Hey All!

Firstly I would like to thank anyone who reads and replies to this thread, all help is greatly appreciated.

The problem I am experiencing is a strange one and there is about two references to it on a Google search and I have to admit they wern't very useful.

Essentially I have an Ubuntu file server with cifs sharing a few directories, a couple of which I have entries in my fstab to mount automatically on boot.  The entries in the fstab were set up with the guide of [this]("http://ubuntuforums.org/showthread.php?t=283131") thread.

I have implemented [this]("http://www.jejik.com/articles/2007/07/automatically_mounting_and_unmounting_samba_windows_shares_with_cifs/") method of automatically unmounting the shares as I was having issues with the machine hanging at shutdown.  This information is just for completion as I do not believe it has any impact on this problem.

And finally... the problem.  The shares appear to mount correctly and I can copy files to them and open files and read them.  However when I come to open a file in gedit, edit it and save it back to the share I get an error message.  The message reads:

> Could not save the file /media/files/example.txt

Unexpected Error: Not a Directory

If the shares are unmounted and I navigate to the samba file share via the "Connect to Server" feature the problems go away.

I also am unable to play music files via Amarok that are stored on these samba shares.

Sadly I am not much of a linux guru but I am trying.  So if any of you brainy people out there could even point me in the right direction it would be great.  Thanks!

---

### Post by nexusnode on 2008-11-06
*bump*

I still haven't been able to find much on this issue - please someone help!

---

### Post by nexusnode on 2008-11-06
For those who have seen this post and not found a solution - I have found one from another post:

[http://ubuntuforums.org/showthread.php?p=6118083](http://ubuntuforums.org/showthread.php?p=6118083)

---

