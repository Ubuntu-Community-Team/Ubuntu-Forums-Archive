---
title: "Cannot mount CIFS share with $ character from command line"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by cur8or on 2008-11-26
I have a strange cifs issue - there is a Windows 2003 domain share with my Windows domain home directory that I try to mount on my Intrepid box. 

Share name looks like:   //server/Home$/username

I use the following command to try to mount it:
mount -t cifs -o creds=/username/.filename //server/Home$/username/ /mnt/

and get the error "mount error 13 = Permission denied"

I can mount non-hidden share with same credentials file just fine:
mount -t cifs -o creds=/username/.filename //server/share1/ /mnt/

I can also browse my home share from smbclient, and from Dolphin (where it looks like this: smb://domain%2Fusername@server/Home$/username/)

Anyone know how to fix this? CIFS probably can't parse that $ character correctly. I tried adding \ in front of $, did not make any difference.

When running mount command with --verbose options I can see that it does strip last directory string (username) when it parses the command:
mount.cifs kernel mount options unc=//server\Home$
Which is not going to work since directory listing for that directory is not allowed.

Thanks in advance for your ideas!

---

### Post by felker2 on 2008-11-26
Have you tried putting single quotes (') around the UNC?

Have you tried replacing the $ sign with \044, like  //netbiosname/sharename\044

---

### Post by cur8or on 2008-11-28
Thank for recommendations. Tried single quotes, did not work. 
I just tried \044 to replace $, didn't work either - it converts share\044 to share044 and share\\044 to share
This is probably a bug in mount.cifs.

I can't use prefixpath option either, while something like this works to mount nested 3rd level directory after mounting 2nd level directory:
to mount //server/share1/share2 I'd use
mount -t cifs -o prefixpath=share1 //server/share1/share2/ /mnt/

But that would still pass unc=//server\share1 to mount, which in my case does not work because I don't have permission to mount share1, I  only have permission to mount share2.

What I need to be able to do is to pass 2 levels of directories to unc, which does not seem to be possible with current CIFS implementation.
(while it works fine from Windows).

---

