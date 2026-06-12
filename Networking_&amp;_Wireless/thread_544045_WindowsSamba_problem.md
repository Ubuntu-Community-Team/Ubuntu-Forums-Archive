---
title: "Windows/Samba problem"
date: 2007-09-05
forum: Networking &amp; Wireless
---

### Post by Tim Blancke on 2007-09-05
I have an Ubuntu machine connected to a network that also contains a Vista machine and a wireless/router with a cable connection. The hardware all works fine, and internet is available on both machines. Further, the Samba Server allows me to fetch files to the Vista machine from the Ubuntu machine

I do have a problem going the other direction though. The Unbuntu machine can see the Vista machine, showing the correct Workgroup and partitions and high level folders. But when I try to open a lowest-level folder to get a file I get the message:" Nautilus cannot display "... followed by the name of the folder I want to open.

Firewalls: Firewall OFF on the Vista machine. No firewall on the Ubuntu machine. Further, the same (Ubuntu) computer works fine if an XP system is booted instead of Ubuntu. This would seem to indicate that the Vista permissions are set OK, and that something in the Ubuntu Samba client is blocking access to the files themselves. It's as if the Ubuntu machine had a firewall, but I never knowingly installed one.

Since I am naive Windows user, unfamiliar with all the protections and safeguards of Linux (but trying to learn), I would greatly appreciate a few helpful comments.

Thanks,

Tim

---

### Post by nathanhill on 2007-09-06
Hi, I've also been frustrated by this issue for a long time.  So much so, that I've moved away from ubuntu (in spite of so many things I like about ubuntu) and tried other distros looking for an answer to this issue, but I didn't find any solutions there either.

I still have not figured out to make the 'native' smb browsing facility in Nautilus be able to browse Vista shares without the error you mention, but I have found a work around:

I installed **pyNeighborhood,** and mount shares using **CIFS.**

(pyNeighborhood can also mount using SMBFS - but this method is dipricated, and I've had trouble with stability and character translation for mounts made using SMBFS).

You need to configure a few things specially though if you want to be able to mount shares logged in as a normal user though:

You need to configure mount.cifs and umount.cifs as SETUID to perform CIFS mount/dismounts as a normal user.  Do this as follows:
[I]
sudo chmod u+s /sbin/mount.cifs
sudo chmod u+s /sbin/umount.cifs[/I]

ANOTHER IMPORTANT POINT - this had me stuck a while:
You can only mount to a mount point  that is OWNED by the user.

I for example have configured pyNeighborhood to mount shares to a pyNeighborhood folder in my users home folder: e.g. /home/USERNAME/pyNeighborhood.

Before I was trying to mount to a folder i created using sudo in the /mnt folder, even if the folder had accesspermissions for a group my normal user was a member of, the mounts never worked.

I found a bug in launchpad discribing this particular problem:
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/106146](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/106146)

Hope this helps you.

I would still WELCOME anyone who can explain how to enable browsing windows shares in nautilus with out mounting using CIFS/SMBFS though.

This is an issue I just can't understand can stay laying around as latent problem as long as it has.  I have searched the forms and googled, and not found anything to tell how to fix it so I can browse VISTA shares with Nautilus with out the error.  I'm pretty stubborn/thorough when I look into finding a solution to an issue.  But I'm still a linux newbee, and I must admit that this is one of the issues that leaves a bad taste in my mouth.

**As much as I like LINUX, I need to be able to connect to other computers simply and effectively even if they are WINDOWS VISTA boxes...**

---

### Post by Tim Blancke on 2007-09-06
Nathan,
Thanks for your reply. Right now it's over my head. But I'll delve into it if I can't turn up something more direct. 

I tried connecting Ubuntu to an XP machine, and Samba works fine in both directions.

So who to blame?

I did try using Firefox and Opera  to fetch a file from the Vista machine, but that didn't work either. I was hoping that approach would avoid Nautulus.

Frankly, I can't believe that the inability to transfer files in one direction using Samba can really be a long-term fundamental problem. No one would release an application that only half worked (I think.). Therefore I think we have a Vista problem. Anyway, I'll let you know if anything turns up. Basically, I like Ubuntu and this is the only problem that I haven't been able to solve so far. I'll keep waiting for a Vista upgrade from someone!

Tim

---

### Post by Tim Blancke on 2007-09-12
Nathan,

I installed pyNeighborood, as you suggested.
It works, and I can now fetch files from a Vista machine. Great!

I also set the file browser to be nautilus, and that works fine.

However I do still have trouble getting a 'mount' when running as an ordinary user.
I followed all the suggestions that you made regarding security authorizations, but still get a 'Failed to mount' message when running as a non-root user. Also, mountcifs doesn't work. Only smbmount works.

Google turned up a number of sites with comments, but the only one that helped was to use gksudo.

So, as an ordinary user, I resorted to gksudo to run pyNeighborhood. That's OK, except it's a very minor pain to have to enter the user password.

I do have an intellectual curiosity about why I can't get the 'user' location to work on its own.
But at least I can transfer files now, and I appreciate your help very much.

Tim Blancke

---

