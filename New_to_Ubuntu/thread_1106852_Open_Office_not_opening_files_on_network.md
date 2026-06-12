---
title: "Open Office not opening files on network"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by longtom on 2009-03-26
Hi,

Any files on a network, which should open with open office, don't.  In the best of cases I see a splash screen of OO and that was it.

No problems with Gnome or Abiword - works just fine.

Ubuntu 8.10
OOo 3.0

Any advise welcome

---

### Post by yeats on 2009-03-26
Okay - these might be obvious questions, but 

1) are you able to open OO.o files on your local drive 

and 

2) are you able to open other files over the network (in other programs)?

---

### Post by superprash2003 on 2009-03-26
sometimes if another user on your network has opened the same file , then the file would get locked..

---

### Post by lykwydchykyn on 2009-03-26
Don't know for sure about Gnome, but in KDE OpenOffice doesn't recognize virtual file systems, such as when you browse a samba share or files over ssh in dolphin/konqueror.  You have to actually mount the remote drive to a folder for OpenOffice to be able to open it.

How are you accessing the files?

---

### Post by HermanAB on 2009-03-27
This a known issue.  OOo file locking doesn't work in some network setups, causing the files to open read-only.

There are two solutions:

    * Get file locking working. This usually seems to involve making sure rpc.statd is running on both the server and the client. But I have not investigated this in detail, as there is another solution that works for me.

    * Find and edit the file
      Code:

      soffice

      . In it, you will find the following lines:
      Code:

      # file locking now enabled by default
      SAL_ENABLE_FILE_LOCKING=1
      export SAL_ENABLE_FILE_LOCKING

      Comment out the last two lines. Note that this disables file locking and so is potentially unsafe. As I said, it works for me, because the file in question is in my home directory, mounted from a NFS server, and I know no-one else has access.

Cheers,

Herman

---

### Post by longtom on 2009-03-27
Thank you for all your contributions.  Unfotunately the problem persists.

> 1) are you able to open OO.o files on your local drive 

and 

2) are you able to open other files over the network (in other programs)?

1) Yes
2) Yes

> sometimes if another user on your network has opened the same file , then the file would get locked..

as said in first post, I can open the files with not open office applications.

> How are you accessing the files?

Doesn't make a difference whether I mount then first or not.  Other applications open those files direct, just not Oo.

> * Find and edit the file
Code:

soffice

. In it, you will find the following lines:
Code:

# file locking now enabled by default
SAL_ENABLE_FILE_LOCKING=1
export SAL_ENABLE_FILE_LOCKING

Can't find the line in my soffice file.

Still open for suggestions.

---

### Post by MrWES on 2009-03-27
> **longtom said:**
> Hi,

Any files on a network, which should open with open office, don't.  In the best of cases I see a splash screen of OO and that was it.

No problems with Gnome or Abiword - works just fine.

Ubuntu 8.10
OOo 3.0

Any advise welcome

Are the network files mounted with Samba? If so, there is a bug in Oo in opening network files mounted with samba. There is a workaround; mounting via cifs. Let me know if this is the case because there is also a bug with shutdown on cifs mounted files -- with another work around :)

Bill

---

### Post by longtom on 2009-03-27
> **MrWES said:**
> Are the network files mounted with Samba? If so, there is a bug in Oo in opening network files mounted with samba. There is a workaround; mounting via cifs. Let me know if this is the case because there is also a bug with shutdown on cifs mounted files -- with another work around :)

Bill

Yep - all mounted with samba.  Worked fine until the last Oo update...

Do I have to rearrange may whole network on Ubuntu to get Oo going again?

---

### Post by MrWES on 2009-03-27
> **longtom said:**
> Yep - all mounted with samba.  Worked fine until the last Oo update...

Do I have to rearrange may whole network on Ubuntu to get Oo going again?

No...well try on the machine trying to access the OOo files, mount them in your /etc/fstab like this:



```
# Mount Shares From Ubuntu Server
//192.168.1.101/MyFiles /home/bill/SharedFiles cifs credentials=/home/bill/.creds,_netdev,uid=bill,gid=users 0 0

```

the .creds file is a file in your /home directory with rw perms by you only (chmod 600). And should look like this:

```
username=YOURUSERNAME
password=YOURPASSWORD

```

Obviously, change the line fstab line above to match your needs. This will allow you to access samba mounted OOo files over the network. However, cifs also has a bug, and shutdown will hang because during shutdown the network connection is killed before cifs has a chance to umount. So to fix that I put the following command in:

```
/etc/gdm/PostSession
```
```
umount SharedFiles/
```
Again, edit that to match your needs. These two adjustments should allow you to access the shares with OOo and let shutdown work properly.

Bill

---

### Post by longtom on 2009-03-27
Thank you very much.

I'll be having a go at it in good time.  In the meantime I work in gnome, which appears to be quite satisfied with my set up and opens any file I ask it to.

So what's wrong with Oo?

---

### Post by MrWES on 2009-03-27
> **longtom said:**
> Thank you very much.

I'll be having a go at it in good time.  In the meantime I work in gnome, which appears to be quite satisfied with my set up and opens any file I ask it to.

So what's wrong with Oo?

[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/229839]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/229839")

---

### Post by longtom on 2009-03-27
> **MrWES said:**
> [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/229839]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/229839")

Thanks.

I am reading that it is suspected to be a Gnome problem.  I am now in KDE...same problem.

---

