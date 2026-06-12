---
title: "nfs server won't start: Unit proc-fs-nfsd.mount not found"
date: 2019-05-27
forum: Networking &amp; Wireless
---

### Post by holiday on 2019-05-27
I deleted proc-fs-nfsd.mount in an attempt to unmask the service and now :

    systemctl start nfs-kernel-server
    Failed to start nfs-kernel-server.service: Unit proc-fs-nfsd.mount not found

I have removed and re-installed nfs-kernel-server.

  systemctl enable nfs-kernel-server
 
But the same complaint about proc-fs-nfsd.mount.

What's going on? What can I try next?

---

### Post by TheFu on 2019-05-27
Put that file back.  Manually deleting files that are part of install packages is never a good idea.  Figure out which package that file is part of and reinstall it.

What do you mean by > in an attempt to unmask the service?

Perhaps this will help?

On my 16.04.6 NFS server, 
```
$ ll /lib/systemd/system/proc-fs-nfsd.mount
-rw-r--r-- 1 root root 98 May  8 18:54 /lib/systemd/system/proc-fs-nfsd.mount

$ more /lib/systemd/system/proc-fs-nfsd.mount
[Unit]
Description=NFSD configuration filesystem

[Mount]
What=nfsd
Where=/proc/fs/nfsd
Type=nfsd
```
With that information, you can recreate the file, the contents and set the permissions.  Or you could restore from the backup you made.

---

### Post by holiday on 2019-05-27
I purged nfs-kernel-server and reinstalled. A simple remove didn't work. 

The NFS server couldn't start because 'proc-fs-nfsd.mount is masked'. Googling about I found various solutions, none of which worked but since that file was a problem I thought that perhaps if I deleted it, it would be recreated. 

Ah ... no. 

But the purge worked fine. I backed up my exports file first, then copied it back, and all was well.

---

### Post by TheFu on 2019-05-27
I looked up what "mask" meant related to systemd.  It is a term that is new with systemd.
[https://fedoramagazine.org/systemd-masking-units/](https://fedoramagazine.org/systemd-masking-units/)  explains.

Leave it to that project to decide 2 existing methods weren't sufficient, so another one is needed. 
I looked through an AskUbuntu answer about this exact error message - BTW always post the EXACT ERROR AS SHOWN in your questions and use code tags so we understand that it is an exact copy. Doing so would prevent a few extra posts needed to clarify.

I assume that using ```
sudo systemctl unmask  proc-fs-nfsd.mount
``` didn't work, but it would be helpful to show that exact command AND whatever error message was returned, also in code tags.

More code tags help clarify what is put in and seen from in terminals.

If this problem is solved, would help the community to use the "thread tools" button at the top and mark it solved.

---

### Post by holiday on 2019-05-27
> **TheFu said:**
> I looked up what "mask" meant related to systemd.  It is a term that is new with systemd.
[https://fedoramagazine.org/systemd-masking-units/](https://fedoramagazine.org/systemd-masking-units/)  explains.

Leave it to that project to decide 2 existing methods weren't sufficient, so another one is needed. 
I looked through an AskUbuntu answer about this exact error message - BTW always post the EXACT ERROR AS SHOWN in your questions and use code tags so we understand that it is an exact copy. Doing so would prevent a few extra posts needed to clarify.

I assume that using ```
sudo systemctl unmask  proc-fs-nfsd.mount
``` didn't work, but it would be helpful to show that exact command AND whatever error message was returned, also in code tags.

More code tags help clarify what is put in and seen from in terminals.

If this problem is solved, would help the community to use the "thread tools" button at the top and mark it solved.

Here is a link to the issue as I posted it to askubuntu.

[https://askubuntu.com/questions/1141073/proc-fs-nfsd-mount-is-masked-cannot-unmask?noredirect=1#comment1891918_1141073](https://askubuntu.com/questions/1141073/proc-fs-nfsd-mount-is-masked-cannot-unmask?noredirect=1#comment1891918_1141073)

I apologise for my incomplete post here. Having had not much response on AskUbuntu I posted a quick hook here. After your response I see it would have been better to have replicated the entire posting. There is no good excuse to not have done that.  I don't post here as often as I used to so perhaps slipped back to old bad habits? Let's say.

Thanks for your response.

---

