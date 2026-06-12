---
title: "'/tmp' does not exist or is not a directory, when connecting to [IPC$]"
date: 2005-08-11
forum: Networking &amp; Wireless
---

### Post by xbaez on 2005-08-11
[B]PLEASE HELP ME
I've tried and tried and my samba is not useless, it worked fine, I suppose it's a synaptic update (installed lots of new packages) that I did[/B]

[2005/08/09 15:14:28, 0] smbd/service.c:make_connection_snum(615)
'/tmp' does not exist or is not a directory, when connecting to [IPC$]
[2005/08/09 15:14:28, 3] smbd/sec_ctx.c:set_sec_ctx(28
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

I swear it's the excact smb.conf file I had working. When I have a daemon such as this working, I back it up. I'm using that file, newly created files... it just doesn't works

And if I don't put the
protocol = LANMAN2
treak, I get an Invalid error
tree connect failed: NT_STATUS_BAD_NETWORK_NAME

Somebody please help me

I'd appreciate some help

"tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)" + Ubuntu

I don't know what package I installed, but Samba has stopped working

I know the shares are right, samba is just not working

mount.smbfs is not working neither, it stays trying to connect to the samba share for hours.

Can anybody please help me?

---

### Post by nad on 2005-08-14
If your upgrade included samba 3x, you will now need to use mount.cifs instead of mount.smbfs.

Also, security has been improved, which means that user authentication is tighter. An explicit --user= argument will usually correct the situation. Consider using a credentials file.

---

