---
title: "Samba - connect OK via IP, hostname returns not found"
date: 2008-04-17
forum: Networking &amp; Wireless
---

### Post by MikkyX on 2008-04-17
Hi all,
We have a network here with lots of Windows boxes and my personal favourite machine, the Ubuntu box.   It has a share on it for the PHP sites we develop here, which is set up via Samba and allows guest access etc. etc. set up in accordance with this Ubuntu Guide entry:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_share_public_folders_with_read.2Fwrite_permissions_.28Authentication.3DNo.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_share_public_folders_with_read.2Fwrite_permissions_.28Authentication.3DNo.29)

As that URL may give away, we were running Feisty server, and it's been fine for months.

Yesterday I finally got around to upgrading the box to Gutsy via:
do-release-upgrade

The install went fine, no complaints I could see - but suddenly, this morning, the Samba share I'd set up stopped working. If I try to access \\hostname\sharename it doesn't work - Windows either says it cannot find the share on the network, or pops up a username / password box with the username force-set to HOSTNAME/Guest (and greyed out so it can't be changed) and a password box. Nothing works here.

However, if I go to \\ip number\sharename it works perfectly.

Has the Gutsy upgrade done something outside of Samba that I've missed? All help appreciated - thanks! :)

---

### Post by Iowan on 2008-04-17
Verify that the hostname (also in the **smb.conf **file) is still what it was.

---

### Post by MikkyX on 2008-04-17
> **Iowan said:**
> Verify that the hostname (also in the **smb.conf **file) is still what it was.
I've got the workgroup set correctly and the server string left as it's always been but I can't see the actual hostname in the file anywhere......

---

### Post by Iowan on 2008-04-17
I was probably thinking of the server string... but verify that **hostname** returns the right name.

---

### Post by MikkyX on 2008-04-17
> **Iowan said:**
> I was probably thinking of the server string... but verify that **hostname** returns the right name.
If I type "hostname" on the command line it returns the correct hostname.

---

