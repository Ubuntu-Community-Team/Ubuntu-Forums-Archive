---
title: "SAMBA: '/tmp' does not exist or is not a directory, when connecting to [IPC$]"
date: 2005-08-09
forum: Networking &amp; Wireless
---

### Post by xbaez on 2005-08-09
[2005/08/09 15:14:28, 0] smbd/service.c:make_connection_snum(615)
  '/tmp' does not exist or is not a directory, when connecting to [IPC$]
[2005/08/09 15:14:28, 3] smbd/sec_ctx.c:set_sec_ctx(288)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2005/08/09 15:14:28, 3] smbd/connection.c:yield_connection(69)
  Yielding connection to IPC$
[2005/08/09 15:14:28, 3] smbd/error.c:error_packet(105)
  error string = Permission denied
[2005/08/09 15:14:28, 3] smbd/error.c:error_packet(145)
  error packet at smbd/reply.c(415) cmd=117 (SMBtconX) eclass=1 ecode=67
[2005/08/09 15:14:28, 3] smbd/process.c:timeout_processing(1334)
  timeout_processing: End of file from client (client has disconnected).

I installed various programs with apt-get, now I boot my computer, and Samba just doesn't works anymore

I'd appreciate some help

---

