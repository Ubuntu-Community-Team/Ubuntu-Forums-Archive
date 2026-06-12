---
title: "ubuntu 11.04 samba as pdc (Primary Domain Controller)"
date: 2011-07-06
forum: New to Ubuntu
---

### Post by lance bermudez on 2011-07-06
following [https://help.ubuntu.com/10.04/serverguide/C/samba-dc.html](https://help.ubuntu.com/10.04/serverguide/C/samba-dc.html)

want profiles left on windows but want windows user when they logong to map to a samba share. gufw is turned off for right now. Have attached my smb.conf

lance@Therese:/etc/samba$ net rpc rights grant "LBERMUDEZ\Domain Admins" SeMachineAccountPrivilege SePrintOperatorPrivilege SeAddUsersPrivilege SeDiskOperatorPrivilege SeRemoteShutdownPrivilege
Enter lance's password:
Could not connect to server 127.0.0.1
The username or password was not correct.
Connection failed: NT_STATUS_LOGON_FAILURE

what did i do wrong?

---

### Post by lance bermudez on 2011-07-07
found new guid at [https://help.ubuntu.com/11.04/serverguide/C/samba-dc.html](https://help.ubuntu.com/11.04/serverguide/C/samba-dc.html)
lance@Therese:~$ net rpc rights grant -U lance "EXAMPLE\Domain Admins" SeMachineAccountPrivilege SePrintOperatorPrivilege SeAddUsersPrivilege SeDiskOperatorPrivilege SeRemoteShutdownPrivilege
Enter lance's password:
Failed to grant privileges for EXAMPLE\Domain Admins (NT_STATUS_NO_SUCH_USER)
lance@Therese:~$ net rpc rights grant -U lance "LBERMUDEZ\Domain Admins" SeMachineAccountPrivilege SePrintOperatorPrivilege SeAddUsersPrivilege SeDiskOperatorPrivilege SeRemoteShutdownPrivilege
Enter lance's password:
Could not connect to server 127.0.0.1
The username or password was not correct.
Connection failed: NT_STATUS_LOGON_FAILURE
lance@Therese:~$ sudo net rpc rights grant -U lance "LBERMUDEZ\Domain Admins" SeMachineAccountPrivilege SePrintOperatorPrivilege SeAddUsersPrivilege SeDiskOperatorPrivilege SeRemoteShutdownPrivilege
[sudo] password for lance: 
Enter lance's password:
Failed to grant privileges for LBERMUDEZ\Domain Admins (NT_STATUS_NO_SUCH_USER)
lance@Therese:~$ net -U lance rpc rights grant "EXAMPLE\Domain Admins" SeMachineAccountPrivilege SePrintOperatorPrivilege SeAddUsersPrivilege SeDiskOperatorPrivilege SeRemoteShutdownPrivilege
Enter lance's password:
Failed to grant privileges for EXAMPLE\Domain Admins (NT_STATUS_NO_SUCH_USER)

---

### Post by lance bermudez on 2011-07-12
could some one help please? I'm trying to connnect a windows 7 pro to the samba domain.

I have used some thing from this video along with what i have already said above.
[http://www.youtube.com/watch?v=8MWBhlaLIxQ](http://www.youtube.com/watch?v=8MWBhlaLIxQ)

I get this on the windows 7 computer
An Active Directory Domain Controller (AD DC) for the domain "lbermudez" could not be contracted.

Ensure that the domain name is typed correctly.

If the name is correct, click Details for troubleshooting information.



Note: This information is intended for a network administrator.  If you are not your network's administrator, notify the administrator that you received this information, which has been recorded in the file C:\Windows\debug\dcdiag.txt.



The domain name "lbermudez" might be a NetBIOS domain name.  If this is the case, verify that the domain name is properly registered with WINS.



If you are certain that the name is not a NetBIOS domain name, then the following information can help you troubleshoot your DNS configuration.



The following error occurred when DNS was queried for the service location (SRV) resource record used to locate an Active Directory Domain Controller (AD DC) for domain "lbermudez":



The error was: "DNS name does not exist."

(error code 0x0000232B RCODE_NAME_ERROR)



The query was for the SRV record for _ldap._tcp.dc._msdcs.lbermudez



Common causes of this error include the following:



- The DNS SRV records required to locate a AD DC for the domain are not registered in DNS. These records are registered with a DNS server automatically when a AD DC is added to a domain. They are updated by the AD DC at set intervals. This computer is configured to use DNS servers with the following IP addresses:



192.168.2.1



- One or more of the following zones do not include delegation to its child zone:



lbermudez

. (the root zone)


attached is my smb.conf and samba logs

---

