---
title: "NFS peer-to-peer..."
date: 2006-08-27
forum: Networking &amp; Wireless
---

### Post by handy on 2006-08-27
Hi, today I have networked 2 Dapper boxes, using NFS.  I did it using the info' on [this page]("http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html#REMOTEMOUNT"). Which I found very useful.

I have never used NFS before, & I am probably abusing it, just using it for a home peer-to-peer network!

***I have set up both machines as servers, so as to get the P2P effect.*** 

*At this stage, I have to **manually mount** a remote directory, after I boot & log onto the 2nd machine.  This being due to the fact that the first fstab is lonely, & therefore can not find the remote directory to mount.*  

So, my questions are:  

1. Is there a better way to set up NFS, P2P?

2. Is there a way to call a script (that mounts a remote directory in this instance), automaticaly after I have logged on?  **Edit:**  It doesn't have to be after I've logged on does it!?

I appreciate any input, thankyou...

---

### Post by handy on 2006-08-27
After a few more reboots of both the machines, its looking like all is well!

I have scripts at the ready, although it is looking like I won't have to run them. I thought I would have to call them at boot up with **Sessions / Startup Programs**.

From my small amount of experience with NFS, I would say it looks to work well for small home P2P LANs.

I know it's early days yet though...

---

### Post by mtn on 2006-09-06
Hi handy,

I have used the same guide but I am stuck as I don't know what the name of my nfs server is! How did you find out the name? I'm networking a wireless laptop through a belkin wireless router to my desktop with the laptop as client. I was thinking it would be a case of pointing the client to the desktop IP until I got to setting up the client where the guide states to use the mount command like this "mount master.foo.com:/home /mnt/home" I'm stuck not having a clue what master.foo.com: should be.

Any help would be excellent.

Cheers

---

### Post by handy on 2006-09-08
Hi **Mtn**, sorry for the delay, I've been out of town for a few days.

I use the following in my **/etc/fstab** :

**192.168.0.3:/home /_media_/close2home nfs rw,hard,intr	0	0**

So, you can see I'm using the IP address instead of the **mount master.foo.com:/home /_mnt_/home**

In Ubuntu, we use **/media/** instead of **/mnt/**, which other linux distro's use.  

You have to create a directory like so:  **/media/*chosenName*** where ***chosenName*** is the name you have chosen for the ***remotely_mounted_filesystem***.

This is then mounted via a line in the **/etc/fstab**. 

Looking at the example line from my **/etc/fstab** you will see **/media/close2home** :) 

The only problem I had was that the IP's on the network can change!!!

For a solution to the above IP problem have a [look here?]("http://ubuntuforums.org/showthread.php?t=246879")

My LAN needs to give 4 computers access to the internet & a printer which is cable conected directly to the network switch.  The 4 computers, do not have to all talk to each other, 2 + 2 is the reality of it.

So, I'm going to reconfigure my network to have 2 servers, each with only 1 client.  This should solve my changing IP problem, & completely satisfy the users, obviating the need to go the static IP route.  (no pun intended) :KS

I hope I've helped & not clouded the situation?  I am a bit tired & I think it shows in my post... :rolleyes:

---

### Post by tbonius on 2006-09-08
So your /etc/fstab nfs mounts are automatically occuring at boot?  I had to make a j00kie script that made sure portmap and the nfs services were started before attempting to mount via nfs:

/etc/init.d/mountnfs.sh
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
bootclean mountnfs

: exit 0

```

---

### Post by handy on 2006-09-09
@ **tbonius**: When trying to do the p2p NFS thing, I found that I needed to run a script on each machine at boot.

It was not as elegant as yours, because I have nowhere near the knowledge that you have.  So I just ran a one line script via **Sessions / Startup Programs** executing **sudo mount -a** with the mount command having the need for a password removed in the **sudo configuration file**.  

This is NOT a security problem for me, my LAN is used at home by wife & I, with **VERY** rare use by visiting mature children.

As mentioned in the previous post, this minor security hole can be plugged by spending a little more time on scripting. This may be needed by those who have untrustworthy people using their LAN. :( 

For my situation,this solution seemed to work, BUT, I did have a problem with changing IP addresses on the network...  As mentioned in my previous post, where a link to the solution to same problem is posted... :) 

Thanks for your post, I'm sure that it is very instructive for those with more knowledge than I.  

I will look at it & learn all I can, I'm 100% sure that it is a proper way to do it, as opposed to my desperate attempt to solve the problem any way I can... :KS

---

### Post by tbonius on 2006-09-09
Hey .. whatever works for ya ;-)

Thats the magic of scripting.. we can all do it whichever way works best for our needs.  I just do it this way beause I dont always use Gnome as my Window Manager.

T

---

### Post by handy on 2006-09-09
I wish that I had your knowledge so that I could write such beautiful scripts!?

Is there a resource that you could recommend to those of us who would like to be able use bash scripts effectively?

I expect that many, but not all linux users come to a point where they realise that understanding the OS to a certain degree, requires the understanding of a scripting language to a similar degree, just to be able to exercise the understanding...

If you know what I mean... :rolleyes:

---

### Post by mtn on 2006-09-09
Thanks Handy. I have my laptop and desktop connectd via FTP which work, sorted that here [http://www.ubuntuforums.org/showthread.php?p=1475816#post1475816](http://www.ubuntuforums.org/showthread.php?p=1475816#post1475816) with help from tbonius (cheers).

I will go back and have another look at NFS (and Samba) in the near future as I think the FTP solution might be a bit limiting!

---

