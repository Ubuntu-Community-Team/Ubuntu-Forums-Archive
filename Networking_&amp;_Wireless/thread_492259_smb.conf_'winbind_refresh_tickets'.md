---
title: "smb.conf 'winbind refresh tickets'"
date: 2007-07-04
forum: Networking &amp; Wireless
---

### Post by jonallport on 2007-07-04
Hi guys,

I'm baffled by this one!

I have several linux servers running mostly Ubuntu (EE & FF) and one on SuSE (10.1) acting as fileservers for Windoze clients with Samba/Winbind hanging off a Win2K domain controller.  The 'issue' I have is this:

If I reboot the domain controller (and, let's face it that happens quite often!) then the Ubuntu boxes need Winbindd to restart before any Windows clients can connect to shares.

The SuSE box doesn't have this issue.  The only difference in the config is the presence of 'winbind refresh tickets = yes' in the smb.conf on the SuSE box and not on the Ubuntu boxes.  If I put that dirrective into the smb.conf on the Ubuntu boxes, testparm kicks it out as an unknown directive.  So, the questions are:

1) What does that directive do?
2) Why is it not implemented in the Ubuntu flavour of Samba?

Info:

SuSE samba v 3.0.22-11-SUSE-CODE10
Ubuntu samba v 3.0.22

Thanks in advance for any help you can offer.

J :^)

---

### Post by jonallport on 2007-07-13
Well, I've found the answer to (1):

'winbind refresh tickets' instructs the winbind daemon (winbindd) to update the ticket-granting-ticket (TGT) held with the Kerberos server periodically (every 10 mins).

The question still remains:

2) Why is it not implemented in the Ubuntu flavour of Samba?

Anybody? Please!

---

### Post by crmanski on 2008-01-03
> **jonallport said:**
> Well, I've found the answer to (1):

'winbind refresh tickets' instructs the winbind daemon (winbindd) to update the ticket-granting-ticket (TGT) held with the Kerberos server periodically (every 10 mins).

The question still remains:
2) Why is it not implemented in the Ubuntu flavour of Samba?

Anybody? Please!

I put this in my smb.conf and the testparm did not complain. I am running 3.0.26a from Gutsy though.
winbind refresh tickets = true

---

### Post by jonallport on 2008-01-16
Righty-ho, I'll push the server up from Edgy to Gutsy, then.

Thanks.

---

