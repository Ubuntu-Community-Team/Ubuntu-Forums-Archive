---
title: "filesystem on nfs-client only sees 16 of 23 groups"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by FrankSchubert on 2007-05-04
Hi,

I stumbled upon a problem when i migrated some of the system groups into our LDAP-Server.

As I reached **>16** groups that a user is assigned to, the group-permissions don't aply anymore on nfs-mounted filesystem.

I can "see" that the user belongs to the group with
*getent <username>*

But when I try to change into the directory (0750) I get *"permission denied"*.

When I log into the nfs-server, *su* to the user, then I can access the files and directories.

This seems a known problem (to the samba guys for example).
Simo Sorce replied to a problem report found in google groups:

############
[I]> I also thought it might have something to do with nested groups, but
> even simple groups with only users as members exhibit the failure
> over NFS.   I have had the thought that it could be the length of
> some of the groupnames, as some of them are pretty long:  the longest
> is 64 bytes.  The one I did most testing with is only 10 bytes long, however.

The NFS protocol limits the number of groups per user to 16 and truncate
all others, so you are not really able to tell the server you are in
group #17 or #18 and so on. I am 99.9% sure this is the problem you are
experiencing.

That's why approximately you can have it working with older groups as
they are probably just reported first and result in the first 16.

Simo.

-- 
Simo Sorce
Samba Team GPL Compliance Officer
email: i...@samba.org
[http://samba.org](http://samba.org)[/I]
################
 
NeilBrown sent a patch wich seems to solve this problem the right way:
[[PATCH 004 of 4] knfsd: Allow the server to provide a gid list when using AUTH_UNIX]("http://thread.gmane.org/gmane.linux.kernel/492274/focus=492276")

Now my questions:
a) Does anyone know a workaround without modifying the kernel?
b) Is the patch from NeilBrown applied to the default kernel in feisty?
[INDENT]b.1) How can I check for myself that the patch is already applied in feisty?[/INDENT]

Regards,
Frank

---

