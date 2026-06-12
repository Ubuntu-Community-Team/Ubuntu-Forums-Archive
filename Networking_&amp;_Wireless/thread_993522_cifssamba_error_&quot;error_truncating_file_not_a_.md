---
title: "cifs/samba error: &quot;error truncating file: not a directory&quot;"
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by isecore on 2008-11-25
I'm falling out of love with Intrepid. This is just the latest in a long series of deep annoyances.

I mount a number of remote shares using Samba. This is shared from my server via Samba, and is a left-over from when I ran Windows mainly. I have no intention of changing it.

Hardy and anything previously handled things fine. Now, when I try to copy files to the shares (or edit files on the shares) I get the following cryptic messages in Nautilus:

"Error truncating file: Not a directory"

WTF??

I have a number of these in my /etc/fstab. They're all identical except that the sharenames differ. I've censored them but you get the idea.

//server/sharename /media/sharename cifs user,noauto,credentials=/home/isecore/.smbpasswd,iocharset=utf8,file_mode=0644,dir_mode=0755 0 0

Due to some funkiness with my network I mount them using simple mount-commands in /etc/rc.local

---

