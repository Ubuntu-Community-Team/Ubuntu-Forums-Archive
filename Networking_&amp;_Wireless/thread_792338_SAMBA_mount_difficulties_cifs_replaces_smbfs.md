---
title: "SAMBA mount difficulties: cifs replaces smbfs"
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by TonyS on 2008-05-12
Gidday all,

When I upgraded my workstation from Gutsy to Hardy all my fstab-mounted SAMBA shares went peculiar... they seemed to mount, but with very strange permissions problems, such that they either wouldn't display any contents at all, or would with most things locked.

I *think* this is due to smbfs being depreciated in favour of cifs... however, installing smbfs didn't improve things, so my theory is shakey!

I therefore have two questions.

First, what is the recommended manner to permanently mount SAMBA shares in Hardy? Using the "Connect to Server..." option works fine but needs to be redone on every reboot (unappealing with half a dozen shares!).

Second, assuming editing fstab is still the best way, how do I revise this old fstab entry to use cifs rather than smbfs?

//192.168.0.10/guide    /media/guide smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0


Incidentally I've seen a number of people on the forums who seem to have hit the same rock, with smbfs disappearing. Is anyone producing an "Unofficial Guide" for Hardy, to help us lower-order geeks get our LANs working?

THANKS ALL!

Tony

---

