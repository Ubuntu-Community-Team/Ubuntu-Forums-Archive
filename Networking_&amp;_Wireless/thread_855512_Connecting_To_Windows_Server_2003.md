---
title: "Connecting To Windows Server 2003"
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by Kileli on 2008-07-10
i have been given the task of spear heading the switch from windows to Linux for my company.(scary considering i have only been using the system for 3 days) They have asked me to see if we can use ubuntu and still run our windows based software(televantage 7, Microsoft office, and some other programs.the problem i am having right now is that i cannot figure out how to get my Ubuntu OS on the windows network. i have samba installed and like wise so i know this machine is on our domain but i cannot see any of the other machines in the neighbor hood network viewer. I know there has to be someone out there that has been faced with a similar dilemma. Please any advice would be helpful. is there a Upnp controller or a way to join the windows network in this way? i just cant seam to get samba configure right

---

### Post by dmizer on 2008-07-11
see the second link in my sig.

---

### Post by Kileli on 2008-07-11
Ok now i can see the work groups on my network and i can see all the windows machines on the network but i cannot see the share folders within those computers i read somewhere that you cannot see them in ubuntu 8.04 and that you have to directly access the folders but it doest look like i can do that either. i admit i am completely new to Linux. i just cant seem to get my Linux machine to coexist inside the windows network

---

### Post by dmizer on 2008-07-11
first of all ... what command (or fstab line) did you use to mount the share?

please post the output of:
```
smbtree
```

finally, post the output of the following two commands:
```
sudo mount -a
dmesg | tail
```

---

### Post by Kileli on 2008-07-11
i just removed winbind and samba in an attempt to start over
when i checked the network i am still able to see all the machines within the windows network i have 3 work groups and 1 domain. i am able to access all the workgroups shares just fine its the domain that i cannot see the share folders in. do i really need samba and winbind installed. it appears as though i just need to authenticate my presence in the domain. is this accurate?

---

### Post by Kileli on 2008-07-11
> **dmizer said:**
> first of all ... what command (or fstab line) did you use to mount the share?

please post the output of:
```
smbtree
```

finally, post the output of the following two commands:
```
sudo mount -a
dmesg | tail
```

WORKGROUP
NOMOREMORTGAGE
	\\XPE00806460A034		
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine XPE00806460A034.  Error was NT_STATUS_ACCESS_DENIED
	\\UWORKSTAION1   		
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine UWORKSTAION1.  Error was NT_STATUS_ACCESS_DENIED
	\\UT106-CLADOW-LT		Clark's Windows Laptop
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine UT106-CLADOW-LT.  Error was NT_STATUS_ACCESS_DENIED
	\\UT106-508906-DT		
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine UT106-508906-DT.  Error was NT_STATUS_ACCESS_DENIED
	\\UT106-508647-DT

---

### Post by dmizer on 2008-07-11
is your windows network an active domain?

---

### Post by Kileli on 2008-07-12
Yes its an active domain with roaming user profiles

---

### Post by dmizer on 2008-07-12
take a look at this thread then: [http://ubuntuforums.org/showthread.php?t=91510](http://ubuntuforums.org/showthread.php?t=91510)

---

