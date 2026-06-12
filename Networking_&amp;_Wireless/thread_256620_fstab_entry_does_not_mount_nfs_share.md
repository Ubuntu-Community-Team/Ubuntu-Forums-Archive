---
title: "fstab entry does not mount nfs share"
date: 2006-09-13
forum: Networking &amp; Wireless
---

### Post by nanbudh on 2006-09-13
hi to all. i have two machines 'A'(192.168.100.20) and 'B'(192.168.100.21) with dapper loaded.Both machines have two user accounts staff and student consequently i have a two directories /home/staff and /home/student on machine A as well as B.

Now i want these directories to be mounted by machine B at boot time in such way that if user logs in as staff on machine B he should have rw access to the mounted folder A:/home/staff and have no access to A:/home/student. similarly if user student logs in at B he should have rw access to A:/home/student but not to A:/home/staff.

i have installed and started portmap as well as nfs-kernel-server on A. i have also installed portmap and nfs-common on B. now everything works OK and if i mount thru terminal like this:
sudo mount 192.168.100.20:/home/staff /home/staff
it works ok.
but if i write this in /etc/fstab it does not mount the relevant files at boot time:
192.168.100.20:/home/staff /home/staff default 0 0
i mean i can mount manually but fstab entry is not working.
PLEASE HELP I HAVE BEEN ON THIS FOR A WEEK NOW.

---

### Post by tbonius on 2006-09-13
This can be an annoying issue.  The fstab is parsed before portmap is even started.  I compensated by creating a mount startup script:

/etc/init.d/mountnfs

```
VERBOSE=yes
TMPTIME=0
[ -f /etc/default/rcS ] && . /etc/default/rcS
. /etc/init.d/bootclean.sh
. /lib/lsb/init-functions

#
#       Run in a subshell because of I/O redirection.
#
test -f /etc/fstab && (

#
#       Read through fstab line by line. If it is NFS, set the flag
#       for mounting NFS file systems. If any NFS partition is found and it
#       not mounted with the nolock option, we start the portmapper.
#
portmap=no
while read device mountpt fstype options
do
        case "$device" in
                ""|\#*)
                        continue
                        ;;
        esac

        case "$options" in
                *noauto*)
                        continue
                        ;;
        esac

        case "$fstype" in
                nfs|nfs4)
                        case "$options" in
                                *nolock*)
                                        ;;
                                *)
                                        portmap=yes
                                        ;;
                        esac
                        ;;
                smbfs|cifs|coda|ncp|ncpfs|ocfs2|gfs)
                        ;;
                *)
                        fstype=
                        ;;
        esac
        if [ -n "$fstype" ]
        then
                case "$NETFS" in
                        $fstype|*,$fstype|$fstype,*|*,$fstype,*)
                                ;;
                        *)
                                NETFS="$NETFS${NETFS:+,}$fstype"
                                ;;
                esac
        fi
done

exec 0>&1

if [ "$portmap" = yes ]
then
        if [ -x /sbin/portmap ]
        then
                log_begin_msg "Starting portmapper..."
                start-stop-daemon --start --quiet --oknodo --exec /sbin/portmap
                log_end_msg $?
                sleep 2
        fi
fi

if [ -n "$NETFS" ]
then
        echo "Mounting remote filesystems..."
        mount -a -t$NETFS
fi

) < /etc/fstab

#
#       Clean /tmp, /var/lock, /var/run
#
bootclean mountnfs

: exit 0

```

chmod it +x and then set it to boot with update-rc.d

That worked for me

T

---

### Post by nanbudh on 2006-09-13
Thanks a lot for your advice. as i am a newbie could you please tell me the chmod command in exact.and the last step too please. i will be grateful. Thanks a Gigabyte

---

### Post by nanbudh on 2006-09-14
ok i did what you advised ie i created a file mountnfs at /etc/init.d and then did "sudo chmod +x /etc/init.d/mountnfs" and then i took a guess and did "sudo update-rc.d defaults" and after that after reboot it started working fine. 
i am glad it did work finally but a strange thing happened, the login screen changed to a blue color and different text box and buttons, there was a picture of a yellow daisy flower at bottom right corner. how did that happen?

i have following questions please:
1. is it necessary to create a script like mountnfs?
2. did i give the chmod and update-rc-d command correctly?
3. can a user with login 'staff' log simultaneously on two computers or would that cause a sharing conflict? what if same file is accessed on both computers?
Thanks a lot in advance.

---

### Post by tbonius on 2006-09-14
None of your questions make sense.

The reason your GDM screen appears differently is most likely because your "Login Screen" option is set to use Random Themes.

It is not necessarily necessary to use a script like mountnfs.sh.. I am not sure what changed in the kernel for fstab entries to not start portmap or nfs before attempting to mount nfs drives.. but that is one workaround.  You could also bump up the run level of portmap and nfs.

I dont know if you initiated the "sudo update-rd.d" command (NOT update-rc-d) but if your NFS mounts work then I would assume so.

Two users logging into two different computers?  Yeah they can do that.. of course.. depending on whether or not you are using LDAP with any specific account rules that might prevent that from happening.. as well as the user has accounts on both machines if there is no central form of authentication.  As far as a file sharing issue.. I have no idea what youre talking about.  Be more specific.

T

---

