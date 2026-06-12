---
title: "can't access gusty's nfs exports from solaris"
date: 2008-02-13
forum: Networking &amp; Wireless
---

### Post by mathiraj on 2008-02-13
I have NFS servers running on a solaris box, opensuse as well as gusty.

The situation is from solaris I need to be able to access gusty's nfs exports and vice versa.

I'm able to access the nfs exports of the solaris from gusty and opensuse
Also I'm able to access the nfs exports of opensuse from gusty and solaris

But when access the nfs exports of gusty from solaris, I get "permission denied" error.
(note : From opensuse I'm able to access gusty's nfs exports and from gusty too doing a "ls /net/gusty-hostname/export" works)

Is it a known problem with accessing nfs exports of gusty from solaris box. I use solaris 10u3.

Here are my /etc/exports from both opensuse and gusty

/export *(rw,root_squash,sync,no_subtree_check)
/tmp    *(rw,root_squash,sync,no_subtree_check)

exportfs returns the following on opensuse and gusty

/export         <world>
/tmp            <world>

any additional setup needed to make gusty play nice with solaris with respect to the NFS exports?

I also tried with different gusty's kernels (general, server, rt, etc.,) with no luck

---

