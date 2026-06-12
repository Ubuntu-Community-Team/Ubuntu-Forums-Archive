---
title: "Can't join domain with Likewise"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by vairoj on 2008-05-23
I'm trying to join my Ubuntu Desktop 8.04 machine to an active directory running on Windows 2000 Server by using Likewise. Using both gui and cli mode, there are both errors with the following message:

```

vairoj@yap:~$ sudo domainjoin-cli join example.com Administrator
Joining to AD Domain:   example.com
With Computer DNS Name: yap.example.com

Administrator@EXAMPLE.COM's password: 
Could not connect to server WAVEONE.example.com
Connection failed: NT_STATUS_NOLOGON_WORKSTATION_TRUST_ACCOUNT
Failed to verify membership in domain: NT_STATUS_NOLOGON_WORKSTATION_TRUST_ACCOUNT!

Error: Unable to join domain [code 0x0008000e]

Creating the computer account in Active Directory failed. Common causes are a
bad administrator password, a bad OU name, or an existing computer account but
not modificiation permissions.

```

Note that the actual domain name is replaced with example.com.

It seems like the computer was partially created on the domain, as the computer name (yap) is shown in Active Directory Management Console on Windows. Though, all the information are blank.

The username/password are definitely correct as they're used to join other Windows computers to the active directory domain without any problem.

Do you have any idea how could I troubleshoot this issue?

---

### Post by stewski on 2008-06-05
Did anyone ever get to the bottom of this
I have the same error on hardy 8.04?

---

### Post by fisho on 2008-06-10
this would be good if some 1 had a answer for this as i'de like to connect my laptop to the domain as well. 

or is there a tutorial on here for 8.04 and win2003

---

### Post by JaxDomino on 2008-06-17
Does Likewise even work with windows 2000?  I am having the same issue.  But when I join to a Windows 2003 server it works!

---

### Post by jamessnell on 2008-06-23
I'm having the same problem with 8.04 & Win2K3 Server.

More than anything I'm rather desperate to discover if this is just a config error on my part, or something deeper?

---

### Post by revchris on 2008-09-24
Has anyone figured this out?  I'm having the exact same problem.

---

### Post by likeWiseGuy on 2008-10-01
> **vairoj said:**
> I'm trying to join my Ubuntu Desktop 8.04 machine to an active directory running on Windows 2000 Server by using Likewise. Using both gui and cli mode, there are both errors with the following message:

```

vairoj@yap:~$ sudo domainjoin-cli join example.com Administrator
Joining to AD Domain:   example.com
With Computer DNS Name: yap.example.com

Administrator@EXAMPLE.COM's password: 
Could not connect to server WAVEONE.example.com
Connection failed: NT_STATUS_NOLOGON_WORKSTATION_TRUST_ACCOUNT
Failed to verify membership in domain: NT_STATUS_NOLOGON_WORKSTATION_TRUST_ACCOUNT!

Error: Unable to join domain [code 0x0008000e]

Creating the computer account in Active Directory failed. Common causes are a
bad administrator password, a bad OU name, or an existing computer account but
not modificiation permissions.

```

Note that the actual domain name is replaced with example.com.

It seems like the computer was partially created on the domain, as the computer name (yap) is shown in Active Directory Management Console on Windows. Though, all the information are blank.

The username/password are definitely correct as they're used to join other Windows computers to the active directory domain without any problem.

Do you have any idea how could I troubleshoot this issue?

Hi, vairoj.

Please let me know how things are going with your domain join and authentication. 

If you would like to do further troubleshooting, try the following:

1. [http://lists-archives.org/samba/34051-net-ads-join-fails-with-nt_status_nologon_workstation_trust_account.html](http://lists-archives.org/samba/34051-net-ads-join-fails-with-nt_status_nologon_workstation_trust_account.html)
The computer account appears to be created using the administrator creds. The join then fails because the computer account appears to have insufficient permissions in the domain. You can verify this by checking whether the computer account was created in AD. 

2. You can also get verbose logging information from the domain join by performing the following command:
domainjoin-cli --loglevel verbose --log /tmp/domainjoin.log join <domain fqdn> <user account>

Review the log at /tmp/domainjoin.log and, if you'd like, share the last few lines of the log in this thread.

Let me know if I can provide you with further information.

---

