---
title: "(error code 0x0000251E DNS_ERROR_BAD_PACKET)"
date: 2015-11-19
forum: Networking &amp; Wireless
---

### Post by n3wguys on 2015-11-19
Dear All,

I have 10 pc and 1 ubuntu server 14.10., and this is already install 1 year ago the AD DC in Ubuntu server 14.10 and 10 client was registered to server.
today I faced one problem, one client could not log in into their PC with user id and password. the system show "username and password is incorrect". I try log in with administrator account, there was success to log in. after it, I moved to log out,and try again with user id of client but still not yet incorrect. the next, I try again to log in with administrator account , the pc client is reject. collusion is:

login into PC Client (Windows 7 and already registered to Ubuntu server 14.10 1 year ago)
1. Log into PC Client with user id and password client is reject.
2. Try login with administrator id and password is success in PC Client.
3. Logout from PC client again and try step 1.
4. Try step 2, is reject
5. I have removed the LAN Cable from PC and log in with administrator account.
6. Remove the domain name from PC Client and setup to default Windows(Workgroup)
7. after it, I try to register again and the system show

```
An error occurred when DNS was queried for the service location(SRV) resource record used to locate an 
Active Directory Domain Controller(AD DC) for domain "xxxx.internal"
The error was: "Bad DNS packet."
 (error code 0x0000251E DNS_ERROR_BAD_PACKET) 
The query was for the SRV record for _ldap._tcp.dc._msdcs.xxxx.internal

```

and meantime I can't join again this PC Client to Ubuntu Server 14.10.


Notice:
4 Windows XP, 4 Windows 7, 2 Ubuntu 14 Desktop
1 PC Server : Ubuntu Server 14.10 (AD DC)
the one of PC client could not be registered to Ubuntu Server 14.10 is Windows 7

Please help me

---

