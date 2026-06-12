---
title: "Connecting to Windows network shares"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by horrendo on 2008-08-26
Hi,

I feel like such an idiot here.  I used to have Windows networking just fine.  Then I did a reinstall with 8.04 (I had 7.10), and I thought I'd set everything up, but no go.

Here's the symptoms ...

I click Places, Network to browse the Windows network.  It shows me all the Windows machines just fine.  When I double click on a machine to explore the network shares for that machine, my machine thinks for a while and then nothing - just an empty panel.

What has happened behind the scenes is that it has tried to connect to the Windows Domain using some password from somewhere, failed, retried, and eventually locked out my Windows domain account.

Before I reinstalled, it used to prompt me for my password each time I would connect.  I vaguely remember checking a box to say 'Remember password', and maybe that's the problem.  We are required to change our passwords every month, so maybe it is using an old password, but not re-prompting me if the login fails.

It's hard to know what's going on, and I'm not sure where to look.

If anyone has any ideas I would be very grateful.

Thanks.

---

### Post by horrendo on 2008-08-26
Anyone have any ideas on this?

---

### Post by in0ni on 2008-08-26
I am having this exact same problem, and was browsing before I posted.

If I browse using Places > Network it shows me "Windows Network", than I click on the domain, than I click on the machine, and nothing. Like you, it apparently sends the wrong password and locks my windows account. I tried making changes to the smb.conf file: changing "passwd backend" to "smbpasswd", set up an account (using: sudo smbpasswd -a username) with the correct password, but nothing. I also tried to set "wins support", nothing. I also changed "unix password sync" to "no"... nothing.

But... see if this works for you, cause it works for me:

If you try to access a share from the machine directly, it will prompt you for a password, and will work: (smb://machine_name/share_name instead of smb://machine_name, which does not work)

Also, if you try to use smbclient to list the shares of that machine: (smbclient -L machine_name -U username). It will prompt for your passwd, and again, it will work -- or at least it does for me.

Let me know if those two work for you, cause they do for me... any one have any ideas why we are unable to browse the shares using nautilus, but are able to browse a share directly, or using smbclient -L ??

---

### Post by horrendo on 2008-08-26
I can confirm the methods that worked for you also worked for me.

I guess it is a sort-of-workaround, but I would love to get back to being able to work the way it used to.

---

### Post by bab1 on 2008-08-26
For Linux (Ubuntu) to be able to browse a Windows computer for shares you need the "[COLOR="DarkOrange"]**smbfs**[/COLOR]" client.  See [[COLOR="Red"]**here**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=898911&highlight=smbfs").

---

### Post by horrendo on 2008-08-26
I already have smbfs installed.  That is not the problem (but thanks anyway).

---

### Post by in0ni on 2008-08-26
yeah, also not the case here. I already had smbfs installed and was using it to mount shares on boot, but there are so many, I rather just browse.

---

### Post by bab1 on 2008-08-26
Hmmmm...

If you are NOT part of an AD domain, then syncing the passwords from the windows host and the Linux host and smbfs is all you need.  Samba (the server) is used to serve files to Windows hosts.  No amount of messing with smb.conf will help you...ever!

If you were a part of AD domain and you upgraded to Hardy...ooops.  I would check the password infrastructure.  Winbind etc.

My network has Windows hosts that talk to Samba.  I also have Linux hosts that talk to Windows shares via smbfs.  I believe now that your probs are the user and/or machine authentication.

I might add that the GUI (gvfs) system is mostly broken in Hardy.  People have been complaining for months now.  I'll bet that's why you can find the shares using the command line.

---

### Post by horrendo on 2008-08-26
So when the "enter password" dialog pops up, there are 3 options - Forget Immediately, Remember password until you logout, and Remember forever.

Does anyone know where the login credentials get stored if you select the 'Remember forever' radio button?

---

### Post by horrendo on 2008-08-26
The fact that it is trashing the Windows Domain account implies to me that it is using an incorrect password multiple times and not re-prompting on an initial failure.

---

### Post by bab1 on 2008-08-26
> **horrendo said:**
> So when the "enter password" dialog pops up, there are 3 options - Forget Immediately, Remember password until you logout, and Remember forever.

Does anyone know where the login credentials get stored if you select the 'Remember forever' radio button?

All the GUI (gvfs) stuff for samba is located at: ```
/var/lib/samba/

```

---

### Post by in0ni on 2008-08-26
> **bab1 said:**
> Hmmmm...

If you are NOT part of an AD domain, then syncing the passwords from the windows host and the Linux host and smbfs is all you need.  Samba (the server) is used to serve files to Windows hosts.  No amount of messing with smb.conf will help you...ever!

If you were a part of AD domain and you upgraded to Hardy...ooops.  I would check the password infrastructure.  Winbind etc.


In my case, I am only accessing AD resources, and I am not authenticating against AD.

I do not have samba installed, just smbclient, and smbfs (with their dependencies). From what I can tell the smb.conf file is used. For example, changing my workgroup to my AD Domain, will make the domain default when clicking on Places > Network. I would assume the authentication would apply as well, but maybe not.

> **bab1 said:**
> 
My network has Windows hosts that talk to Samba.  I also have Linux hosts that talk to Windows shares via smbfs.  I believe now that your probs are the user and/or machine authentication.


That is exactly what it is, since the windows account is being locked out on AD, due to many authentication attempts.

> **bab1 said:**
> 
I might add that the GUI (gvfs) system is mostly broken in Hardy.  People have been complaining for months now.  I'll bet that's why you can find the shares using the command line.

This might be the case... I think I will just forget about it for now (wait for bug fix) -- since I can access the files and can use smbclient to list when needed.

---

### Post by in0ni on 2008-08-27
bug report: [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072)

---

