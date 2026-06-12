---
title: "SMB Large File Transfer"
date: 2007-03-26
forum: Networking &amp; Wireless
---

### Post by tuaris on 2007-03-26
I've noticed this on many different computers at many different environments.  I am connected to a Windows share, I want to upload or download a large file (it's happened with files as small as 10 MB or 30GB).  The transfer begins ok, but somewhere around 30% It stops with an error "Timeout Reached".  The "retry" button is useless.  When I click "Cancel" the window closes.

I have also seen this happen in Suse Linux Enterprise Server 10, except the window does not close.

Also noticed that after this happens, I can no longer access the SMB mounts via the "Network Places" menu, I get "Could not open location 'smb://User@Computer/Share' Unknown error code: 46".  The mounts can only be opened from the desktop or the nautilus sidebar.

---

### Post by bypolar.txt on 2007-04-13
Hey tuaris i noticed the same thing when trying to back up a Gentoo folder under Ubuntu. i think this thread might help

 [http://ubuntuforums.org/showthread.php?t=347430&highlight=nas+mount]("http://ubuntuforums.org/showthread.php?t=347430&highlight=nas+mount"). 

But the way i solved it was by ripping the Gentoo hdd out of my Ubuntu box and dropping it in a win2k system. and mounting Gentoo using a Reiserfs driver for windows. That way was consistent even through a wireless connection and an 18 hour transfer...

---

### Post by EmmEff on 2007-04-13
Try mounting the filesystem manually from the shell (using mount -t cifs...) and doing the same copy.  I'm sure you'll find that it succeeds.

I transfer multiple gigs a day in both directions (Linux to Windows and visa-versa) everyday without any issue, but I don't do it through Nautilus.

---

### Post by WetWired on 2007-05-05
Has anyone found a fix for this problem? I'm having the same problem, and I'd rather it just work than have to manually mount it every time.

---

### Post by dmizer on 2007-05-06
> **WetWired said:**
> Has anyone found a fix for this problem? I'm having the same problem, and I'd rather it just work than have to manually mount it every time.

you can configure fstab to mount your share for you automatically.  i've written directions here: [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534) follow the directions listed under "permanent mount" 

mounting using cifs and fstab allows for the following advanced features you cannot achieve with mounting your share in nautilus (places > connect to server)
> ability to transfer files larger than 2 gig.
> better network stability and speed
> direct access to your network share from applications (eg: amaroc)
> improved performance with non-roman characters in file names.

this is not a comprehensive list.

---

