---
title: "nmblookup fails on certain machines"
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by MerceanCoconut on 2008-03-28
Hello,

I am trying to access a Windows share on a Windows XP box named "lab1".  nmblookup works on all other machines (Windows Vista) on the network except for "lab1".  I can access the shared directory by browsing to the IP address (smb://10.14.34.12), but smb://lab1 does not work.   I would appreciate any help and suggestions.  Output from smbtree and nmblookup commands are below:

chris@chris-laptop:~$ smbtree
Password:
session request to 10.14.34.13 failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
session request to 10.14.34.13 failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
WORKGROUP
session request to 10.14.34.13 failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
        \\PERRY-PC
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine PERRY-PC.  Error was NT_STATUS_ACCESS_DENIED
        \\LAB1
cli_start_connection: failed to connect to LAB1<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME
        \\BRN0068AE
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine BRN0068AE.  Error was ERRSRV - 22
                \\BRN0068AE\IPC$                IPC Service ()
                \\BRN0068AE\BINARY_P1           NetBIOS Port



chris@chris-laptop:~$ nmblookup lab1
querying lab1 on 10.14.34.255
name_query failed to find name lab1

chris@chris-laptop:~$ nmblookup BRN0068AE
querying BRN0068AE on 10.14.34.255
10.14.34.11 BRN0068AE<00>

---

### Post by Eiríkr on 2008-03-28
Not sure why, but XP seems problematic in certain situations.  [post=4604979]This post[/post] remarks on a possible hostname-related bug in XP systems.

Anyone know of any solutions?

Cheers,

Eiríkr

---

