---
title: "Xubuntu NFS Client"
date: 2006-10-18
forum: Networking &amp; Wireless
---

### Post by ATAQ on 2006-10-18
Hey I have an NFS/ Samba Server running on my Ubuntu 5.10 Server and I am trying to connect to the server from my Xubuntu 6.06 desktop but there is no application there that  I can view my files from.
I am a newb as far as networking goes. Any help would be gratefull.
Thanks,

---

### Post by kidders on 2006-10-18
Hi there,

You should access network shares the same way you would a USB hard disk or a CD ... mount the filesystem and navigate to the mount point as you normally would.

**mount -t nfs server:/path/to/share**
**mount -t smbfs //server/share**

---

### Post by ATAQ on 2006-10-18
Thanks, but how do I get the source and name of the nfs server?

---

### Post by kidders on 2006-10-18
Hey again,

The easiest way to get a sharelist from a host using NFS is with **showmount -e hostname**. If you don't know the hostname, you're a bit stuck though. Afaik NFS shares don't like to broadcast themselves the way Samba ones do.

---

### Post by dannyboy79 on 2006-10-18
also, smbclient -L "hostname or ip", then enter your password for that machine and you'll see all available shares on that server. or if you don't know what the hostname is either, you can try smbtree, enter password for the machine you're actually working on and you should see all available domains and workgroups and each of their shares. or findsmb, I think. well now that I think about it, maybe this is only for smb servers. you could always try it, nothing to lose

---

### Post by ATAQ on 2006-10-18
nice one guys, job sorted. thanks for ye're time

---

### Post by kidders on 2006-10-18
> **dannyboy79 said:**
> also, smbclient -L "hostname or ip", then enter your password for that machine and you'll see all available shares on that server. or if you don't know what the hostname is either, you can try smbtree, enter password for the machine you're actually working on and you should see all available domains and workgroups and each of their shares. or findsmb, I think. well now that I think about it, maybe this is only for smb servers. you could always try it, nothing to lose

Nice solution :-) (Assuming, of course, that your Samba and NFS shares are all identical.)

Glad we could help!

---

### Post by dannyboy79 on 2006-10-18
> **kidders said:**
> Nice solution :-) (Assuming, of course, that your Samba and NFS shares are all identical.)

Glad we could help!

I'm a bit offended by your sarcastic remark! :mad: and if you could read that's exactly why I wrote, "well now that I think about it, maybe this is only for smb servers. you could always try it, nothing to lose"

---

### Post by mips on 2006-10-18
> **dannyboy79 said:**
> I'm a bit offended by your sarcastic remark! :mad: and if you could read that's exactly why I wrote, "well now that I think about it, maybe this is only for smb servers. you could always try it, nothing to lose"

I might be missing something but I fail to see the sarcasm you are referring to.

---

### Post by kidders on 2006-10-18
> **mips said:**
> I might be missing something but I fail to see the sarcasm you are referring to.

Lol yes... I merely suggested that the idea of an "NFS/Samba server" implies that anything shared via NFS might well have an opposite number in Samba. Thus, the notion that one could detect NFS shares simply by broadcasting for Samba ones is, albeit indirect, the kind of "outside-the-box" suggestion that would never have occurred to me!

No offence was intended [-( hehe. In fact, quite the opposite.

---

### Post by dannyboy79 on 2006-10-19
> **kidders said:**
> Lol yes... I merely suggested that the idea of an "NFS/Samba server" implies that anything shared via NFS might well have an opposite number in Samba. Thus, the notion that one could detect NFS shares simply by broadcasting for Samba ones is, albeit indirect, the kind of "outside-the-box" suggestion that would never have occurred to me!

No offence was intended [-( hehe. In fact, quite the opposite.

Oh, I took your smiley face as laughing at me. Thank you for the compliment then!

---

