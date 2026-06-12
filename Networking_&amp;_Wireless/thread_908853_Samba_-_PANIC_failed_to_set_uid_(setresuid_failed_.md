---
title: "Samba - PANIC failed to set uid (setresuid failed with EAGAIN)"
date: 2008-09-02
forum: Networking &amp; Wireless
---

### Post by cesarkallas on 2008-09-02
Hello,

I have been using the last Ubuntu server (8) and my samba has a problem, some times the shared directory doesn't open.

The samba is configured as a PDV (domain) and the partition with the shared directory is mounted with the flags (relatime,acl,user_xattr).

See the log:

[2008/09/02 23:07:08, 1] smbd/service.c:make_connection_snum(1033)
  alv-ts01 (10.20.3.245) connect to service program$ initially as user joao (uid=1004, gid=1004) (pid 19567)
[2008/09/02 23:07:08, 2] smbd/open.c:open_file(391)
  joao opened file auto.bat read=Yes write=No (numopen=1)
[2008/09/02 23:07:08, 0] lib/util_sec.c:set_effective_uid(205)
  setresuid failed with EAGAIN. uid(1004) might be over its NPROC limit
[2008/09/02 23:07:08, 0] lib/util_sec.c:assert_uid(101)
  Failed to set uid privileges to (-1,1004) now set to (0,0)
[2008/09/02 23:07:08, 0] lib/util.c:smb_panic(1633)
  PANIC (pid 19567): failed to set uid

[2008/09/02 23:07:08, 0] lib/util.c:log_stack_trace(1737)
  BACKTRACE: 20 stack frames:
   #0 /usr/sbin/smbd(log_stack_trace+0x1c) [0x613d4c]
   #1 /usr/sbin/smbd(smb_panic+0x43) [0x613e33]
   #2 /usr/sbin/smbd [0x618f31]
   #3 /usr/sbin/smbd [0x4b9fee]
   #4 /usr/sbin/smbd(pop_sec_ctx+0x96) [0x4ba166]
   #5 /usr/sbin/smbd(unbecome_root+0x9) [0x4af909]
   #6 /usr/sbin/smbd(gid_to_sid+0x169) [0x5d36a9]
   #7 /usr/sbin/smbd(get_nt_acl+0x41c) [0x4c3c4c]
   #8 /usr/sbin/smbd(is_visible_file+0x274) [0x46e1a4]
   #9 /usr/sbin/smbd [0x46e720]
   #10 /usr/sbin/smbd(dptr_ReadDirName+0x54) [0x46e794]
   #11 /usr/sbin/smbd [0x4a5385]
   #12 /usr/sbin/smbd [0x4a86be]
   #13 /usr/sbin/smbd(handle_trans2+0x25e) [0x4a8e0e]
   #14 /usr/sbin/smbd(reply_trans2+0x6dc) [0x4af68c]
   #15 /usr/sbin/smbd [0x4c80c4]
   #16 /usr/sbin/smbd(smbd_process+0x7b1) [0x4c93c1]
   #17 /usr/sbin/smbd(main+0xa20) [0x6c6420]
   #18 /lib/libc.so.6(__libc_start_main+0xf4) [0x7f22d6a091c4]
   #19 /usr/sbin/smbd [0x45a809]
[2008/09/02 23:07:08, 0] lib/fault.c:dump_core(181)
  dumping core in /var/log/samba/cores/smbd
[2008/09/02 23:07:09, 2] auth/auth.c:check_ntlm_password(309)


I don't know, but is necessary to compile again the samba with the flag USE_SETRESUID (include/config.h) ??

Please, help me!!!

---

