---
title: "Admin as SMB user"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by jkurtisr32 on 2011-06-10
Hello,

I have my samba server working very well except for one issue. I cannot seem to get the smbpasswd profile to stick when using the admin username.

As with all of my other smb users, I did the following:
```
sudo smbpasswd -a kurtis
```
I then enter my new password (not the same as I use to log in), and the profile works well. I can access shares using my desired credentials.

But once I reset the server, the credentials do not work until I repeat the above code. Any ideas on how to make the user profile stick?

Thanks,
Kurtis

---

### Post by kjuergen on 2011-06-10
Samba and ubuntu have never matched. The config files are spread all over and conflicting and the default settings are pure nonsense. What you do with the command line gets over-written at boot from somewhere else (can't recall from what). You have to make the change at all places to prevent that.
All I hope for is that I don't have to set it up again soon which is why my server stays on LTS till the last minute and if they still have that problem I'll go Scientific Linux.

---

### Post by jkurtisr32 on 2011-06-10
Thanks for the reply.

I just found something that I hate:
I rebooted, and the the smb username, kurtis, is still there, although the newPassword I set for my user, kurtis, doesn't work (entirely). I changed my fstab on my client machine so that for the FIRST mount (there are three), it authenticates with my actual user password for kurtis (which is root), while the other two continue to use newPassword. All three mounts work when I mount -a. FFFFUUUUUUUUUU, samba!!!!

-Kurtis

---

