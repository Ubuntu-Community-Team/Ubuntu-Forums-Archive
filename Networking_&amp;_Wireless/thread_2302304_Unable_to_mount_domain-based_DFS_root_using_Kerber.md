---
title: "Unable to mount domain-based DFS root using Kerberos on Ubuntu 14.04 LTS"
date: 2015-11-09
forum: Networking &amp; Wireless
---

### Post by Craig_Tolley on 2015-11-09
Hi, 

I am trying to mount a Microsoft domain-based DFS path using CIFS and Kerberos in Ubuntu 14.04 LTS. However when I attempt to do this I get the following mount error using the following mount command: 

```
sudo mount -t cifs //mydomainname.co.uk/data/home /mnt/dfshome -o sec=krb5 -vvvv

mount error(126): Required key not available
```

I know why this error occurs - it is because the hostname that is derived from the mount command (HOST/mydomain.co.uk) does not match any principals that have been registered in the Active Directory domain, however, the problem is how to add such a record into the domain. This is clearly shown in the logs: 

```

Nov  9 13:54:41 me-linux cifs.upcall: handle_krb5_mech: getting service ticket for cifs/mydomainname.co.uk
Nov  9 13:54:41 me-linux cifs.upcall: cifs_krb5_get_req: unable to get credentials for cifs/mydomainname.co.uk
Nov  9 13:54:41 me-linux cifs.upcall: handle_krb5_mech: failed to obtain service ticket (-1765328377)
Nov  9 13:54:41 me-linux cifs.upcall: handle_krb5_mech: getting service ticket for host/mydomainname.co.uk
Nov  9 13:54:41 me-linux cifs.upcall: cifs_krb5_get_req: unable to get credentials for host/mydomainname.co.uk
Nov  9 13:54:41 me-linux cifs.upcall: handle_krb5_mech: failed to obtain service ticket (-1765328377)
```

Using NTLM security and specifying the username, domain and password works successfully, the path mounts and is usable.
 
[B]Background Information
[/B]DFS Mount Path: \\mydomainname.co.uk\data\home
DFS Namespace is hosted on multiple domain controllers (3 servers)
Mounting the path directly from any one of the namespace servers directly using Kerberos is successful
Kerberos authentication in general is working, tickets can be granted to clients and used to authenticate against resources across the network. 
DNS forward and reverse records exist and are correct for all servers and clients involved in the process

If I add an SPN to a machine (any machine) in the domain, and then repeat the mount command, the error changes. Instead I get an 

```
mount error(5): Input/output error
```
To evaluate this one I ran a tcpdump of the communications during the mount. This showed that the ticket was being retrieved and used, but failed to be accepted - most likely because the ticket was assigned to a different machine. 

In Active Directory if I add a HOST/mydomainname.co.uk to one of the domain controllers which is acting as a DFS Namespace Server, the record saves but the new value is removed - presumably by the AD services. Similarly I am unable to add the HOST/mydomainname.co.uk SPN to multiple machines in the domain as it believes this to be a duplicate which is not valid. [B]

Version Numbers
[/B]Kernel: 3.13.0-67-generic
mount from util-linux 2.20.1 
mount.cifs version: 5.1[B]

I think the problem either boils down to the lack of a correct SPN in the domain, or a missing option on my mount command. Alternatively I am trying to do something that is not supported or not achievable. Anyone with any experience of doing this?

Articles already read/investigated: [/B]
[LIST]
[*][http://mikemstech.blogspot.co.uk/2012/10/how-to-mount-dfs-share-in-linux.html](http://mikemstech.blogspot.co.uk/2012/10/how-to-mount-dfs-share-in-linux.html) - implies it can be done, but I think is actually using NTLM as the sec=krb5 option is not specified
[*][https://bugzilla.samba.org/show_bug.cgi?id=7257](https://bugzilla.samba.org/show_bug.cgi?id=7257) - a few years old, but seems to imply that it is not possible.
[*][http://forums.fedoraforum.org/showthread.php?t=249327](http://forums.fedoraforum.org/showthread.php?t=249327) - not Ubuntu, but suggests that cifs.upcall should be able to deal with the DFS related parts of the mount process
[*][https://bugs.launchpad.net/ubuntu/+source/cifs-utils/+bug/676525](https://bugs.launchpad.net/ubuntu/+source/cifs-utils/+bug/676525) - vaguely related, but not the same issue as it is pointed directly at the namespace server in the mount command
[*]+ others but many related back to these 4
[/LIST]

---

### Post by Craig_Tolley on 2015-11-24
Anyone got any ideas? Going to follow this up on the Samba mailing lists to see if I get any more luck there.

---

