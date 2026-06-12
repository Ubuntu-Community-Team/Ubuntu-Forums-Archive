---
title: "Did smbfs do something to my directory?"
date: 2007-05-07
forum: Networking &amp; Wireless
---

### Post by aleska on 2007-05-07
Don't know if this is really a networking question or other.  
I had set up a mounted network attached storage device, server via samba.  It was working well and without problem.  I was using smbfs and had my setup in /etc/fstab.  Turns out I should have been using cifs anyway, but that's another story.
So, last night, I was following a script to batch convert ogg music files on the mounted NAS to mp3.  It was working great when I when off to bed.
In the morning I came back to find out that somewhere along the line samba crapped out or something.  I found the following in dmesg
[INDENT][ 3524.196000] smb_lookup: find //Music failed, error=-5
[ 3554.196000] smb_lookup: find //Music failed, error=-5
[ 3584.200000] smb_lookup: find //Music failed, error=-5
[ 3614.200000] smb_lookup: find //Music failed, error=-5
[ 3614.860000] smbfs: Unrecognized mount option cp850
[ 3644.200000] smb_lookup: find //Music failed, error=-5
[ 3674.200000] smb_lookup: find //Music failed, error=-5
[ 3704.204000] smb_lookup: find //Music failed, error=-5
[ 3734.204000] smb_lookup: find //Music failed, error=-5
[ 3735.312000] smb_lookup: find //Music failed, error=-5
[ 3737.200000] smb_lookup: find //Music failed, error=-5
[ 3788.996000] smb_lookup: find //Music failed, error=-5
[/INDENT]
Anyway, so I have been able to mount again, this time using cifs properly, rather than smbfs; however, I have to do it to a new directory.  For some reason it won't allow me to mount to that old directory.  Even after removing the reference to the old local directory in fstab, and restarting, it seems the the local directory is hosed.  List (ls) shows it is there when I ls from command line, but it doesn't even appear in Konqueror.  Also, I've tried removing it, with "rm" "rm -d", and both bomb saying it can't because it's a directory.  I've tried "rmdir" but that comes back saying "rmdir: ls_share: Device or resource busy".
Any ideas on what I can and should do here?  TIA

---

### Post by dmizer on 2007-05-08
reboot your remote server.  your directory should be fine, but your server still thinks that you're attached.  there's probably a less "brute force" fix for this, but it's probably the quickest and easiest.

---

### Post by aleska on 2007-05-08
Thanks dmizer!  I'll try that when I get back home.

---

