---
title: "mounting /home"
date: 2011-01-01
forum: New to Ubuntu
---

### Post by eli1000 on 2011-01-01
Hi

I am a new ubuntu user and an absolute beginner. I had installed ubuntu with wubi in parallel with my windows and it had been fine. Today, I got an error message at the login "An error occurred while mounting /home" and I can't login. When I go to the recovery mode, the /home directory seems to be empty! Can someone help me out? Have I lost all my data?:(
When I try to mount it manually, I get: wrong fs type, bad option, bad superblock on /dev/loop1, missing codepage or helper program, or other error...

Thanks in advance!
Eli

---

### Post by blazemore on 2011-01-01
Hi. In order to help you can you please go back to recovery mode and type
```
cat /etc/fstab
```

I know you'll have to type it manually so just post the line that includes the word /home

What antivirus are you running on Windows, by the way?

---

### Post by eli1000 on 2011-01-02
I'm running AntiVir on Windows,
and the fstab line is:
/host/ubuntu/disks/home.disk   /home   ext3   loop   0   0

Thank you so much!

---

### Post by eli1000 on 2011-01-05
I uninstalled the last application I installed on ubuntu (which was wine) and now I can login with skipping /home mount, but my /home is still empty and it seems like I have lost everything :( Does data recovery work or is this a mounting problem?
Please help, anyone :(

---

### Post by bcbc on 2011-01-05
So you have created a separate virtual disk for home. Likely that is no longer in your /ubuntu/disks directory or if it is, it has some sort of error.

What you should do:
Run check disk on Windows - whatever 'drive' you installed Ubuntu (I'll assume c: ). So go to My computer, right click C:, Properties, Tools, Check disk for errors, automatically fix. If it's C: you'll have to reboot to complete.

Then confirm that the home.disk is still there: c:\ubuntu\disks\home.disk
If not, look for a hidden folder C:\FOUND.000 and it should be there - windows sometimes moves corrupted files or repaired files to these hidden directories. Move it back.

If the home.disk is there, but it's not mounting, then run fsck on it. The following command you can run since it's not mounting the home.disk, but usually you'd need to boot from a live CD before fsck'ing as you should only do it on unmounted file systems.
```
sudo fsck /host/ubuntu/disks/home.disk
```

Then try 
```
sudo mount -a
```
See if /home magically appears.

Any issues you find while doing the above, stop and report back.

---

### Post by eli1000 on 2011-01-05
Hi,

Thank you for your reply.
The home.disk was already there but I tried to run the disk check (the size of the file remained to be 0KB), and when I try to run fsck, I get the message:
"Attempt to read block from filesystem resulted in short read while trying to open /host/ubuntu/disks/home.disk could this be a zero-length partition"

Any ideas? :(

---

### Post by sandyd on 2011-01-05
> **eli1000 said:**
> Hi,

Thank you for your reply.
The home.disk was already there but I tried to run the disk check (the size of the file remained to be 0KB), and when I try to run fsck, I get the message:
"Attempt to read block from filesystem resulted in short read while trying to open /host/ubuntu/disks/home.disk could this be a zero-length partition"

Any ideas? :(
Time for testdisk.

---

### Post by bcbc on 2011-01-05
I'm not sure you'll be able to do anything to get this back. You can't undelete it since it isn't deleted, it's just zero length. And typically home.disk isn't a contiguous file so it's unlikely a raw file recovery utility would be able to retrieve it intact.

That's a really strange thing to happen.

---

