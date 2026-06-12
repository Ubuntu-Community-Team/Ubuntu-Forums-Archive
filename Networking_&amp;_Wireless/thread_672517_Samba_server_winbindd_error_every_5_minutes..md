---
title: "Samba server winbindd error every 5 minutes."
date: 2008-01-19
forum: Networking &amp; Wireless
---

### Post by PgR on 2008-01-19
Running a Samba PDC on 7.10.

/var/log/syslog is full of 
```
Jan 19 22:03:51 CCHSVRSAMBA1 winbindd[8055]: [2008/01/19 22:03:51, 0] libsmb/clientgen.c:cli_receive_smb(112)
Jan 19 22:03:51 CCHSVRSAMBA1 winbindd[8055]:   Receiving SMB: Server stopped responding
``` and I'd rather it wasn't. They appear in bursts of 3 such messages every 5 minutes, give or take a few seconds.

I've noticed that roughly 5 minutes after winbindd starts it complains about a child process and stops talking to it, but doesn't kill it. Thereafer every 5 minutes the above message appears.

What should I do? It's a pain.

Hope the following is helpful.

Output of ps auxf | grep winbindd
```

root      8055  0.0  0.1   9044  1576 ?        Ss   21:58   0:00 /usr/sbin/winbindd
root      8056  0.0  0.1   9300  1956 ?        S    21:58   0:00  \_ /usr/sbin/winbindd
root      8077  0.0  0.1   9192  1776 ?        S    21:58   0:00  \_ /usr/sbin/winbindd
root      8078  0.0  0.0   9044   952 ?        S    21:58   0:00   \_ /usr/sbin/winbindd

```


/var/log/syslog  (duplicated in /var/log/samba/log.winbind)
```

Jan 19 22:03:20 CCHSVRSAMBA1 winbindd[8078]:   async_request_timeout_handler: child pid 8056 is not responding. Closing connection to it.
Jan 19 22:03:20 CCHSVRSAMBA1 winbindd[8077]: [2008/01/19 22:03:20, 0] nsswitch/winbindd_dual.c:async_request_timeout_handler(181)
Jan 19 22:03:20 CCHSVRSAMBA1 winbindd[8077]:   async_request_timeout_handler: child pid 8056 is not responding. Closing connection to it.
Jan 19 22:03:38 CCHSVRSAMBA1 winbindd[8055]: [2008/01/19 22:03:38, 0] libsmb/clientgen.c:cli_receive_smb(112)
Jan 19 22:03:38 CCHSVRSAMBA1 winbindd[8055]:   Receiving SMB: Server stopped responding
Jan 19 22:03:51 CCHSVRSAMBA1 winbindd[8055]: [2008/01/19 22:03:51, 0] libsmb/clientgen.c:cli_receive_smb(112)
Jan 19 22:03:51 CCHSVRSAMBA1 winbindd[8055]:   Receiving SMB: Server stopped responding
```

Output of netstat -ep
```
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       User       Inode      PID/Program name
tcp        4      0 cchsvrsamba1.mydo:48900 cchsvrsamb:microsoft-ds ESTABLISHEDroot       309025     8056/winbindd
tcp        0      0 cchsvrsamb:microsoft-ds cchsvrsamba1.mydo:48900 ESTABLISHEDroot       309027     8082/smbd
tcp        0      0 cchsvrsamba:netbios-ssn client1.mydomain.co:4584 ESTABLISHEDroot       309014     8080/smbd

```

/var/log/samba/log.smbd   (It's a long sample!)
```
[2008/01/19 22:03:28, 3] smbd/process.c:check_reload(1309)
  Printcap cache time expired.
[2008/01/19 22:03:28, 3] printing/pcap.c:pcap_cache_reload(117)
  reloading printcap cache
[2008/01/19 22:03:28, 3] printing/pcap.c:pcap_cache_reload(223)
  reload status: ok
[2008/01/19 22:03:28, 3] smbd/oplock.c:init_oplocks(863)
  init_oplocks: initializing messages.
[2008/01/19 22:03:28, 3] smbd/oplock_linux.c:linux_init_kernel_oplocks(276)
  Linux kernel oplocks enabled
[2008/01/19 22:03:28, 3] smbd/process.c:process_smb(1068)
  Transaction 0 of length 194
[2008/01/19 22:03:28, 3] smbd/process.c:switch_message(926)
  switch message SMBnegprot (pid 8583) conn 0x0
[2008/01/19 22:03:28, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/01/19 22:03:28, 3] smbd/negprot.c:reply_negprot(505)
  Requested protocol [PC NETWORK PROGRAM 1.0]
[2008/01/19 22:03:28, 3] smbd/negprot.c:reply_negprot(505)
  Requested protocol [MICROSOFT NETWORKS 1.03]
[2008/01/19 22:03:28, 3] smbd/negprot.c:reply_negprot(505)
  Requested protocol [MICROSOFT NETWORKS 3.0]
[2008/01/19 22:03:28, 3] smbd/negprot.c:reply_negprot(505)
  Requested protocol [LANMAN1.0]
[2008/01/19 22:03:28, 3] smbd/negprot.c:reply_negprot(505)
  Requested protocol [LM1.2X002]
[2008/01/19 22:03:28, 3] smbd/negprot.c:reply_negprot(505)
  Requested protocol [DOS LANMAN2.1]
[2008/01/19 22:03:28, 3] smbd/negprot.c:reply_negprot(505)
  Requested protocol [LANMAN2.1]
[2008/01/19 22:03:28, 3] smbd/negprot.c:reply_negprot(505)
  Requested protocol [Samba]
[2008/01/19 22:03:28, 3] smbd/negprot.c:reply_nt1(364)
  using SPNEGO
[2008/01/19 22:03:28, 3] smbd/negprot.c:reply_negprot(606)
  Selected protocol NT LANMAN 1.0
[2008/01/19 22:03:28, 3] smbd/process.c:process_smb(1068)
  Transaction 1 of length 166
[2008/01/19 22:03:28, 3] smbd/process.c:switch_message(926)
  switch message SMBsesssetupX (pid 8583) conn 0x0
[2008/01/19 22:03:28, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/01/19 22:03:28, 3] smbd/sesssetup.c:reply_sesssetup_and_X(1244)
  wct=12 flg2=0xc801
[2008/01/19 22:03:28, 3] smbd/sesssetup.c:reply_sesssetup_and_X_spnego(1029)
  Doing spnego session setup
[2008/01/19 22:03:28, 3] smbd/sesssetup.c:reply_sesssetup_and_X_spnego(1060)
  NativeOS=[Unix] NativeLanMan=[Samba] PrimaryDomain=[]
[2008/01/19 22:03:28, 3] smbd/sesssetup.c:reply_spnego_negotiate(697)
  reply_spnego_negotiate: Got secblob of size 47
[2008/01/19 22:03:28, 3] libsmb/ntlmssp.c:debug_ntlmssp_flags(63)
  Got NTLMSSP neg_flags=0x60088215
[2008/01/19 22:03:28, 3] smbd/process.c:process_smb(1068)
  Transaction 2 of length 234
[2008/01/19 22:03:28, 3] smbd/process.c:switch_message(926)
  switch message SMBsesssetupX (pid 8583) conn 0x0
[2008/01/19 22:03:28, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/01/19 22:03:28, 3] smbd/sesssetup.c:reply_sesssetup_and_X(1244)
  wct=12 flg2=0xc801
[2008/01/19 22:03:28, 3] smbd/sesssetup.c:reply_sesssetup_and_X_spnego(1029)
  Doing spnego session setup
[2008/01/19 22:03:28, 3] smbd/sesssetup.c:reply_sesssetup_and_X_spnego(1060)
  NativeOS=[Unix] NativeLanMan=[Samba] PrimaryDomain=[]
[2008/01/19 22:03:28, 3] libsmb/ntlmssp.c:ntlmssp_server_auth(739)
  Got user=[CCHSVRSAMBA1$] domain=[CCH] workstation=[CCHSVRSAMBA1] len1=0 len2=0
[2008/01/19 22:03:28, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2008/01/19 22:03:28, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2008/01/19 22:03:28, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/01/19 22:03:28, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/01/19 22:03:28, 3] auth/auth.c:check_ntlm_password(221)
  check_ntlm_password:  Checking password for unmapped user [CCH]\[CCHSVRSAMBA1$]@[CCHSVRSAMBA1] with the new password interface
[2008/01/19 22:03:28, 3] auth/auth.c:check_ntlm_password(224)
  check_ntlm_password:  mapped user is: [CCH]\[CCHSVRSAMBA1$]@[CCHSVRSAMBA1]
[2008/01/19 22:03:28, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2008/01/19 22:03:28, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2008/01/19 22:03:28, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/01/19 22:03:28, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/01/19 22:03:28, 3] auth/auth_sam.c:check_sam_security(281)
  check_sam_security: Couldn't find user 'CCHSVRSAMBA1$' in passdb.
[2008/01/19 22:03:28, 3] auth/auth_winbind.c:check_winbind_security(80)
  check_winbind_security: Not using winbind, requested domain [CCH] was for this SAM.
[2008/01/19 22:03:28, 2] auth/auth.c:check_ntlm_password(319)
  check_ntlm_password:  Authentication for user [CCHSVRSAMBA1$] -> [CCHSVRSAMBA1$] FAILED with error NT_STATUS_NO_SUCH_USER
[2008/01/19 22:03:28, 3] smbd/error.c:error_packet_set(106)
  error packet at smbd/sesssetup.c(105) cmd=115 (SMBsesssetupX) NT_STATUS_LOGON_FAILURE
[2008/01/19 22:03:28, 3] smbd/process.c:process_smb(1068)
  Transaction 3 of length 92
[2008/01/19 22:03:28, 3] smbd/process.c:switch_message(926)
  switch message SMBsesssetupX (pid 8583) conn 0x0
[2008/01/19 22:03:28, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/01/19 22:03:28, 3] smbd/sesssetup.c:reply_sesssetup_and_X(1244)
  wct=13 flg2=0xc801
[2008/01/19 22:03:28, 3] smbd/sesssetup.c:reply_sesssetup_and_X(1390)
  Domain=[]  NativeOS=[Unix] NativeLanMan=[Samba] PrimaryDomain=[]
[2008/01/19 22:03:28, 3] smbd/sesssetup.c:reply_sesssetup_and_X(1405)
  sesssetupX:name=[]\[]@[cchsvrsamba1]
[2008/01/19 22:03:28, 3] smbd/sesssetup.c:check_guest_password(142)
  Got anonymous request
[2008/01/19 22:03:28, 3] auth/auth.c:check_ntlm_password(221)
  check_ntlm_password:  Checking password for unmapped user []\[]@[] with the new password interface
[2008/01/19 22:03:28, 3] auth/auth.c:check_ntlm_password(224)
  check_ntlm_password:  mapped user is: []\[]@[]
[2008/01/19 22:03:28, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2008/01/19 22:03:28, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2008/01/19 22:03:28, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/01/19 22:03:28, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2008/01/19 22:03:28, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2008/01/19 22:03:28, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2008/01/19 22:03:28, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/01/19 22:03:28, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/01/19 22:03:28, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2008/01/19 22:03:28, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2008/01/19 22:03:28, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/01/19 22:03:28, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/01/19 22:03:28, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2008/01/19 22:03:28, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2008/01/19 22:03:28, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/01/19 22:03:28, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/01/19 22:03:28, 3] auth/auth.c:check_ntlm_password(270)
  check_ntlm_password: guest authentication for user [] succeeded
[2008/01/19 22:03:28, 3] passdb/lookup_sid.c:fetch_gid_from_cache(1089)
  fetch gid from cache 15000 -> S-1-5-32-544
[2008/01/19 22:03:28, 3] passdb/lookup_sid.c:fetch_gid_from_cache(1089)
  fetch gid from cache 15001 -> S-1-5-32-545
[2008/01/19 22:03:28, 3] lib/privileges.c:get_privileges(261)
  get_privileges: No privileges assigned to SID [S-1-5-21-1847232298-597593696-534341723-501]
[2008/01/19 22:03:28, 3] lib/privileges.c:get_privileges(261)
  get_privileges: No privileges assigned to SID [S-1-5-2]
[2008/01/19 22:03:28, 3] lib/privileges.c:get_privileges(261)
  get_privileges: No privileges assigned to SID [S-1-5-32-546]
[2008/01/19 22:03:28, 3] smbd/oplock.c:init_oplocks(863)
  init_oplocks: initializing messages.
[2008/01/19 22:03:28, 3] smbd/oplock_linux.c:linux_init_kernel_oplocks(276)
  Linux kernel oplocks enabled
[2008/01/19 22:03:28, 3] smbd/process.c:timeout_processing(1328)
  timeout_processing: End of file from client (client has disconnected).
[2008/01/19 22:03:28, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/01/19 22:03:28, 3] smbd/connection.c:yield_connection(69)
  Yielding connection to 
[2008/01/19 22:03:28, 3] smbd/connection.c:yield_connection(76)
  yield_connection: tdb_delete for name  failed with error Record does not exist.
[2008/01/19 22:03:28, 3] smbd/server.c:exit_server_common(768)
  Server exit (normal exit)
[2008/01/19 22:03:30, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/01/19 22:03:38, 3] smbd/oplock.c:init_oplocks(863)
  init_oplocks: initializing messages.
[2008/01/19 22:03:38, 3] smbd/oplock_linux.c:linux_init_kernel_oplocks(276)
  Linux kernel oplocks enabled
[2008/01/19 22:03:38, 3] smbd/oplock.c:init_oplocks(863)
  init_oplocks: initializing messages.
[2008/01/19 22:03:38, 3] smbd/oplock_linux.c:linux_init_kernel_oplocks(276)
  Linux kernel oplocks enabled
[2008/01/19 22:03:38, 3] smbd/process.c:timeout_processing(1328)
  timeout_processing: End of file from client (client has disconnected).
[2008/01/19 22:03:38, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/01/19 22:03:38, 3] smbd/connection.c:yield_connection(69)
  Yielding connection to 
[2008/01/19 22:03:38, 3] smbd/connection.c:yield_connection(76)
  yield_connection: tdb_delete for name  failed with error Record does not exist.
[2008/01/19 22:03:38, 3] smbd/server.c:exit_server_common(768)
  Server exit (normal exit)
[2008/01/19 22:03:40, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/01/19 22:03:41, 3] smbd/process.c:process_smb(1068)
  Transaction 0 of length 194
[2008/01/19 22:03:41, 3] smbd/process.c:switch_message(926)
  switch message SMBnegprot (pid 8594) conn 0x0

```

---

### Post by Hanno on 2008-02-28
bump

---

### Post by porbas on 2008-02-28
> **PgR said:**
> Running a Samba PDC on 7.10.

/var/log/samba/log.smbd   (It's a long sample!)
```

[2008/01/19 22:03:28, 3] auth/auth_sam.c:check_sam_security(281)
  check_sam_security: Couldn't find user 'CCHSVRSAMBA1$' in passdb.
[2008/01/19 22:03:28, 3] auth/auth_winbind.c:check_winbind_security(80)
  check_winbind_security: Not using winbind, requested domain [CCH] was for this SAM.
[2008/01/19 22:03:28, 2] auth/auth.c:check_ntlm_password(319)
  check_ntlm_password:  Authentication for user [CCHSVRSAMBA1$] -> [CCHSVRSAMBA1$] FAILED with error NT_STATUS_NO_SUCH_USER

```

There is no workstation account for your server in CCH domain. I don't know if it helps but try join CCHSVRSAMBA1 to selfcontrolled domain CCH:
```

sudo net join -S CCHSVRSAMBA1 -U admin_name%admin_password

```

I think winbind is useless in your configuration (one and only one samba PDC server). Maybe it was started because of lack of CCHSVRSAMBA1 server account in domain? Try to kill winbind and restart samba.

```

sudo killall winbindd
sudo /etc/init.d/samba restart

```

best regards

---

