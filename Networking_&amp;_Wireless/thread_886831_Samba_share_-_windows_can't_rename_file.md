---
title: "Samba share - windows can't rename file"
date: 2008-08-11
forum: Networking &amp; Wireless
---

### Post by lochraven on 2008-08-11
Ok so first off, I'm fairly new to Linux in general, so if I'm doing something totally retarded just tell me and let me know what I should be doing instead.

I have a partition on my linux pc created specifically for sharing media between Ubuntu and my Windows VM. I've created a samba share for it, and I am able to see it in windows: I can browse/rename/add/delete files without any issues. However, some apps (Zune..ahem) try to rename files, it fails.  

So while downloading a song Zune creates a file called ZuneXX.tmp.  Once it's complete it tries to rename the file to the correct mp3.  Here's what FileMon gives me in WinXP:

> 2:39:58 PM	Zune.exe:3272	SET INFORMATION 	Z:\My Music\Zune\Subscription\Okkervil River\Black Sheep Boy (Bonus Tracks)\Zun25.tmp	ACCESS DENIED	FileBasicInformation

Here's the share from /etc/samba/smb.conf:
```
[MediaShare]
path = /media/share
available = yes
browsable = yes
public = yes
writable = yes
create mask = 0775
directory mask = 0775
```

I set the masks just a moment ago to no avail hoping that might work.  Anyone know what the heck I should be doing here?  Thanks in advance.

---

### Post by Iowan on 2008-08-11
Did you restart Samba after changing **smb.conf**?

---

### Post by lochraven on 2008-08-11
> **Iowan said:**
> Did you restart Samba after changing **smb.conf**?
I knew someone was going to ask that...

I think so... I ran:
sudo /etc/init.d/samba restart.

Also, shortly after making this post I ended up having to kill -9 nmbd, and restart it again because it was taking up 100% of one of my cores.  No idea why that happened.

I take it that's all I need to do right?  I haven't actually restarted my workstation.

I just un-installed vmplayer 2.04 and downgraded to 2.03 because I thought I had this all working a few months ago before I upgraded.  Unfortunately that didn't fix anything either.  I also created a new Ubuntu admin user with the same credentials as my WinXP VM. Still same issue.

---

### Post by lochraven on 2008-08-11
Bueller? Anyone?  Am I not using the permissions mask correctly or something?  

Oh well... In the meantime I'm just using 

rename 's/tmp/mp3/' *.tmp

...and then using Mp3Tag to rename all the files from the ID3 tags.  Works well enough - just a pain.  Just in case anyone else runs into something similar.  Doubtful since of course no one in their right mind should be using Zune... but it was free and I'm cheap.

---

### Post by gm.matias on 2010-02-12
I am using VMPlayer and in the configuration I enabled the Share Files options but it did not work for me. I read some more articles and found a good solution that works for me. I put in here: [http://www.gmmatias.com/sharing-a-disk-drive-of-an-ubuntu-host-to-a-guest-windows-on-vmplayer-using-samba-2010-02-12](http://www.gmmatias.com/sharing-a-disk-drive-of-an-ubuntu-host-to-a-guest-windows-on-vmplayer-using-samba-2010-02-12)

Hope it helps.

---

### Post by mistofeles on 2012-02-05
> **gm.matias said:**
> I am using VMPlayer and in the configuration I enabled the Share Files options but it did not work for me. I read some more articles and found a good solution that works for me. I put in here: [http://www.gmmatias.com/sharing-a-disk-drive-of-an-ubuntu-host-to-a-guest-windows-on-vmplayer-using-samba-2010-02-12](http://www.gmmatias.com/sharing-a-disk-drive-of-an-ubuntu-host-to-a-guest-windows-on-vmplayer-using-samba-2010-02-12)

Hope it helps.

Unfortunately it doesn't help. The link doesn't open.

---

