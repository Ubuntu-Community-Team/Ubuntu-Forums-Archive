---
title: "ZFS not starting NFS after upgrade to saucy."
date: 2013-12-25
forum: Networking &amp; Wireless
---

### Post by Kanji_Man on 2013-12-25
I have a server that had been running 12.04.3 LTS Precise Penguin for a long time, reliably sharing zfs pools accross nfs to remote machines.  I decided to do-release-upgrade all the way up to the latest 13.10 saucy salamander and see if everything would still work.  This is not a mission critical server and I clonezilla'd the drive for backup so a little down time is not a big deal. Everything appears to work except for one hitch:

I am unable to share my zfs pools via nfs if they are the only nfs shares on the server.

"sudo zpool status" shows all the pools are online and functioning.  I can "sudo zfs umount zpool" and "sudo zfs mount zpool" without a problem.   I can access the pools with "ls /media/zpool" and can successfully create and remove directories in the pools (mkdir /media/zpool/test, ls /media/zpool, rm -r /media/zpool/test) so the zfs pools appear to be mounted and functioning properly locally on the server. "sudo zfs get sharenfs" shows that all the pools are flagged "on" for nfs sharing.

"showmount -e" spews out "clnt_create: RPC: Program not registered" which I interpret as nfs-kernel-server not running.
"sudo /etc/init.d/nfs-kernel-server restart" ends with "* Not starting NFS kernel daemon: no exports." - Makes sense because I have no NFS shares on the machine except for zfs, which normally manages its own exports. But how is zfs supposed to do its job without the daemon?

As a workaround I can manually add the zpool mountpoint to /etc/exports to get the nfs daemon to run:
/media/zpool         192.168.1.0/24(rw,asnc,no_root_squash,no_subtree_check)
then "sudo exportfs -a" and "sudo /etc/init.d/nfs-kernel-server restart" ends with "* Starting NFS kernel daemon   [ OK ]"
"showmount -e" shows the manually added zpool as shared and I can mount the share from remote machines.  I can then "sudo zfs share -a", any additional zpools are then added to "showmount -e" and I can mount those shares from remote machines.

Has something changed since precise in the way nfs and zfs work together?  I would think this would be a common use model for zfs but am having difficulty finding much detail searching google or this forum.  In precise, the nfs daemon would start with an empty exports, allowing zfs to add its shares and things worked.  I upgraded to saucy using "sudo do-release upgrade" (a few times, it was a rather long process even on broadband).  I updated zfs with "sudo add-apt-repository ppa:zfs-native/stable", "sudo apt-get update", and "sudo apt-get upgrade".  This is the only ppa added to the system and I finished it with "sudo apt-get dist-upgrade" to ensure no packages were being held back.

Is there any way to override the NFS daemon's default behavior and force it to stay running when there are no exports?
OR
Is there a way for ZFS to start the daemon when there are pools to share? And get nfs to share them if they are the only shares?
OR
Is there another approach to resolve this situation other than the workaround I listed?

---

### Post by bradmccormack100 on 2014-01-05
Hello Kanji_Man,

I just got hit with this issue too. Although this was my second time setting up ZFS and first time setting up NFS so it was extra learning for me.
If you want an alternate hack just edit the daemon itself.

I commented out the relevant if clauses in the script such as the following.
..
```

# See how we were called.
case "$1" in
  start)
        export_files="/etc/exports"
        for file in /etc/exports.d/*.exports ; do
                if [ -f "$file" ]; then
                        export_files="$export_files $file"
                fi
        done
        #if [ -f /etc/exports ] && grep -q '^[[:space:]]*[^#]*/' $export_files
        #then
                do_modprobe nfsd


                # See if our running kernel supports the NFS kernel server
                if ! grep -E -qs "[[:space:]]nfsd\$" /proc/filesystems; then
                        log_warning_msg "Not starting $DESC: no support in current kernel."
                        exit 0
                fi


                do_mount nfsd $PROCNFSD_MOUNTPOINT || NEED_SVCGSSD=no
                log_begin_msg "Exporting directories for $DESC..."
                $PREFIX/sbin/exportfs -r
                RET=$?
                if [ $RET != 0 ]; then
                        log_end_msg $RET
                        exit $RET
                fi
                log_end_msg 0


                log_daemon_msg "Starting $DESC"
                log_progress_msg "nfsd"


                # See if rpcbind is running
                /usr/sbin/rpcinfo -p >/dev/null 2>&1
                RET=$?
                if [ $RET != 0 ]; then
                    echo
                    log_warning_msg "Not starting: portmapper is not running"
                    exit 0
                fi


                start-stop-daemon --start --oknodo --quiet \
                    --nicelevel $RPCNFSDPRIORITY \
                    --exec $PREFIX/sbin/rpc.nfsd -- $RPCNFSDCOUNT
                RET=$?
                if [ $RET != 0 ]; then
                        log_end_msg $RET
                        exit $RET
                fi


                # make sure 127.0.0.1 is a valid source for requests
                ClearAddr=
                if [ -f /proc/net/rpc/auth.unix.ip/channel ]
                then
                    fgrep -qs 127.0.0.1 /proc/net/rpc/auth.unix.ip/content || {
                        echo "nfsd 127.0.0.1 2147483647 localhost" >/proc/net/rpc/auth.unix.ip/channel
                        ClearAddr=yes
                    }
                fi


     $PREFIX/bin/rpcinfo -u localhost nfs 3 >/dev/null 2>&1 ||
                    RPCMOUNTDOPTS="$RPCMOUNTDOPTS --no-nfs-version 3"


                [ -z "$ClearAddr" ] || echo "nfsd 127.0.0.1 1" >/proc/net/rpc/auth.unix.ip/channel


                if [ "$NEED_SVCGSSD" = "yes" ]; then
                        do_modprobe rpcsec_gss_krb5
                        log_progress_msg "svcgssd"
                        start-stop-daemon --start --oknodo --quiet \
                            --exec $PREFIX/sbin/rpc.svcgssd -- $RPCSVCGSSDOPTS
                        RET=$?
                        if [ $RET != 0 ]; then
                                log_end_msg $RET
                                exit $RET
                        fi
                fi


                log_progress_msg "mountd"
                start-stop-daemon --start --oknodo --quiet \
                    --exec $PREFIX/sbin/rpc.mountd -- $RPCMOUNTDOPTS
                RET=$?
                if [ $RET != 0 ]; then
                        log_end_msg $RET
                        exit $RET
                fi


                log_end_msg 0
        #else
                #log_warning_msg "Not starting $DESC: no exports."
        #fi
        ;;

```

You can then blacklist the file from being upgraded or just re-edit it later.
Note - This was on Debian 7 for me so it might look a little different for you but it should be that simple.

I then just restarted the daemon and can see all the ZFS exports on the client.

I'm feeling sick today so hopefully I explained that OK, my brain isn't working very well.

---

### Post by tgalati4 on 2014-01-05
Could the difference be going from fuse zfs module (in userspace) on 12.04 to a kernel zfs module (now in system/kernel space)?  At least you answered your question.

---

