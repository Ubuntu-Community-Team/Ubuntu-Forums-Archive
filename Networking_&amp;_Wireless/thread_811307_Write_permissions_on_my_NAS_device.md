---
title: "Write permissions on my NAS device"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by sp00ner on 2008-05-29
Still pretty much a newby. I posted this a couple of times in the beginner section without much luck. My problem is that I don't seem to have write permissions to my NAS device inside the Gnome GUI. For example, I cannot copy files from the local disk to the NAS using the GUI file explorer. I get a "not enough space" error when there is definitely free space available. Another example is, I can open a document from the NAS in say Open Office but when I try to save my changes it says something about a general input/output error while accessing /mnt/nas/bla bla bla.doc. My work around has been to save files to my local disk and copy them to the nas using the command line.

Any ideas? I know one of you brainy gurus has a few tricks up your sleeve. If I can get this one problem solved, all my computers and laptops in the house are getting this OS installed.

Ubuntu 7.10 with the Gnome desktop

---

### Post by sammy_pal on 2008-05-29
What are you using to mount your NAS device ?
I mean are you mounting it using samba or NFS or something else??

---

### Post by sp00ner on 2008-05-29
I am at work right now so I cant verify, but I am pretty sure in the fstab file it specifies smbfs in the line that mounts it during bootup.

---

### Post by sp00ner on 2008-05-29
Thought I should also mention that on a seperate laptop running the same version of Ubuntu only with the KDE desktop, and using the same method to mount the NAS, I dont have this problem.

---

### Post by sammy_pal on 2008-05-30
Can you post the line in the fstab file, that mounts the NAS device. Maybe something is wrong with the access permissions.

---

### Post by sp00ner on 2008-06-01
//nas/home_nas /mnt/nas smbfs credentials=/etc/samba/user,rw,uid=curt 0 0

---

### Post by Paqman on 2008-06-03
Try this:

```

//nas/home_nas /mnt/nas smbfs credentials=/etc/samba/user,file_mode=0777,dir_mode=0777 0 0

```

I'd also use cifs instead of smbfs, it's an updated version of the same protocol. Just replace smbfs on that line with cifs.

---

### Post by sp00ner on 2008-06-03
Thanks Paqman, I will give that a try when I get home from work and post the results.

---

### Post by sp00ner on 2008-06-06
> **Paqman said:**
> Try this:

```

//nas/home_nas /mnt/nas smbfs credentials=/etc/samba/user,file_mode=0777,dir_mode=0777 0 0

```

I'd also use cifs instead of smbfs, it's an updated version of the same protocol. Just replace smbfs on that line with cifs.

I copied and pasted this line into my fstab file and removed the old line, and rebooted. The same problem still exists. So I replaced the smbfs with cifs and it doesnt seem to want to mount. If I try mounting from the command line I get the following error.

mount error: could not find target server. TCP name nas/home_nas not found
No ip address specified and hostname not found

---

