---
title: "CIFS mount freezes after laptop comes from suspend"
date: 2015-04-27
forum: Networking &amp; Wireless
---

### Post by Kljuka on 2015-04-27
I have a problem on my laptops that cifs mount (disk mounted from another computer using samba) freezes after laptop comes from suspend or sleep. Laptop has to be in suspend state for at least 10 minutes for this to happen.
What can I do? I really want to solve this problem as it's preventing me to recommend Ubuntu in company (they'll use Windows otherwise).

What I did:
I mounted the cifs share on my laptop by first creating
```
mkdir /media/smb-name
```

then inserting mounting procedure into /etc/fstab
```
//192.168.0.1/smb-name    /media/smb-name    cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777    0    0
```

And Adding the credentials in /root/.smbcredentials:
```
username=myusername
password=mypassword
```

And mounting the cifs share
```
mount -a
```

After suspending the laptop (for at least 10 minutes - not sure what is the exact amount of time needed) and waking it up, it "freezes" waiting for the share. For example executing this command in terminal:
```
ls -lah /media/smb-name
```

I've also opened a bug report but no one seems to notice it :( or direct me in any direction so I could solve it (I'm not sure I have enough knowledge to solve it). It seems to work well in Cent OS so this must be a Ubuntu specific problem:
[https://bugs.launchpad.net/ubuntu/+source/cifs-utils/+bug/1447632](https://bugs.launchpad.net/ubuntu/+source/cifs-utils/+bug/1447632)

Any help would be very appreciated

---

### Post by TheFu on 2015-04-27
Don't know the answer, I don't see this because we use autofs, not static mounts in the fstab.  Might that help you? [https://askubuntu.com/questions/15498/how-to-setup-automount-autofs](https://askubuntu.com/questions/15498/how-to-setup-automount-autofs)

---

### Post by Kljuka on 2015-04-27
Thank you TheFu for your help. Unfortunatelly no matter how hard I tried I couldn't make autofs mount my drive.

What I did:
/etc/auto.master (added)
```

/media/share   /root/auto.smb

```

then added /root/auto.smb
```

share -fstype=cifs,rw,username=xyz,password=xyz ://192.168.1.1/sharename

```

And then restarted the service
```

service autofs restart
ls /media/share

```

The "ls" command showed empty folder

The debugging feature shows:
```

>automount -f -v

Starting automounter version 5.0.7, master map /etc/auto.master
using kernel protocol version 5.02
mounted indirect on /media/share with timeout 300, freq 75 seconds

```

And then it's waiting forever while the /media/share directory remains empty.

---

### Post by TheFu on 2015-04-27
I have 3 files modified.

auto.master
```
/Data /etc/auto.Data --timeout=60 --ghost
```

auto.Data
```
D      -fstype=cifs,rw,iocharset=utf8,file_mode=0666,dir_mode=0777,credentials=/etc/samba/win7lap-D.credentials  ://172.22.22.14/D
```

/etc/samba/win7lap-D.credentials - just like your /root/.credentials file. ;) Nice.

The just restart autofs and make certain the CIFS share is enabled, active, with the userid/password stored in the credentials file. 
**sudo service autofs restart**

This results in /Data/D being the same as the Windows Share on the IP address listed and named "D" - which is actually the D: on the windows box.  Make sense?  Only /Data should be created and no files or directories should exist below /Data to keep problems from arising.  For example, I don't ever mount network storage under /media since that area is used by the OS to mount temporary storage.  It might be bad to have 2 storage subsystems trying to manage the same mount point dirs - thats all.

Clear as mud?  Oh ... and with autofs - nothing is mounted until some program requests it.  So ls /Data/D will mount it. Eventually, it will timeout and umount it if the storage isn't in use.  A shell with a pwd of /Data/D will keep it mounted.  I use autofs for all USB and NFS storage too.  Perfect for laptops, since they aren't always on the same network and may not have access to the storage. Of course, before I move from the home network anywhere else, I have to change directory to a non-NFS and non-CIFS pwd.


Update: /root/auto.smb above was NOT visible when I wrote this message.  As Morbius1 says below - **/media/share/share** is where things are mounted according to the settings in the prior message. This is a common mistake for everyone using autofs.

---

### Post by Morbius1 on 2015-04-27
It's way too late in the day for me to get into this properly but ....:

> And then restarted the service
```
service autofs restart
ls /media/share
```

The "ls" command showed empty folder
And it will since you are not accessing the mount point yet.

** According to your auto.master the parent folder for your mounts is /media/share.

** Your map file specifies the mount point ( the subdirectoy of that parent folder ) as share.

** So the full path to the mount point is /media/share/share.

Do a:
```
ls -l /media/share/share
```
You notice in TheFu's example the mount point isn't /Data or /D but /Data/D. ( BTW, don't forget TheFu's  "ghost" option or else this will drive you insane )

Am I missing something or should I just go to bed?

---

### Post by Kljuka on 2015-04-28
Thank TheFu and Morbius1

Now it (autofs mounting) works :). It seems the problem was with missing --ghost. And It seems to be a bad idea to mount into /media as all other /media/<other-mounts> dissapear (eg.: mounted through fstab, network manager).

I still have one question: I created directory for this
```
mkdir /storage
```

But I only know how to mount into (using autofs):
> /storage/storage
Not directly into:
> /storage


Unfortunately the initial problem (and bug) remains. These are my conclusions:

[LIST=1]
[*]Suspend computer while network share is still mounted (60 seconds till timeout (to auto unmount) haven't passed):
[LIST]
[*]on wake, you have to wait for 1,5 min to list that directory (it freezes the console in the mean time) 
[*]on laptop wake you wait for 3 min (more than 1,5 min),  and it works great (no waiting needed for the mounts to come back up). 
[/LIST]
  
[*]Suspend computer when network share has already been unmounted (you were inactive for 60 seconds in mounted directory so autofs has unmounted it):
[LIST]
[*]great! That works instantly as it mounts freshly 
[/LIST]
  
[/LIST]
 

So there really seems to be a bug in Ubuntu as it locks the cifs mounts for 1,5 minutes after wake from suspend or sleep (in case cifs mount was still mounted when going to suspend/sleep)

---

### Post by Morbius1 on 2015-04-28
I don't know if even autofs can overcome a bug between the network and hibernate but the only thing I can think of is to give your timeout a very small number.
```
 --timeout=5
```

As for the mount points you shouldn't need to create them yourself. AutoFS does that for you - as long as the "ghost" parameter is present.

So for example if you were to edit your master to this:
```
 /AutoFS /root/auto.smb --timeout=5 --ghost
```
And your auto.smb file to this:
```
smb-share -fstype=cifs,rw,username=xyz,password=xyz ://192.168.1.1/sharename
```
AutoFS will create the /AutoFS folder and it's subfolder /smb-share for you automatically.

---

### Post by Kljuka on 2015-04-28
Yes, you're right about the timeout. 

Would it be possible to mount (in your case) directly in
```
/AutoFS
```
(not int /autoFS/smb-share)?

---

### Post by Morbius1 on 2015-04-28
I would have to look through my notes on this but I don't think so.

AufoFS has been around for decades so there's probably a way to do this but I'm not sure how to pull it off at the moment. What you don't want to do is make "/" the parent folder since that would put your entire root directory under the control of AutoFS and that would not be a good thing.

If I find something I'll post back.

---

### Post by Kljuka on 2015-04-29
Thanks Morbius1 for help. 

Even though the solution doesn't fix the bug it might help mitigate it a bit.

p.s.: in case someone has any time, I'm very curious if I'm the only one having this problem (long waiting for cifs mounts). Or is it a general problem? For example: yesterday I had to wait 15 minutes for cifs shares to come back up.

---

### Post by TheFu on 2015-04-29
I don't see the issue. Have CIFS served by both Win7 and Ubuntu 14.04.  Reconnecting takes just a few sec - maybe 2-3 after the network comes back up.  OTOH, I do NOT suspend or hibernate with active connections.

---

### Post by Kljuka on 2015-04-30
Interesting. Then you fall under this category :) :

> 
2. Suspend computer when network share has already been unmounted (you were  inactive for 60 seconds in mounted directory so autofs has unmounted  it):

[LIST]
[*]great! That works instantly as it mounts freshly 
[/LIST]


---

### Post by TheFu on 2015-04-30
> **Morbius1 said:**
> I would have to look through my notes on this but I don't think so.

AufoFS has been around for decades so there's probably a way to do this but I'm not sure how to pull it off at the moment. What you don't want to do is make "/" the parent folder since that would put your entire root directory under the control of AutoFS and that would not be a good thing.

If I find something I'll post back.

Sorry - missed a few messages here.

You can mount to top level directories.  Use the - in the auto.master
```
/-      /etc/auto.nfs
```
However, I've never tried this with any other mounts than NFS and only for a single auto.nfs file (though that file does have multiple mount points inside it).  /D, /S, /R, /M .... etc.
Clear as mud?

---

### Post by Kljuka on 2015-05-02
Yes, it's clear :), thank you. I think I'll get used to "subdirectory mounting" (/storage/storage) or even leave the whole process to network manager (on desktop) as autofs doesn't circumvent the cifs bug in Ubuntu.

With network manager it would look like adding a file to:
/etc/network/if-up.d
```

/bin/mount -t cifs //192.168.1.1/storagename /media/storage -o credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 

```
(and of course create the /root/.smbcredentials with: )
```

username=myusername
password=mypassword

```

---

