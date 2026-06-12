---
title: "Lubuntu 14.04 LTS -- Samba updates 18 Apr 2016 -- create problems with gvfs"
date: 2016-04-19
forum: Networking &amp; Wireless
---

### Post by Dr John on 2016-04-19
The automatic updates to Samba that were provided on 18 April 2016 apparently clobber some of the functionality of gvfs.  In particular, the functionality reverts to one in which when trying to connect to a particular CIFS/SMB share using gvfs (no matter how it is done), the resulting behavior is one that asks for the password, but doesn't act on it correctly, then repeatedly asks again for the password.  I found this because I use gigolo to automatically log in to a CIFS/SMB share at login time and, not only did it not log in correctly, but repeatedly asked for my password again.  At first I thought it was a virus, but determined that it was a "feature" of the gvfs logging process.  It's the same using PCManFM, and also using the command line.

A temporary fix is to insert the following into /etc/samba/smb.conf:

# LANMAN fix

client lanman auth = yes
client ntlmv2 auth = no


While this fixes my functionality in gigolo, and it also enables command line login using gvfs, it doesn't solve the problem of not being able to see the CIFS/SMB servers when one uses PCManFM and asks it to explore the Windows network.

I note that while, in the process of updating Samba with the latest updates /etc/samba/smb.conf was changed, the changes had nothing to do with the temporary fix shown above.   A file compare between the original smb.conf and the modified smb.conf shows nothing that would have caused this.

I also note that this bug has existed since at least 2010 (see launchpad bug #510059).  One would think that this issue would have been permanently addressed by now, but apparently a medium priority bug, such as this, gets to live on for quite some time.

Meanwhile, I post this bug here in this forum so that others who have been affected by it can take advantage of the work-around that I have found without having to spend all day on it as I did.

---

### Post by scpatl4now on 2016-04-20
I am having the same basic problem in that I can see windows shares but none of the windows shares see Ubuntu any more. I will try your fix when I get a chance

---

