---
title: "SAMBA issue with my bizhub scanner"
date: 2008-07-22
forum: Networking &amp; Wireless
---

### Post by lil_elvis2000 on 2008-07-22
I have a problem between my konica-minolta bizhub scanner and its send-to-smb function. It works fine to the other Windows PCs. but does
not work to the SAMBA shares on the Ubuntu machine. I have got around
this by using FTP (the scanner supports send-to-FTP).

I have increased the SAMBA log level to 3 and here is the output:

[HTML]<code>
[2008/07/22 11:24:06, 3] smbd/process.c:process_smb(1069)
  Transaction 1 of length 62
[2008/07/22 11:24:06, 3] smbd/process.c:switch_message(927)
  switch message SMBnegprot (pid 15668) conn 0x0
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/07/22 11:24:06, 3] smbd/negprot.c:reply_negprot(505)
  Requested protocol [LANMAN1.0]
[2008/07/22 11:24:06, 3] smbd/negprot.c:reply_negprot(505)
  Requested protocol [NT LM 0.12]
[2008/07/22 11:24:06, 3] smbd/negprot.c:reply_nt1(351)
  not using SPNEGO
[2008/07/22 11:24:06, 3] smbd/negprot.c:reply_negprot(606)
  Selected protocol NT LM 0.12
[2008/07/22 11:24:06, 3] smbd/process.c:process_smb(1069)
  Transaction 2 of length 224
[2008/07/22 11:24:06, 3] smbd/process.c:switch_message(927)
  switch message SMBsesssetupX (pid 15668) conn 0x0
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/07/22 11:24:06, 3] smbd/sesssetup.c:reply_sesssetup_and_X(1253)
  wct=13 flg2=0x8001
[2008/07/22 11:24:06, 3] smbd/sesssetup.c:reply_sesssetup_and_X(1399)
  Domain=[]  NativeOS=[KONICA MINOLTA OS 1.0] NativeLanMan=[KONICA MINOLTA LANMAN 1.0] PrimaryDomain=[]
[2008/07/22 11:24:06, 2] smbd/sesssetup.c:setup_new_vc_session(1209)
  setup_new_vc_session: New VC == 0, if NT4.x compatible we would close all old resources.
[2008/07/22 11:24:06, 3] smbd/sesssetup.c:reply_sesssetup_and_X(1414)
  sesssetupX:name=[]\[salik]@[kmbt835dc8]
[2008/07/22 11:24:06, 3] auth/auth.c:check_ntlm_password(221)
  check_ntlm_password:  Checking password for unmapped user []\[salik]@[kmbt835dc8] with the new password interface
[2008/07/22 11:24:06, 3] auth/auth.c:check_ntlm_password(224)
  check_ntlm_password:  mapped user is: [CHAMRAID01]\[salik]@[kmbt835dc8]
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2008/07/22 11:24:06, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2008/07/22 11:24:06, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2008/07/22 11:24:06, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2008/07/22 11:24:06, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2008/07/22 11:24:06, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2008/07/22 11:24:06, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2008/07/22 11:24:06, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2008/07/22 11:24:06, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2008/07/22 11:24:06, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2008/07/22 11:24:06, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2008/07/22 11:24:06, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2008/07/22 11:24:06, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2008/07/22 11:24:06, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2008/07/22 11:24:06, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2008/07/22 11:24:06, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2008/07/22 11:24:06, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2008/07/22 11:24:06, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2008/07/22 11:24:06, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2008/07/22 11:24:06, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/07/22 11:24:06, 3] auth/auth.c:check_ntlm_password(270)
  check_ntlm_password: sam authentication for user [salik] succeeded
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/07/22 11:24:06, 2] auth/auth.c:check_ntlm_password(309)
  check_ntlm_password:  authentication for user [salik] -> [salik] -> [salik] succeeded
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/07/22 11:24:06, 3] lib/privileges.c:get_privileges(261)
  get_privileges: No privileges assigned to SID [S-1-5-21-1011972055-1388681995-1597502561-3000]
[2008/07/22 11:24:06, 3] lib/privileges.c:get_privileges(261)
  get_privileges: No privileges assigned to SID [S-1-22-2-1000]
[2008/07/22 11:24:06, 3] lib/privileges.c:get_privileges(261)
  get_privileges: No privileges assigned to SID [S-1-5-2]
[2008/07/22 11:24:06, 3] lib/privileges.c:get_privileges(261)
  get_privileges: No privileges assigned to SID [S-1-5-11]
[2008/07/22 11:24:06, 3] lib/privileges.c:get_privileges(261)
  get_privileges: No privileges assigned to SID [S-1-22-2-4]
[2008/07/22 11:24:06, 3] lib/privileges.c:get_privileges(261)
  get_privileges: No privileges assigned to SID [S-1-22-2-20]
[2008/07/22 11:24:06, 3] lib/privileges.c:get_privileges(261)
  get_privileges: No privileges assigned to SID [S-1-22-2-24]
[2008/07/22 11:24:06, 3] lib/privileges.c:get_privileges(261)
  get_privileges: No privileges assigned to SID [S-1-22-2-25]
[2008/07/22 11:24:06, 3] lib/privileges.c:get_privileges(261)
  get_privileges: No privileges assigned to SID [S-1-22-2-29]
[2008/07/22 11:24:06, 3] lib/privileges.c:get_privileges(261)
  get_privileges: No privileges assigned to SID [S-1-22-2-30]
[2008/07/22 11:24:06, 3] lib/privileges.c:get_privileges(261)
  get_privileges: No privileges assigned to SID [S-1-22-2-44]
[2008/07/22 11:24:06, 3] lib/privileges.c:get_privileges(261)
  get_privileges: No privileges assigned to SID [S-1-22-2-46]
[2008/07/22 11:24:06, 3] lib/privileges.c:get_privileges(261)
  get_privileges: No privileges assigned to SID [S-1-22-2-107]
[2008/07/22 11:24:06, 3] lib/privileges.c:get_privileges(261)
  get_privileges: No privileges assigned to SID [S-1-22-2-111]
[2008/07/22 11:24:06, 3] lib/privileges.c:get_privileges(261)
  get_privileges: No privileges assigned to SID [S-1-22-2-112]
[2008/07/22 11:24:06, 3] lib/privileges.c:get_privileges(261)
  get_privileges: No privileges assigned to SID [S-1-22-2-113]
[2008/07/22 11:24:06, 3] lib/privileges.c:get_privileges(261)
  get_privileges: No privileges assigned to SID [S-1-22-2-1002]
[2008/07/22 11:24:06, 3] lib/privileges.c:get_privileges(261)
  get_privileges: No privileges assigned to SID [S-1-22-2-1003]
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/07/22 11:24:06, 3] smbd/password.c:register_vuid(304)
  User name: salik	Real name: Salik Rafiq,,,
[2008/07/22 11:24:06, 3] smbd/password.c:register_vuid(325)
  UNIX uid 1000 is UNIX user salik, and will be vuid 100
[2008/07/22 11:24:06, 3] smbd/password.c:register_vuid(356)
  Adding homes service for user 'salik' using home directory: '/home/salik'
[2008/07/22 11:24:06, 3] param/loadparm.c:lp_add_home(2691)
  adding home's share [salik] for user 'salik' at '/home/salik'
[2008/07/22 11:24:06, 3] smbd/process.c:timeout_processing(1329)
  timeout_processing: End of file from client (client has disconnected).
[2008/07/22 11:24:06, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/07/22 11:24:06, 3] smbd/connection.c:yield_connection(69)
  Yielding connection to 
[2008/07/22 11:24:06, 3] smbd/server.c:exit_server_common(768)
  Server exit (normal exit)
</code>[/HTML]

Not quite sure what is going on here. Have checked the manual and it looks like I have everything setup properly. It is able to send it to a Windows PC (XP Pro) and by FTP to the Ubuntu server...but not to SMB to the Ubuntu machine.

The error message on the printer is ED0001, which I can't find in the manual. I am asking other sources what this means.

Any ideas?

---

### Post by jasonsp6 on 2008-09-04
lil_elvis2000,

I wanted to let you know you are not the only one with this problem.  I have a Konica-Minolta Bizhub C450 and am encountering the same issue using Scan-to-SMB to a Samba file server.  I can connect fine to a Windows2000 Server and a shared folder on my XP Pro workstation, but not to a Samba Server (version 3.0.24). 
Surprisingly, the Konica-Minolta machine does not report back any errors in the scanner log!

I am trying to contact a Konica-Minolta networking specialist to help troubleshoot this issue, but it is difficult to contact the knowledgeable engineers in that company.  It is possible a firmware update on the machine may correct this.

I will update this thread if I discover a working solution.

---

### Post by lil_elvis2000 on 2008-09-08
Cheers.

---

### Post by jasonsp6 on 2008-09-12
I have made a little progress in troubleshooting this issue.
I have got my Konica-Minolta Bizhub C450 to Scan-to-SMB on a Mac OS X1.5 SMB share.  OS X uses Samba under the hood for SMB file sharing.  

If anyone is interested here are the configuration files from my working OSX share.  

The smb.conf is divided into three configuration files:


**/etc/smb.conf (main config file)**
```
; Configuration file for the Samba software suite.
; ============================================================================
;
; For the format of this file and comprehensive descriptions of all the
; configuration option, please refer to the man page for smb.conf(5).
;
; The following configuration should suit most systems for basic usage and
; initial testing. It gives all clients access to their home directories and
; allows access to all printers specified in /etc/printcap.

; BEGIN required configuration

; Parameters inside the required configuration block should not be altered.
; They may be changed at any time by upgrades or other automated processes.
;
; Site-specific customizations will only be preserved if they are done
; outside this block. If you choose to make customizations, it is your
; own responsibility to verify that they work correctly with the supported
; configuration tools.

[global]
    debug pid = yes
    log level = 1
    server string = Mac OS X

    printcap name = cups
    printing = cups

    encrypt passwords = yes
    use spnego = yes

    passdb backend = odsam

    idmap domains = default
    idmap config default: default = yes
    idmap config default: backend = odsam
    idmap alloc backend = odsam
    idmap negative cache time = 5

    map to guest = Bad User
    guest account = nobody

    unix charset = UTF-8-MAC
    display charset = UTF-8-MAC
    dos charset = 437

    vfs objects = darwinacl,darwin_streams

    ; Don't become a master browser unless absolutely necessary.
    os level = 2
    domain master = no

    ; For performance reasons, set the transmit buffer size
    ; to the maximum and enable sendfile support.
    max xmit = 131072
    use sendfile = yes

    ; The darwin_streams module gives us named streams support.
    stream support = yes
    ea support = yes

    ; Enable locking coherency with AFP.
    darwin_streams:brlm = yes

    ; Core files are invariably disabled system-wide, but attempting to
    ; dump core will trigger a crash report, so we still want to try.
    enable core files = yes

    ; Configure usershares for use by the synchronize-shares tool.
    usershare max shares = 1000
    usershare path = /var/samba/shares
    usershare owner only = no
    usershare allow guests = yes
    usershare allow full config = yes

    ; Filter inaccessible shares from the browse list.
    com.apple:filter shares by access = yes

    ; Check in with PAM to enforce SACL access policy.
    obey pam restrictions = yes

    ; Make sure that we resolve unqualified names as NetBIOS before DNS.
    name resolve order = lmhosts wins bcast host

    ; Pull in system-wide preference settings. These are managed by
    ; synchronize-preferences tool.
    include = /var/db/smb.conf

[printers]
    comment = All Printers
    path = /tmp
    printable = yes
    guest ok = no
    create mode = 0700
    writeable = no
    browseable = no

; Site-specific parameters can be added below this comment.
; END required configuration.


```


[B]
/var/db/smb.conf (imported system wide preferences)[/B]
```
#
# Configuration options for smbd(8), nmbd(8) and winbindd(8).
#
# This file is automatically generated, DO NOT EDIT!
#
# Defaults signature: d3410200e77400247c7c4700002aba3a480000
# Preferences signature: 200ea0af1609678ca480000262000000
# Configuration rules: $Id: rules.cpp 32909 2007-08-17 23:07:40Z jpeach $
# Server role: Standalone
# Guest access: never
# NetBIOS browsing: not a master browser
# Services required: org.samba.smbd org.samba.nmbd
#

[global]
	security = USER
	auth methods = odsam
	netbios name = macbook
	workgroup = WORKGROUP
	dos charset = 437
	server string = macbook
	ntlm auth = yes
	lanman auth = no
	max smbd processes = 10
	log level = 1
	use kerberos keytab = yes
	com.apple: lkdc realm = LKDC:SHA1.057597A277BC70C8CA75CA81C4C40FDE536D2967
	realm = LKDC:SHA1.057597A277BC70C8CA75CA81C4C40FDE536D2967
	map to guest = Never
	domain master = no
	preferred master = no
	enable disk services = yes
	enable print services = no
	wins support = no

[homes]
	comment = User Home Directories
	browseable = no
	read only = no
	create mode = 0750
	guest ok = no
	com.apple: show admin all volumes = yes

[global]

```


**/var/samba/shares/ scans  (one plaintext file for each share)**
```
#VERSION 3
path=/Users/Jason/Scans
comment=Scans
usershare_acl=S-1-1-0:F
guest ok=yes
directory mask=755
create mask=644

```

Please disregard some of the OS X specific remarks in the file if you try to mirror these settings.

---

### Post by lil_elvis2000 on 2008-09-15
Now to figure out which line actually makes it work. 

BTW what specific build of SAMBA is OS X using? I think OS X is also BSD based...and I wonder if that is also a factor.

---

### Post by jasonsp6 on 2008-09-16
lil_elvis2000,


Do you have an external Fiery print controller on your Bizhub?


Yesterday I discovered something interesting.  I have a Fiery IC-402 print controller on my Bizhub.  Strangely enough, no errors are ever displayed in the scanner job-history log.  It always logs: "Result: Job Complete". Even when testing it with invalid host, username and passwords.

Out of curiosity I disconnected the Fiery controller from the copier (unplugged the Ethernet jumper, video interface cable and switched back to internal print controller). 
With the Fiery disconnected scan-to-smb works perfectly on all destinations (Apple, Windows & Samba/Linux).  The job-history log also now works.
From this test I believe the Fiery is somehow interfering with the scan-to-smb data that passes though it.  It is probably not a Samba issue!  My scan-to-smb now works with default Samba server settings.

I will update when I figure why the external print controller is causing scan-to-smb to fail.  

Again, I don't believe this is a Samba or Linux problem anymore.

---

### Post by lil_elvis2000 on 2008-09-16
I don't have anything additional on my machine that I know of. I do get errors on my scan-to-smb...I get some unknown error which I cannot find anywhere. When I check the SMB log..the scanner logs in okay. but then "timesout". or at least that is the error in the samba log.

I'm not sure that there is a samba setting for that. Does anyone know.

Maybe your contact would know if there is a bios update for my bizhub 250...its on a lease so I could always get the company to update it at my request.

---

### Post by Franjo_Kluz on 2008-11-04
Hi everybody!

I just registered in Ubuntu forums!
I have same problem as you.
I am relatively new user of Ubuntu 7.10, (using it for 6 months), so I don't know every bit of it, but I can help you with the Konica Minolta machines because I am an advanced service engineer in a partner company with Konica Minolta.

I got scan-to-SMB working easy with Windows XP machines from Bizhub 360, 420 C250, C252, but I can't make it work with Ubuntu.

Procedure should be very simple:
1. Create shared directory in **root** directory and **share it**.
2. Allow users to write files
3. On copier press utility, one-touch registration, scan, address book, SMB
4. Fill account name, IP address (of your machine), destination path (just a name of shared directory for example: scans (warning!-case sensitive)) user name and password.

My problems with ubuntu were how to create a dir in root since it's owned by root. So I've learnt how to login as root. I created  a directory, share it, set to be owned by user (me) -not by root

So, by now technically I've did the same job as with win xp, but for some strange reason i just got the "login error" message on copier's scan job details.

I've explore ubuntu system further particularly menu "system"->administration->Login window
In "remote" tab I allowed remote login and
in "security" tab I allowed remote administrator login and check third option for "permissions" on the bottom of the same window.

I have tried various combination but without sucess.
So I joined this forum in search for help, maybe we can solve this problem  together.
My opinon is that there's a problem with samba share, not with bizhub machines, (updating firmware won't help) because with 4 models I've got same problems with ubuntu and no problems with win xp.

Printing with ubuntu to Bizhub machines are very good supported and I want to make scan-to-smb function from these machines work with ubuntu also.

I like Ubuntu system very much, it is easy to use, very user oriented, more secured than xp, no troubles with viruses, pretty faster than win on same machine.....

---

### Post by amb1545 on 2008-11-19
Anybody make progress in troubleshooting this issue?

I have a client that is experiencing the same issue and I'd really prefer not having to open up FTP to get scans working.  I have a technician calling Konica Minolta tomorrow morning, but I am not very hopeful that they will know much about samba.

---

### Post by Franjo_Kluz on 2008-11-29
When I was exchanging files between my laptop (Ubuntu) and my home computer (Ubuntu) via SMB network I noticed that I can't copy a file from my computer to a shared dir on my laptop. The other way around works perfectly - on my laptop enter a shared dir which is on computer and pull the file to desired dir on laptop.

So only PULL method work! When try to PUSH the file to a shared dir - operation failed. I concluded that is the same thing when the copier try to write into a shared folder PUSH method - same thing doesn't work.
I think that there lies solution to our problem.

The other example is that on network windows computer doesn't see ubuntu shared folders - possibly copier doesn't see shared folder also.

---

### Post by john_s on 2009-11-24
Dragging an old topic up...

I've just found this problem today - the copier scanned to a Windows XP share, but refuses to scan to a samba share on the Ubuntu box.

Will post back if I find a solution.

---

### Post by tranbo2@yahoo.com on 2011-08-03
I have the same issue ...does anyone get this to work? ubuntu 1104

---

### Post by pareshrana on 2012-05-10
Has anyone gotten this to work? I have a Bizhub 222. Scan to SMB to a Windows XP share works just file. Scan to SMB to a samba share on Ubuntu server 10.04 results in the Bizhub reporting Result: ED09CC. I can connect to the same Ubuntu SMB share from OSX and Windows clients with no problem.

Please help !!

Paresh

---

### Post by lisati on 2012-05-10
Thread closed: a lot can change in the time this thread has been around. Feel free to start a new thread referring back to this one.

---

