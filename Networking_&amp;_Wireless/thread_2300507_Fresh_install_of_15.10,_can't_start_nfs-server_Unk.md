---
title: "Fresh install of 15.10, can't start nfs-server: Unknown fs types nfsd, rpc_pipefs"
date: 2015-10-26
forum: Networking &amp; Wireless
---

### Post by theosib on 2015-10-26
When I installed this 15.10 system, I selected that I wanted to install an NFS server, so it should have had all of the packages installed, and it should have been a simple matter of editing /etc/exports and restarting the service, but not only was nfs-kernel-server NOT installed, but after installing, I can't get it to start.  If anyone can help me get this straightened, out I would be very grateful.

First, I get this:
# service nfs-kernel-server restart
A dependency job for nfs-server.service failed. See 'journalctl -xe' for details.

So I do 'journalctl -xe', and I see stuff about missing dependencies.  Initially, I got errors about "nfsd" being an unknown filesystem, and Googling that didn't get me terribly far.  I did an apt-get update and upgrade, and then I got an error about nfs-common having an error while being configured, so I tried to configure it with "sudo dpkg --configure -a", and I get errors about both nfs-common and nfs-kernel-server not being configured.  Configuring nfs-common again, I'm told once again to look at 'journalctl -xe', and the main errors I see are all about unmet dependencies and this one:

Oct 26 10:38:32 thing1 mount[5635]: mount: unknown filesystem type 'rpc_pipefs'
Oct 26 10:38:32 thing1 systemd[1]: run-rpc_pipefs.mount: Mount process exited, code=exited status=32
Oct 26 10:38:32 thing1 systemd[1]: Failed to mount RPC Pipe File System.

Googling this, I find only an ArchLinux thread with no helpful answer.

So, what do I do next, and what went wrong in the install process that caused all of this in the first place?

Thanks!

Update:

I rebooted, because that's what one thing I googled suggested and this error has come back:

Oct 26 10:48:17 thing1 systemd[1]: nfs-idmapd.service: Job nfs-idmapd.service/start failed with result 'dependency'.
Oct 26 10:48:17 thing1 systemd[1]: run-rpc_pipefs.mount: Unit entered failed state.
Oct 26 10:48:17 thing1 mount[1587]: mount: unknown filesystem type 'nfsd'
Oct 26 10:48:17 thing1 systemd[1]: proc-fs-nfsd.mount: Mount process exited, code=exited status=32
Oct 26 10:48:17 thing1 systemd[1]: Failed to mount NFSD configuration filesystem.

Nowhere is any instructions for setting up nfs have I found "nfsd" mentioned.  Mind you, that looks like something a client would need, but I'm trying to set up an NFS *server*, so it should be a simple matter of setting up /etc/exports and restarting the service.  So what's going wrong?

---

### Post by theosib on 2015-10-26
I rebooted, because that's what one thing I googled suggested and this error has come back:

Oct 26 10:48:17 thing1 systemd[1]: nfs-idmapd.service: Job nfs-idmapd.service/start failed with result 'dependency'.
Oct 26 10:48:17 thing1 systemd[1]: run-rpc_pipefs.mount: Unit entered failed state.
Oct 26 10:48:17 thing1 mount[1587]: mount: unknown filesystem type 'nfsd'
Oct 26 10:48:17 thing1 systemd[1]: proc-fs-nfsd.mount: Mount process exited, code=exited status=32
Oct 26 10:48:17 thing1 systemd[1]: Failed to mount NFSD configuration filesystem.

Nowhere is any instructions for setting up nfs have I found "nfsd" mentioned.  Mind you, that looks like something a client would need, but I'm trying to set up an NFS *server*, so it should be a simple matter of setting up /etc/exports and restarting the service.  So what's going wrong?

---

