---
title: "[SOLVED]  NFS kernel server refuses to run post updates 20.04LTS"
date: 2020-06-24
forum: Networking &amp; Wireless
---

### Post by flaggman on 2020-06-24
[COLOR=#008000]**Attempting to mount exported shares on same server box to local server /media folder in the same operation as creating the links to the exports folder through a single use of /etc/fstab creates race situation it appears which causes startup of nfs-kernel-server to fail with cyclic error. It once worked as a quick troubleshooting aid but it appears tolerances have tightened. SOLUTION remove the mounting of exported shares to local /media folder during startup sequence. **[/COLOR][COLOR=#ff0000][I][B]



additional info:  This problem has now occurred on three ubuntustudio 20.04LTS workstation update this past weekend. All give identical indications and all have to be checked and rechecked and reinstall rpcbind in spite of latest version installed and running and then manually start nfs-kernel-server and has to be done repeatedly every reboot of these machines to get the nfs server to come up and run stably. This should be automatic so something has changed or been overlooked in the update process that now affects this deleteriously and does not give the option to send reports to developers. [/B][/I][/COLOR]


I recently upgraded to 20.04 LTS and all worked fine then after a couple of updates I was unable to mount file shares on workstation client machines.
checking of status on server shows fstab and exports all indicate all is normal yet when I try to start the nfs-kernel-server service it does not run.

Can someone explain what got changed that I need to look into to get the service back to normal operation?  Thanks

[I]The following are the error indications :

fwupd-offline-update.service is a disabled or a static unit not running, not starting it.
fwupd-refresh.service is a disabled or a static unit not running, not starting it.
fwupd.service is a disabled or a static unit not running, not starting it.
/var/lib/dpkg/info/fwupd.postinst: 47: dpkg-vendor: not found
Setting up libprocps8:amd64 (2:3.3.16-5ubuntu1) ...
Setting up bolt (0.9-1) ...
bolt.service is a disabled or a static unit not running, not starting it.
# service nfs status
Unit nfs.service could not be found.
# /etc/init.d/nfs-kernel-server start
Starting nfs-kernel-server (via systemctl): nfs-kernel-server.serviceFailed to start nfs-kernel-server.service: Transaction order is cyclic. See system logs for details.
See system logs and 'systemctl status nfs-kernel-server.service' for details.
 failed!
# systemctl status nfs-kernel-server.service
&#9679; nfs-server.service - NFS server and services
     Loaded: loaded (/lib/systemd/system/nfs-server.service; enabled; vendor preset: enabled)
    Drop-In: /run/systemd/generator/nfs-server.service.d
             &#9492;&#9472;order-with-mounts.conf
     Active: inactive (dead)

Jun 18 18:17:48 woodchipper systemd[1]: nfs-server.service: Trying to enqueue job nfs-server.service/start/replace
Jun 18 18:17:48 woodchipper systemd[1]: nfs-server.service: Found ordering cycle on exports-sharedata1.mount/start
Jun 18 18:17:48 woodchipper systemd[1]: nfs-server.service: Found dependency on nfs-server.service/start
Jun 18 18:17:48 woodchipper systemd[1]: nfs-server.service: Unable to break cycle starting with nfs-server.service/start[/I]

---

### Post by SeijiSensei on 2020-06-24
What do you see in /var/log/syslog?

---

### Post by flaggman on 2020-06-24
This is result of service nfs-kernel-server start

root@[serverHostID]:/var/log# tail syslog
Jun 24 08:45:03 [serverHostID] systemd[1]: Keeping job nfs-config.service/start because of nfs-server.service/start
Jun 24 08:45:03 [serverHostID] systemd[1]: nfs-server.service: Found ordering cycle on exports-songs.mount/start
Jun 24 08:45:03 [serverHostID] systemd[1]: nfs-server.service: Found dependency on nfs-server.service/start
Jun 24 08:45:03 [serverHostID] systemd[1]: nfs-server.service: Unable to break cycle starting with nfs-server.service/start
Jun 24 08:45:03 [serverHostID] systemd[1]: Requested transaction contains an unfixable cyclic ordering dependency: Transaction order is cyclic. See system logs for details.
Jun 24 08:45:03 [serverHostID] systemd[1]: Sent message type=error sender=org.freedesktop.systemd1 destination=n/a path=n/a interface=n/a member=n/a cookie=1 reply_cookie=1 signature=s error-name=org.freedesktop.systemd1.TransactionOrderIsCyclic error-message=Transaction order is cyclic. See system logs for details.
Jun 24 08:45:03 [serverHostID] systemd[1]: Failed to process message type=method_call sender=n/a destination=org.freedesktop.systemd1 path=/org/freedesktop/systemd1 interface=org.freedesktop.systemd1.Manager member=StartUnit cookie=1 reply_cookie=0 signature=ss error-name=n/a error-message=n/a: Transaction order is cyclic. See system logs for details.
Jun 24 08:45:03 [serverHostID] systemd[1]: Bus private-bus-connection: changing state RUNNING &#8594; CLOSING
Jun 24 08:45:03 [serverHostID] systemd[1]: Bus private-bus-connection: changing state CLOSING &#8594; CLOSED
Jun 24 08:45:03 [serverHostID] systemd[1]: Got disconnect on private connection.
root@[serverHostID]:/var/log#

---

### Post by SeijiSensei on 2020-06-24
You might need to add "fsid" fields in /etc/exports like this:
```

/home   192.168.100.0/24(rw,async,no_root_squash,insecure,no_subtree_check,fsid=0)

```
Each fsid must be unique.

---

### Post by flaggman on 2020-06-25
After setting all shares to your suggested parameters and restarting server doing a
mount -a on the workstation client gave same results. I commented out the "songs" share 
that initially gave cyclic error indication and repeated system restarts  but it just did the same thing on the next 
assigned share.


[B]userID@Workstation-client:~$ sudo su
[sudo] password for userID: 
root@Workstation-client:/home/userID# mount -a[/B]
mount.nfs: requested NFS version or transport protocol is not supported
mount.nfs: requested NFS version or transport protocol is not supported
mount.nfs: requested NFS version or transport protocol is not supported
mount.nfs: requested NFS version or transport protocol is not supported
mount.nfs: requested NFS version or transport protocol is not supported
mount.nfs: requested NFS version or transport protocol is not supported
mount.nfs: requested NFS version or transport protocol is not supported
mount.nfs: requested NFS version or transport protocol is not supported
mount.nfs: requested NFS version or transport protocol is not supported
mount.nfs: requested NFS version or transport protocol is not supported
mount.nfs: requested NFS version or transport protocol is not supported
root@Workstation-client:/home/userID# 


[B]root@Server Host ID:/home/userID# systemctl status nfs-kernel-server.service
&#9679; nfs-server.service - NFS server and services
     Loaded: loaded (/lib/systemd/system/nfs-server.service; enabled; vendor preset: enabled)
    Drop-In: /run/systemd/generator/nfs-server.service.d
             &#9492;&#9472;order-with-mounts.conf
     Active: inactive (dead)[/B]
root@Server Host ID:/home/userID# service nfs-kernel-server stop
root@Server Host ID:/home/userID# service nfs-kernel-server start
Failed to start nfs-kernel-server.service: Transaction order is cyclic. See system logs for details.
See system logs and 'systemctl status nfs-kernel-server.service' for details.
root@Server Host ID:/home/userID# systemctl status nfs-kernel-server.service
&#9679; nfs-server.service - NFS server and services
     Loaded: loaded (/lib/systemd/system/nfs-server.service; enabled; vendor preset: enabled)
    Drop-In: /run/systemd/generator/nfs-server.service.d
             &#9492;&#9472;order-with-mounts.conf
     Active: inactive (dead)

Jun 25 16:44:56 Server Host ID systemd[1]: nfs-server.service: Trying to enqueue job nfs-server.service/stop/replace
Jun 25 16:44:56 Server Host ID systemd[1]: nfs-server.service: Installed new job nfs-server.service/stop as 786
Jun 25 16:44:56 Server Host ID systemd[1]: nfs-server.service: Enqueued job nfs-server.service/stop as 786
Jun 25 16:44:56 Server Host ID systemd[1]: nfs-server.service: Job 786 nfs-server.service/stop finished, result=done
Jun 25 16:45:10 Server Host ID systemd[1]: nfs-server.service: Trying to enqueue job nfs-server.service/start/replace
Jun 25 16:45:10 Server Host ID systemd[1]: nfs-server.service: Found ordering cycle on exports-sharentfs1.mount/start
Jun 25 16:45:10 Server Host ID systemd[1]: nfs-server.service: Found dependency on nfs-server.service/start
Jun 25 16:45:10 Server Host ID systemd[1]: nfs-server.service: Unable to break cycle starting with nfs-server.service/start
root@Server Host ID:/home/userID#

---

### Post by flaggman on 2020-06-25
I happened to notice a post in another related forum that someone solved the problem by starting rpcbind first then launch the nfs server. I did an apt install rpcbind to get the report that the latest version already installed then manually launched it; then launched nfs-kernel-server and it came up normally and began working properly again. I have not restarted servers or workstation clients yet to confirm that was a fix or whether it was a permanent fix but at least now I have a starting point if I run across it again.  There have been a lot more updates and upgrades put out with COVID19 lockdown helping to create coding time for volunteers so looks like something occurred in one of the last three updates that changed something. 
Thanks for your input.

---

### Post by TheFu on 2020-06-25
rpcbind should be up (a dependency) for nfs server in the nfs systemd unit file. This should prevent the nfs-server from starting before rpcbind does.  But really the nfs server package should handle that already.  Seems to on my box:

```
multi-user.target.wants/nfs-server.service:Wants=rpcbind.socket
multi-user.target.wants/nfs-server.service:After= network.target proc-fs-nfsd.mount rpcbind.socket nfs-mountd.service
```
i don't have any servers on 20.04 today.  I’m cautious with servers.

---

