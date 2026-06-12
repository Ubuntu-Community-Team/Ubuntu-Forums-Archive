---
title: "using a remote folder with big files"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by Hospadar on 2009-05-20
At work, I need to be able to share a folder of data with a co-worker.  Ideally the folder we need is on a server somewhere, ideally we would both mount it with sshfs and we could just live happily ever after.


The problem is we have really huge data files (it's functional data from an mri) and sshfs would be way too slow.  We also are constantly creating and deleting files so something like subversion is not really feasible as we have to much going on to want to worry about explicitly removing and adding files with svn (or git or what have you). furhtermore, we don't really need to keep multiple previous versions of our big data.   


We are considering (all via cron job) just rsyncing (push) to the server, and then when we have both done that, we rsync again (pull) to get each other's new files.  The problem with this is that if I delete a file locally, then rsync (pull), I'll get that file right back.  If I tell rsync to delete remote files not on my machine, then I might accidentally delete files that my boss added (since there really would't be a way to tell between files I deleted locally and files someone else added remotely). 

I'm wondering if there's some way to make sshfs keep local copies of everything (maybe in swap space, maybe just a folder) and just check on access to make sure the local copy is current.  If you know of anything else that would allow us to keep stuff synchronised, that would be great too.  We both use linux machines and have no problems on the command line, setting up cron jobs, etc.

---

### Post by Titan8990 on 2009-05-20
Sounds like webDAV would suit your needs just fine. Also WebDAV supports "locking" a file when it is in use so two people are not trying to alter the same document at the same time. 

WebDAV can also be mounted via fuse like sshfs

---

