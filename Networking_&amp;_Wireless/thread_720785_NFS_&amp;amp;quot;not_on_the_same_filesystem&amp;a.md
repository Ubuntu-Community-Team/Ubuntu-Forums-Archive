---
title: "NFS &amp;amp;quot;not on the same filesystem&amp;amp;quot;"
date: 2008-03-10
forum: Networking &amp; Wireless
---

### Post by dgrafix on 2008-03-10
Why am i getting this message when trying to delete files?

---

### Post by Eiríkr on 2008-03-10
Is there any chance the NFS share in question originates on a different machine than the NFS server you're connecting to?  It's possible to re-share NFS shares, and I recall reading that this requires certain special considerations.

---

### Post by dgrafix on 2008-03-10
They were copied to my fileserver from a backup (from my old server)
I have 4 PCs connected to this fileserver that all need full RW access.

So, how can i make them "belong" to the new one then?

---

### Post by Eiríkr on 2008-03-10
By "copied" I assume you mean that the relevant files now reside on the hard drive of the NFS server machine, in which case re-sharing doesn't sound like the issue.  Re-sharing is when files on machine A are shared via NFS to machine B, which then reshares some or all of the same NFS-mounted directories again via NFS.  

Depending on how the backup was restored though, it's possible that UIDs/GIDs and / or permissions no longer match with the server machine configuation.  I've never run into this particular NFS error so I'm not sure if this is relevant, but just in case I'd suggest running [font=courier]ls -l[/font] and [font=courier]ls -ln[/font] on the shared directory and make sure the usernames / groups and UIDs / GIDs match with what you expect.

---

### Post by dgrafix on 2008-03-10
yes they do.

Ive even tried chowning -R / 777  them all

---

### Post by Eiríkr on 2008-03-10
Then I'm a bit puzzled.  Can the troublesome files be deleted locally, after logging in (or ssh-ing in) to the server machine?  If so, would you mind posting your /etc/exports file?

---

### Post by dgrafix on 2008-03-10
Ok Sorted it i think.

It was permissions after all.

---

### Post by Eiríkr on 2008-03-10
Cool, glad to hear things are working.  If this issue is fixed for you then, please remember to mark the thread as SOLVED in the Thread Tools dropdown at the top of the page.

Cheers,

Eiríkr

---

### Post by dgrafix on 2008-03-11
Will do, i just wanted to be sure. It appears the parent folder (in this case the home folder hosting the shares needs to have others - all access, 774 permissions, even though the shares themselves only need the owner and group 770 permissions :confused: (serveradminaccount and the group of fileaccess which allowed connecting users belong to)

---

### Post by Eiríkr on 2008-03-11
Very strange indeed.  What version of NFS sharing are you using, 2, 3, or 4?  And presumably you're using the nfs-kernel-server default Ubuntu package?  In my case, I'm using the alternate nfs-user-server package to allow for UID / GID mapping, which seems to default to v3 sharing, and the home folder hosting the shares is in mode 755.  Maybe there's something about "other" read permissions that's the key here?  Curious, whatever the case.

Cheers,

Eiríkr

---

### Post by dgrafix on 2008-03-11
No idea, ive got Ubuntu 7.10 and simply did apt-get install nfs-kernel-server whatever that brings down is what i got.


I think the problem is that the user who 'owns' the fileshares is the server's admin account,  not the same as the users who connects to it. 

I have a group, lets call it 'fileaccess' for remote users who has full RW group permissions on the shares (770). This folder is in /home/adminsaccount/fileaccess

However it appears that the home folder for the server's admin account (who has no account on clients) needs to be 774 otherwise the exported shares cannot be mounted by the clients.

I think this may cause a problem somehow but am still trying to figure it out.

Its working now that i have changed those other perms on the home folder to 774, even though i can use 770(same U/Gids) on the shares which is a bit weird

---

### Post by Eiríkr on 2008-03-11
Interesting -- this suggests that some process whose group membership falls into that "other" category needs to read something in the admin account's home directory.  Odd.  Thanks for posting the details though, you never know when some obscure complication like this might arise somewhere else.

Cheers,

Eiríkr

---

### Post by dgrafix on 2008-03-13
This is still causing issues for me. I seem to get this "not on same filesystem" comming up randomly,
The only way to get rid of it is to reset the permissions (even though they are already set) restart the server and then remount the drives from the client.

Is NFS broken or something??? Or do i need to create a group called fileaccess the same as on the server?!?

---

### Post by Eiríkr on 2008-03-13
> **dgrafix said:**
> Or do i need to create a group called fileaccess the same as on the server?!?

Aha -- yes!  Since filesystem permissions via NFS are all based on the UIDs / GIDs, it is imperative that these same UIDs / GIDs are also used by the client users.  The names themselves don't need to be the same, but the numerical IDs most definitely do.  So you could have group "fileaccess" on the server with GID 512, and group "zipperheads" on the client, but so long as "zipperheads" was also GID 512, clients in this group would have the same permissions on the NFS share as server-side members of the "fileaccess" group.

I'm not sure why this would be causing intermittent problems, though, unless there's some pattern, like maybe you're always running into trouble when accessing via certain client accounts, or something similar.  

HTH,

Eiríkr

PS -- I should qualify the above a bit -- *if* the "fileaccess" group is the primary group for shared files / directories, then yes, you'd need to have a group on the client with the same GID for access to go smoothly, *for those specific files and directories*.

---

