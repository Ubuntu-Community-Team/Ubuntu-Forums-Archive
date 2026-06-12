---
title: "accessing Windows shares from Mythbuntu 9.04"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by nwwoods on 2009-05-16
I did a clean install of Mythbuntu Jaunty on a new system.  All went well, I can connect to the network just fine, TV setup is fine, etc.

I cannot access Windows shares.  It seems as if SMB is not recognized -- Thunar gives me a do-not-enter icon as soon as I type smb: in the address field... Firefox says there is no program that can process the SMB protocol when I try smb://<servername or ip>

Samba and smbclient are installed.  

I installed Netbook Remix on another system and all is well, so presumably there is some package or packages I still need to add?  What gives?

Thanks for any insight.

---

### Post by nwwoods on 2009-05-16
Additional data:
I compared packages with 'smb' between the two systems and they are the same.  So perhaps there is a config setting somewhere I am supposed to make?

Thanks.

---

### Post by wizard10000 on 2009-05-16
> **nwwoods said:**
> Additional data:
I compared packages with 'smb' between the two systems and they are the same.  So perhaps there is a config setting somewhere I am supposed to make?

Thanks.

Compare /etc/samba/smb.conf on both machines - you should see the difference without a whole lot of trouble  :)

Good luck -

---

### Post by nwwoods on 2009-05-16
Thanks Mr. Wizard.  

The only meaningful diffs I noted was MythTV said securty=share and wins support=no which were both commented out in Netbook Remix.  Commented them out but no dice.  Also noted a bunch of authenitcation params in the Netbook Remix version that were not there at all in the MythTV version.  Added them, still no dice.  There is a [printers] section but that's for sharing a locally attached printer with Windows clients if memory serves?

I can see (via ps) two instances of smbd -D running.

Other thoughts?

---

