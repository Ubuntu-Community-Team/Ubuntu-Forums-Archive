---
title: "How to Samba &amp; Ubuntu workstation 8.04.1"
date: 2008-09-17
forum: Networking &amp; Wireless
---

### Post by polarbar on 2008-09-17
:popcorn:
Hi,

I am a rookie with Linux.

I just installed Ubuntu workstation 8.04.1.

I want to share files with other Windows XP workstation.

I have to read first information on "How to Samba".

What are the best treads to read for installing Samba on an Ubuntu workstation 8.04.1 ?:)

---

### Post by rbc on 2008-09-17
[http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)
This is for Ubuntu 6.10, but still applicable. It will walk you right through it

---

### Post by polarbar on 2008-09-17
Thanks rbc, I will look this video.:)

---

### Post by Another Monkey on 2008-09-17
Hi there, the video makes mention of "System/Administration/Shared Folders" which has been removed from Hardy and it seems there is no replacement.

I am tearing my hair out trying to get Windows and Ubuntu working together at home.  Neither machine can even see each other, let alone share.  I can ping OK.

I tried to create a share and I had to install a sharing service (it did not tell me what it was installing, but I thought Samba was installed out-of-the-box?).  Then it told me that I did not have permissions to create a share.  If I do "sudo nautilus" at the terminal I can create a share OK, do I have to do that all the time?

The error was:
```
'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.
```

I've also spotted that Samba is missing from under Services (and other thread mentioned that this need to be enabled).

I also tried to connect back to myself as a test (I have no idea if this should work or not) using "smb:///127.0.0.1" and got told that it could not be found.

The really, really annoying thing is that the networking is fine if I take the lappy into the office.  It sees all the Windows servers, workstations and their shares fine; no need to edit anything.  It is just at home it refuses to play.  Office is ethernet and domain authentication, home is wireless with WPA enabled and no domain (no idea if that has any bearing).

This is really driving me nuts, although I suspect it might b something at the Windows side of things.

---

### Post by gregphil on 2008-09-17
To test a samba browse from the command line you would use
 
smbclient -L COMPUTERNAME
for authenticated shares (security = USER), and
 
smbclient -L COMPUTERNAME -N
for anonymous (security = SHARE) shares
 
smbtree
should list all shares on subnet for WORKGROUP specified in smb.conf

---

### Post by Iowan on 2008-09-17
> **gregphil said:**
> To test a samba browse from the command line you would use
[COLOR="Red"]
smbclinet[/COLOR] -L COMPUTERNAME
for authenticated shares  (security = USER),  and

[COLOR="Red"]smbclinet[/COLOR] -L COMPUTERNAME -N
for anonymous (security = SHARE) shares

smbtree
should list all shares on subnet for WORKGROUP specified in smb.conf
I presume you meant smbclient.

---

### Post by greenstar on 2008-09-17
> **Another Monkey said:**
> Hi there, the video makes mention of "System/Administration/Shared Folders" which has been removed from Hardy and it seems there is no replacement.

I, too, am disappointed to find this missing from my System->Administration menu.

> **Another Monkey said:**
> The error was:
```
'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.
```

I encountered this error also. I resolved it by making sure that the user I created shares with had the appropriate privileges to do so. To do this, go to: System->Administration->Users and Groups, click unlock, enter your password. Then select the user in question and click Properties. In the User Privileges tab, be sure that the line "Share files with the local network" is checked. Click OK, then Close.

HTH,
Greenstar

---

