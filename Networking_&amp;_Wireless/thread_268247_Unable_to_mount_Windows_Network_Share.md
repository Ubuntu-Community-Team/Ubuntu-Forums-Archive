---
title: "Unable to mount Windows Network Share"
date: 2006-09-29
forum: Networking &amp; Wireless
---

### Post by leona on 2006-09-29
Hi there.

Apolgies for double posting, was advised to repost my question here.

Running Ubuntu64 6.06.

I am trying to get my machine to auto mount a directory on my windows file server.

I've got this working in Suse no problem.

I can do it manually, but if I put the commands in the fstab file nothing happens it will not mount.

The manual commands I'm using
```
sudo mount //192.168.1.1/fileshare /home/leona/network -o username=files,password=xxx,fmask=777,dmask=777
```
Works but
the fstab line.
```
//192.168.1.1/fileshare  /home/leona/network/    smbfs   username=files,password=xxx,fmask=777,dmask=777   0       0

```
Doesn't.

What is going wrong?  Is there a log I can look at to see the error?

I have tried other methods of connecting to this share, as suggested in a post, creating a file with the command and then running at the session start up, again if I ran from terminal it would work, but refused to work at startup.

I don't get it, I must be missing something simple,

Help or advice would be greatly appciated.

---

### Post by morphodone on 2006-09-29
I saw your post in the other forum as well.

I'm not sure what you are missing there.

I assume there is nothing listed in /home/leona/network/ when
you first boot right?

You might try adding 'auto' like so.

```
//192.168.1.1/fileshare  /home/leona/network/    smbfs   **auto**,username=files,password=xxx,fmask=777,dmask=777   0       0
```

---

### Post by leona on 2006-09-30
Thanks morphodone

Yes that's right the folder is empty when I click on it or dir it, nothing in it.

Added the auto, but sadly same result.

:confused: ](*,) :confused:

---

### Post by morphodone on 2006-09-30
Hmmm, I don't use samba shares all that much.

I'll read up in a little while and see if I can find anything for you.

---

### Post by Compact on 2006-09-30
I had the same problem. The solution is to install smbfs packages. You can do it trought synaptic.

---

### Post by leona on 2006-09-30
Smbfs is installed, I just rechecked.

I'm told linux is pritty good at logging stuff, is there a startup log or network log I could look at to see if that tells me what the problem might be?

---

### Post by gesho on 2006-10-01
dmesg gives startup log
other logs are at /var/log folder

---

### Post by leona on 2006-10-02
Thank you gesho. 
I found this in the dmsg log
37.202455] smbfs: mount_data version 1919251317 is not supported
Can anyone translate it, does it have anytyhing to do with my issue, how can I resolve it?

---

### Post by Iowan on 2006-10-03
I just stumbled on to this one elsewhere in the forums:
[http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html]("http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html")

---

### Post by leona on 2006-10-03
Thanks Iowan, I tried all that without success, but it did give me an idea, maybe its a permissions issue?? hum.

So I have come up with a rather 'nasty' workaround, I'm not going to call it a fix, cos this should work withut me having to do this, I'm sure this is a bug.

Anyway I created a txt file called 'connectwshare' in my users folder, I inserted the following into it.

```

#!/bin/bash
smbmount //192.168.1.1/fileshare /home/leona/network -o username=files,password=xxx,uid=leona,gid=users

```
then 
chmod it to 777
also ran this.
chmod u+s /usr/bin/smbmnt

put this in the startup tab of my session config and ..... bingo,  it now connects the share "finally" but like I said I'm not sure this is the correct way it should be done, but its the only way I can get it to work.

---

### Post by morphodone on 2006-10-03
Saw an article about this today.

[Here]("http://www.cyberciti.biz/faq/configure-a-system-to-automount-a-samba-share-with-etcfstab/")

Maybe it'll give you some insight on what you are doing wrong.

---

