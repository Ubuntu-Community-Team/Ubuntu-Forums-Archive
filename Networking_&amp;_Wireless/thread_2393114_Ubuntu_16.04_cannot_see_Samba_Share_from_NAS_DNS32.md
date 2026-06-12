---
title: "Ubuntu 16.04 cannot see Samba Share from NAS DNS323"
date: 2018-05-29
forum: Networking &amp; Wireless
---

### Post by allwell on 2018-05-29
Hi,

I have migrated to Ubuntu 16.04 from Windows XP SP3.

All is good the only issue is I cannot see my samba shared disk from Dlink DNS323 which I can access via Windows XP.

I have tried smbtree -N and testparm and the troubling issue is I cannot see my DNS323 box from the output of the command.

My DNS323 is running Alt-F firmware RC0.3 which I have enabled samba share and inetd only.

I have also tried smb //192.168.1.169 (which is my DNS323 static ip) and always encountered timeout error (not having having prompt to enter user id and pw).

I can http DNS323 via web browser without issue.

Any help is very much appreciated. If it is required to furnish and diagnostic output kindly guide me via the command to be used i will furnish accordingly.

Thanking your all in advance for your time and help.

Best regards,
Liew

---

### Post by TheFu on 2018-05-30
Install the smbclient package.
Open almost any Linux file browser, enter smb://192.168.1.169/ into the address bar.
Does that work?  I didn't look up the addon package names, but there are some for gvfs.

If the NAS supports NFS, that would likely be a better protocol to use from Linux.

---

### Post by allwell on 2018-06-01
Thank you TheFu for the reply.

smb://192.168.1.169 would loop for sometime then error prompt saying timeout appeared.

Yes the NAS supports NFS i will try the alternative and thank you for the suggestion.

Kind regards.

---

### Post by TheFu on 2018-06-01
I searched the forums for Dlink DNS323 samba issues and found a few over 10 yrs old.  Something about LANMAN authentication.  LANMAN is extremely week.  


sudoedit /etc/samba/smb.conf
Find the [global] section, and insert:
```

max protocol = NT1
client lanman auth = yes
client ntlmv2 auth = no
```

Ouch. NFSv3 only has IP addresses for security, but that would be a little better than LANMAN.

---

