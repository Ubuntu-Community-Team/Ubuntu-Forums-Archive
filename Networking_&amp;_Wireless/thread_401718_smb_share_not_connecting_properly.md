---
title: "smb share not connecting properly"
date: 2007-04-04
forum: Networking &amp; Wireless
---

### Post by SonicSteve on 2007-04-04
Edit; Issue solved by dmizer's mount windows/samba unicode cifs how to. See the second sig link below.

Hi guys,
I don't know enough about the FSTAB file and samba to know if this is weird or just that I've made a mistake somewhere.

When I run sudo mount -a, enter my password, the command seems to execute properly. That is there are no errors.
However the mount doesn't show up in the "places" menu. Nor does it show up on the desktop. It does however show up in the mount folder I assigned to it. I only have read access though.

I have 2 Ubuntu machines running Edgy call them 1 (has the share) and 2 (trying to mount). I have a share that I believe is setup properly at least a windows computer can mount the share properly and have RW access. 

Here is the FSTAB command line I'm using;
# <file system> <mount point>   <type>  <options>       <dump>  <pass>


**//ubuntu/UbuntuShare /mnt/UbuntuSh smbfs, rw, 0 0**


OK so after rebooting the same FSTAB line now gives this error;
mount: unknown filesystem type ''
I'm stumped. 

Is this right? Should it be working? Is there something special about sharing SMB between 2 Ubuntu machines that I'm not familiar with? Windows connects to the share very nicely.

---

### Post by amohanty on 2007-04-04
Try the following
> 
//ip_address_of_smb_server/UbuntuShare /mnt/UbuntuShare smbfs rw 0 0

if you have the ip address mapped to hostname in /etc/hosts then it shoudl work fine.

HTH
AM

---

### Post by SonicSteve on 2007-04-05
I'll give it a try and let you know how it goes.

OK so now I have this error;
27570: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed

Any Idea what this means?
Edit;
I can access the share by way of Network browsing. I can't write to the share but I can access it.

---

### Post by SonicSteve on 2007-04-05
Here is my Hosts file;
127.0.0.1	localhost
127.0.1.1	UbuntuServer
192.168.0.107   ubuntu
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

I have configured the ubuntu computer to have a static IP on my router.

---

### Post by SonicSteve on 2007-04-05
OK so I found out the problem is with authentication
[http://www.debian-administration.org/articles/165](http://www.debian-administration.org/articles/165)

Now I need to configure read write access.
my line is now this.
//ubuntu/UbuntuShare /mnt/UbuntuSh smbfs username=****, password=*****,umask=000,  0 0
It mounts well but no RW.

---

### Post by SonicSteve on 2007-04-05
Wow am I getting tired of this. 
Here is my FSTAB mount 
//Ubuntu/UbuntuShare /mnt/UbuntuSh smbfs auto,rw, username=*****, password=******, 00     

I have tried everything I can think of. I even tried a howto for NFS(didn't work) 
The line above still mounts without errors, but only has read access. 

I'm still looking for some help on this before I'm bald!

Thanks

Edit;
I just confirmed that windows can still read and write to the share. We so badly need to make this easier. It just isn't right that it should be easier to setup a read/write drive mount in windows than it is between 2 ubuntu computers.

---

### Post by amohanty on 2007-04-06
keep the umask=... and add **user** right after **auto** (after a comma of course)

AM

---

### Post by dmizer on 2007-04-06
i wrote a tutorial for this that should help you out significantly.  try the second link in my sig.

and please remember that samba is a windows proprietary file sharing protocol which is one of the reasons that you're having difficulty.  i'm sincerely not trying to berate you for being frustrated, because i know it is indeed frustrating.  but sometimes it helps to have a bit of perspective on the whole issue to relieve some of that frustration.

---

### Post by SonicSteve on 2007-04-06
> **dmizer said:**
> i wrote a tutorial for this that should help you out significantly.  try the second link in my sig.

and please remember that samba is a windows proprietary file sharing protocol which is one of the reasons that you're having difficulty.  i'm sincerely not trying to berate you for being frustrated, because i know it is indeed frustrating.  but sometimes it helps to have a bit of perspective on the whole issue to relieve some of that frustration.

I'm just starting to figure this out. It actually occurred to me yesterday that SMB might not be the best way to share between two Ubuntu machines. 
I'll try your unicode method when I get the chance.

---

### Post by SonicSteve on 2007-04-06
> **amohanty said:**
> keep the umask=... and add **user** right after **auto** (after a comma of course)

AM

Tried this and I get the errdos access denied message.

---

### Post by dmizer on 2007-04-06
yeah ... between two ubuntu machines.

that's nfs.  should take you all of a couple minutes to set up.  check the fourth link in my sig.

---

### Post by SonicSteve on 2007-04-06
> **dmizer said:**
> yeah ... between two ubuntu machines.

that's nfs.  should take you all of a couple minutes to set up.  check the fourth link in my sig.


Yeah for dmizer and the magic unicode!!!! I haven't a clue what that stuff is but now it works!
For some reason NFS always gives me permission denied messages. I've tried chmod 777 on the share folders and still the same thing. This all happened after following the how to you mentioned.

ANYWAY mission accomplished even if it's a bit unorthodox.
Thankyou thankyou thankyou!!!!

---

### Post by dmizer on 2007-04-06
no problem.  too bad  you couldn't get nfs to work though.

unicode is merely an option to allow non-latin character groups to be displayed in a samba share.  the options that probably made the biggest difference to you were the file_mode and dir_mode which provide for the correct local permissions mask.

also, please go back and edit your first post, and mark it as solved so that others will know that they can find an answer here.

---

