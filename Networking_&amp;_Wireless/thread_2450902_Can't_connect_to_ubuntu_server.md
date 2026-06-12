---
title: "Can't connect to ubuntu server"
date: 2020-09-23
forum: Networking &amp; Wireless
---

### Post by debcal on 2020-09-23
Good day. I have Ubuntu 18.04.2 LTS running my server. I have multiple Windows 10 PC's that need to access the server. I am using Bash on my PC to access and administer commands on the server via the network. My PC has no problem in accessing the server via Windows Explorer either. 

Another PC had a factory reset done and since then it can no longer access the server. I can see the server via the network in Windows Explorer. However when I click on the server it says "Error code 0x80070035 The network path was not found". When clicking troubleshoot in Windows 10 it says it cannot identify the problem. The detailed information says that no issues are detected. This PC was previously able to access the server.

I have activated the SMB 1.0/cifs file sharing support feature on the Windows PC. In the windows command prompt I can successfully ping the IP of the server.

I have limited linux experience (server was setup by someone else). How can I get this machine to access the server again?

---

### Post by TheFu on 2020-09-23
Please don't use NT1.  Samba supports smb3 easily which is both fast and has better security. However, Microsoft patched some security issues a few months ago which are pretty serious - the US DoD mandated that all their systems be patched for these specific issues by Sept 21, 2020. It was serious - take-over the entire AD Domain - serious.

If all you need it access, might I suggest using ssh and sftp tools instead of fighting with CIFS bug fixes that are coming out randomly from MSFT?
Load up **WinSCP** on Windows. Run openssh-server on Ubuntu. WinSCP can connect using ssh-keys or ssh credentials. It "just works" and avoids the unavoidable MSFT patching which breaks CIFS connections.

If you are stuck using CIFS/Samba, Morbius1's Samba instructions:  [https://ubuntuforums.org/showthread.php?t=2434383](https://ubuntuforums.org/showthread.php?t=2434383)
There are times when Samba connections are the best answer, but there are always alternatives. Plus, these alternatives can be used safely over the internet, unlike samba/CIFS.

---

