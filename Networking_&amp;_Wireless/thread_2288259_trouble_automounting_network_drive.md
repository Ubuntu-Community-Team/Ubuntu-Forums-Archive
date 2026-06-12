---
title: "trouble automounting network drive"
date: 2015-07-25
forum: Networking &amp; Wireless
---

### Post by rebeltaz on 2015-07-25
I have an external drive attached to my main system auto mounted at boot up via fstab using it's uuid to /mnt/multimedia.

I want to have this drive made available on my girlfriend's computer every time she boots up. I tried adding to her fstab:

```
//192.168.1.15/mnt/multimedia /mnt/multimedia smbfs user=user,password=password 0 0
```

but when I ran 'mount -a' I got "mount: wrong fs type, bad option, bad superblock on..." so I changed 'smbfs' to 'auto' and then I got "mount: special device //192.168.1.15/mnt/multimedia does not exist"

What am I doing wrong!?

---

### Post by TheFu on 2015-07-26
If your girlfriend runs OSX or Linux, then you want to use NFS.  Look for a guide on how to setup NFS - their is a client and a server that must be installed.

If your girlfriend runs Windows, then you are stuck with CIFS/Samba. Look for a guide on how to setup samba - their are GUI and text config file methods - most people prefer the GUI for simple mounts.

Also - when you post, please be extremely explicit which change is made on which computer and don't forget that Linux is a multi-user OS, so the specific userid(s) involved will be needed too.

So - what OS is the GF running?

---

### Post by rebeltaz on 2015-07-26
> **TheFu said:**
> If your girlfriend runs OSX or Linux, then you want to use NFS.  Look for a guide on how to setup NFS - their is a client and a server that must be installed.

If your girlfriend runs Windows, then you are stuck with CIFS/Samba. Look for a guide on how to setup samba - their are GUI and text config file methods - most people prefer the GUI for simple mounts.

Also - when you post, please be extremely explicit which change is made on which computer and don't forget that Linux is a multi-user OS, so the specific userid(s) involved will be needed too.

So - what OS is the GF running?

I thought I did say which computer I did what on... No?

Both of our computers are Ubuntu 10.04 LTS. Her userid is elevyn and mine is derek. Samba is set up on my main system as well as (I now see) my laptop (which is Ubuntu 12.04 LTS). Just for the record, I don't automatically mount these drives on my laptop, but I can manually do it if I need to using 
```
sudo mount -t cifs //192.168.1.15/multimedia -o username=derek,password=password /mnt/multimedia
```

So I guess I need to setup Samba on hers... Thank you. Believe it or not, I usually know what I'm doing. Sometimes I just need a nudge :)

---

### Post by TheFu on 2015-07-26
Well - 10.04 desktop support ended in 2013. For server, last April - so .... nudge. [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) ;)

Yes, you provided a little data, but not enough to get the answer you seek in 1 reply. There is a client and a server for samba - no mention of which was installed where. I wasn't sure, so I asked.

CIFS is **not** the best way to share files on Unix systems on the same LAN. It just isn't.  NFS is best for a multitude of reasons - beyond being faster and maintaining normal, expected, Unix file permissions.
[https://help.ubuntu.com/lts/serverguide/network-file-system.html](https://help.ubuntu.com/lts/serverguide/network-file-system.html)

Putting a password into a command is poor security. Using a locked down credential file would be smarter if you plan to use CIFS. Nudge. ;)  OTOH, if you use NFS, take a look at autofs so the remote mount only happens when requested - this is really handy for a laptop. [https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)  I like to use autofs for USB drives to.

But the first thing you should do is get on 14.04 for the 5-more years of support (April 2019). We really shouldn't be helping anyone on 10.04 anymore - it is against forum rules.

Anyway - hope this all helps you to setup the new installs.

---

### Post by rebeltaz on 2015-07-26
> **TheFu said:**
> 
But the first thing you should do is get on 14.04 for the 5-more years of support (April 2019). We really shouldn't be helping anyone on 10.04 anymore - it is against forum rules.

Anyway - hope this all helps you to setup the new installs.

Thank you for your nudge :D I will look in to all of those suggestions... The reason for sticking with 10.04 is because it works (usually). "If it ain't broke, don't fix it!" and all that... besides that, every time I let software update itself - laptop, tablet, TV, Bluray player - it never fails that SOMETHING breaks. It broke so bad in my brand-new TV that I had to install a new mainboard to fix it! So I'm always hesitant to upgrade/update anything. 

Again, Thank you for your help!

---

