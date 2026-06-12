---
title: "Ubuntu Server 10.04 Data Drive"
date: 2010-06-28
forum: New to Ubuntu
---

### Post by tbzep on 2010-06-28
I just finished building a file server with Ubuntu Server 10.04. I used two old hard drives, one for Ubuntu, the other for data.  After wrestling with it for several hours, I got it going and it's been running fine for a couple of days.

I shut it down to move it into its cubby hole and restarted.  Much to my frustration, I got a S.M.A.R.T. notification at boot saying my data drive is bad and I need to replace it immediately.

Assuming I'm not worried about any data saved on the drive, can I just swap in another one without having to change any settings?  I've got another drive laying around.  

What about formatting?  I believe it had WinXP on it at one time, so it should be NTFS, which is needed for the windows share.

Edit: I just noticed the server forum and posted the question there.  I don't see a delete button anywhere.

---

### Post by gzarkadas on 2010-06-29
You may have to change the line in /etc/fstab that mounts the specific disk **if** you used UUID to identify the drive and not a device path (such as /dev/sdb1). This is also true if you will use a different filesystem type than the previous one.

About formatting: You should format the drive to a native linux format such as ext3 or ext4 (my choice).

---

