---
title: "kerberos and nfs4"
date: 2008-07-21
forum: Networking &amp; Wireless
---

### Post by merkelml on 2008-07-21
Hi, 

I have an issue with ubuntu 8.04 clients. I have set up an ubuntu 8.04 server (AMD64) which is a kerberos server and nfs server. The home directories are mounted via nfs4 with kerberos encryption and security:

myserver:/home /home nfs4 exec,rw,sec=krb5p,hard,intr 0 

The mounts are working fine. I had/have no problem with mounting the /homes until I upgraded the clients and server from 7.10 to 8.04. After the upgrade I get tons of the following messages in daemon.log in the clients (debugging enabled to get a clue what is going on). But mounting still works.

A user logs on (in this case the one with uid 1001) which can sucessfully log on and work. What I don't understand why does rpc.gssd try to login user with uid 1003. He is not even in the office.

Jul 21 11:13:22 e6750 rpc.gssd[5825]: handling krb5 upcall 
Jul 21 11:13:22 e6750 rpc.gssd[5825]: getting credentials for client with uid 1003 for server myserver 
Jul 21 11:13:22 e6750 rpc.gssd[5825]: CC file 'krb5cc_1001_QkOZ4a' being considered 
Jul 21 11:13:22 e6750 rpc.gssd[5825]: '/tmp/krb5cc_1001_QkOZ4a' owned by 1001, not 1003 
Jul 21 11:13:22 e6750 rpc.gssd[5825]: using FILE:/tmp/krb5cc_1003 as credentials cache for client with uid 1003 for server myserver 
Jul 21 11:13:22 e6750 rpc.gssd[5825]: using environment variable to select krb5 ccache FILE:/tmp/krb5cc_1003 
Jul 21 11:13:22 e6750 rpc.gssd[5825]: creating context using fsuid 1003 (save_uid 0) 
Jul 21 11:13:22 e6750 rpc.gssd[5825]: ERROR: GSS-API: error in gss_acquire_cred(): Unspecified GSS failure.  Minor code may provide more information - No credentials cache found 
Jul 21 11:13:22 e6750 rpc.gssd[5825]: WARNING: Failed while limiting krb5 encryption types for user with uid 1003 
Jul 21 11:13:22 e6750 rpc.gssd[5825]: WARNING: Failed to create krb5 context for user with uid 1003 for server myserver
Jul 21 11:13:22 e6750 rpc.gssd[5825]: doing error downcall 
Jul 21 11:13:22 e6750 rpc.gssd[5825]: Failed to write error downcall! 


and

Jul 18 09:43:32 e6750 rpc.gssd[5808]: handling krb5 upcall 
Jul 18 09:43:32 e6750 rpc.gssd[5808]: getting credentials for client with uid 1003 for server myserver
Jul 18 09:43:32 e6750 rpc.gssd[5808]: CC file 'krb5cc_1001_bWky9v' being considered 
Jul 18 09:43:32 e6750 rpc.gssd[5808]: '/tmp/krb5cc_1001_bWky9v' owned by 1001, not 1003 
Jul 18 09:43:32 e6750 rpc.gssd[5808]: using FILE:/tmp/krb5cc_1003 as credentials cache for client with uid 1003 for server myserver
Jul 18 09:43:32 e6750 rpc.gssd[5808]: using environment variable to select krb5 ccache FILE:/tmp/krb5cc_1003 
Jul 18 09:43:32 e6750 rpc.gssd[5808]: creating context using fsuid 1003 (save_uid 0) 
Jul 18 09:43:32 e6750 rpc.gssd[5808]: ERROR: GSS-API: error in gss_acquire_cred(): Unspecified GSS failure.  Minor code may provide more information - No credentials cache found 
Jul 18 09:43:32 e6750 rpc.gssd[5808]: WARNING: Failed while limiting krb5 encryption types for user with uid 1003 
Jul 18 09:43:32 e6750 rpc.gssd[5808]: WARNING: Failed to create krb5 context for user with uid 1003 for server myserver 
Jul 18 09:43:32 e6750 rpc.gssd[5808]: doing error downcall 
Jul 18 09:43:32 e6750 rpc.gssd[5808]: Failed to write error downcall! 



Usually every few milliseconds the login is repeated with the same results. Then out of nothing there is quiet for a couple of hours.


Can anyone shed some light into this? There are no crontabs for the user with 1003  so I don't understand the login attemps. This happens with multiple clients and multiple users.

This would not be a big deal but from time to time the nfs mount "dies" (desktop freezes partially), logout and logon fixes the issue. I haven't found anything useful in the logs beside tons of the posted error messages which might cloak the real problem.

Any help would be appreciated.

Marcel

---

