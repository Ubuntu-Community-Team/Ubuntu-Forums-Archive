---
title: "Strange NFS problem"
date: 2015-02-11
forum: Networking &amp; Wireless
---

### Post by Sebastiaan_Grob on 2015-02-11
I'm running VMWare ESXi 5.1 as a host.

Within that host I have several virtual machines running:

[LIST]
[*]**NiY** My main server (CentOS release 5.10 (Final))
[*]**downloadstation** My download server (Ubuntu 14.04.1 LTS)
[*]And several other which are not important
[/LIST]

I also have a HTPC which boots the xbmcbuntu iso, using TFTP, from NiY and mounts an additional NFS share for copy on write.

And downloadserver mounts a NFS share from NiY

My problem is that since i upgraded downloadserver from Ubuntu 12 to Ubuntu 14, it can no longer mount the NFS shares from NiY. The HTPC still can mount all the NFS shares.

What I have tried so far:

[LIST]
[*]Pinging all machines from all machines by hostname and IP, this works
[*]Granting all access in /etc/exports
[*]Disabling iptables on NiY (downloadserver is not running iptables)
[*]Using showmount to inspect the exports from NiY, this works: [http://pug205.nl/stackoverflow/showmount.jpg](http://pug205.nl/stackoverflow/showmount.jpg)
[*]Mounting the nfs share on NiY, this works
[*]Installing a fresh virtual machine with Ubuntu 12 and mount, does **not** work
[*]Installing a fresh virtual machine with CentOS 7 and mount, does **not** work
[*]Mount my NAS via NFS, this **does** work from **all** machines
[*]Checking logs on NiY, they are not mentioning any thing related to NFS
[*]logs on downloadstation contain some information
[/LIST]
```
RPC: Registered named UNIX socket transport module.
RPC: Registered udp transport module.
RPC: Registered tcp transport module.
RPC: Registered tcp NFSv4.1 backchannel transport module.
FS-Cache: Netfs 'nfs' registered for caching
Installing knfsd (copyright (C) 1996 [EMAIL="okir@monad.swb.de"]okir@monad.swb.de[/EMAIL]).
init: idmapd-mounting (/mnt/media) main process (296) killed by TERM signal
init: statd-mounting (/mnt/media) main process (297) killed by TERM signal
NFS: Registering the id_resolver key type
Key type id_resolver registered
Key type id_legacy registered
init: failsafe main process (542) killed by TERM signal
nfs: server {IP NiY} not responding, still trying
```

The last line keeps appearing in the logs


/etc/exports:
```

    #XBMC Frodo 12.2 XBMCBUNTU
    /export/XBMC/xbmcbuntu-12.2.Intel-NVIDIA *(ro,nohide,async,mp,no_root_squash,insecure,no_subtree_check)
    /export/nfsroot/xbmcbuntu-12.2.Intel-NVIDIA/{MAC ADDRESS HTPC} {IP HTPC}(rw,nohide,async,no_root_squash,insecure,no_subtree_check)

#XBMC Gotham 13.0 XBMCBUNTU
    /export/XBMC/xbmcbuntu-13.0~gotham_amd64 * (ro,nohide,async,mp,no_root_squash,insecure,no_subtree_check)
    /export/nfsroot/xbmcbuntu-13.0~gotham_amd64/{MAC ADDRESS HTPC} {IP HTPC (rw,nohide,async,no_root_squash,insecure,no_subtree_check)

#Media share
    /mnt/data/media *(rw,nohide,sync,no_root_squash,no_subtree_check)

```

I tried mounting with verbose logging and running Wireshark to check if anything did go to NiY (either by hostname or ip address):
```

root@downloadstation:~# mount -vvv -t nfs niy:/mnt/data/media /mnt/Download/
    mount: fstab path: "/etc/fstab"
    mount: mtab path:  "/etc/mtab"
    mount: lock path:  "/etc/mtab~"
    mount: temp path:  "/etc/mtab.tmp"
    mount: UID:        0
    mount: eUID:       0
    mount: spec:  "niy:/mnt/data/media"
    mount: node:  "/mnt/Download/"
    mount: types: "nfs"
    mount: opts:  "(null)"
    mount: external mount: argv[0] = "/sbin/mount.nfs"
    mount: external mount: argv[1] = "niy:/mnt/data/media"
    mount: external mount: argv[2] = "/mnt/Download/"
    mount: external mount: argv[3] = "-v"
    mount: external mount: argv[4] = "-o"
    mount: external mount: argv[5] = "rw"
    mount.nfs: timeout set for Wed Jan 28 01:30:59 2015
    mount.nfs: trying text-based options 'vers=4,addr={IP NiY},clientaddr={IP downloadstation}'

```
And it just hangs until i press [CTRL] + [C]

This is the output from Wireshark running on NiY with the previous mount command (only showing traffic from and to downloadstation)

```

No.     Time        Source               Destination         Protocol Info
        514 3.258878    IP downloadstation   IP NiY              NFS      V4 COMP Call <EMPTY> PUTROOTFH PUTROOTFH;GETFH GETFH;GETATTR GETATTR
        515 3.258898    IP NiY               IP downloadstation  TCP      nfs > 859 [ACK] Seq=1 Ack=121 Win=46 Len=0 TSV=314460502 TSER=78612280
       1135 35.288077   IP downloadstation   IP NiY              SMB      Echo Request
       1136 35.288140   IP NiY               IP downloadstation  SMB      Echo Response
       1137 35.288223   IP downloadstation   IP NiY              TCP      37709 > microsoft-ds [ACK] Seq=43 Ack=43 Win=2296 Len=0 TSV=78620288 TSER=314492532
       1681 63.319756   IP downloadstation   IP NiY              TCP      [TCP Keep-Alive] 859 > nfs [ACK] Seq=120 Ack=1 Win=229 Len=0 TSV=78627296 TSER=314460502
       1682 63.319769   IP NiY               IP downloadstation  TCP      [TCP Keep-Alive ACK] nfs > 859 [ACK] Seq=1 Ack=121 Win=46 Len=0 TSV=314520564 TSER=78612280
       1683 63.319790   IP downloadstation   IP NiY              TCP      859 > nfs [FIN, ACK] Seq=121 Ack=1 Win=229 Len=0 TSV=78627296 TSER=314460502
       1684 63.358905   IP NiY               IP downloadstation  TCP      nfs > 859 [ACK] Seq=1 Ack=122 Win=46 Len=0 TSV=314520604 TSER=78627296
       1944 78.359607   IP downloadstation   IP NiY              TCP      859 > nfs [RST, ACK] Seq=122 Ack=1 Win=229 Len=0 TSV=78631056 TSER=314520604
       1945 78.359639   IP downloadstation   IP NiY              TCP      [TCP Port numbers reused] 859 > nfs [SYN] Seq=0 Win=29200 Len=0 MSS=1460 TSV=78631056 TSER=0 WS=7
       1946 78.359654   IP NiY               IP downloadstation  TCP      nfs > 859 [SYN, ACK] Seq=0 Ack=1 Win=5792 Len=0 MSS=1460 TSV=314535605 TSER=78631056 WS=7
       1947 78.359715   IP downloadstation   IP NiY              TCP      859 > nfs [ACK] Seq=1 Ack=1 Win=29312 Len=0 TSV=78631056 TSER=314535605
       1948 78.359737   IP downloadstation   IP NiY              NFS      V4 COMP Call <EMPTY> PUTROOTFH PUTROOTFH;GETFH GETFH;GETATTR GETATTR
       1949 78.359743   IP NiY               IP downloadstation  TCP      nfs > 859 [ACK] Seq=1 Ack=121 Win=5888 Len=0 TSV=314535605 TSER=78631056
       1950 78.359760   IP downloadstation   IP NiY              NFS      V4 COMP Call <EMPTY> PUTROOTFH PUTROOTFH;GETFH GETFH;GETATTR GETATTR
       1951 78.359763   IP NiY               IP downloadstation  TCP      nfs > 859 [ACK] Seq=1 Ack=241 Win=5888 Len=0 TSV=314535605 TSER=78631056
       5308 95.447441   IP downloadstation   IP NiY              SMB      Echo Request
       5309 95.447488   IP NiY               IP downloadstation  SMB      Echo Response
       5310 95.447545   IP downloadstation   IP NiY              TCP      37709 > microsoft-ds [ACK] Seq=85 Ack=85 Win=2296 Len=0 TSV=78635328 TSER=314552692
      13721 138.455024  IP downloadstation   IP NiY              TCP      [TCP Keep-Alive] 859 > nfs [ACK] Seq=240 Ack=1 Win=29312 Len=0 TSV=78646080 TSER=314535605
      13722 138.455045  IP NiY               IP downloadstation  TCP      [TCP Keep-Alive ACK] nfs > 859 [ACK] Seq=1 Ack=241 Win=5888 Len=0 TSV=314595700 TSER=78631056
      16183 155.606860  IP downloadstation   IP NiY              SMB      Echo Request
      16184 155.606928  IP NiY               IP downloadstation  SMB      Echo Response
      16185 155.607035  IP downloadstation   IP NiY              TCP      37709 > microsoft-ds [ACK] Seq=127 Ack=127 Win=2296 Len=0 TSV=78650368 TSER=314612853

```

Any help?

---

### Post by SeijiSensei on 2015-02-11
Just out of curiosity, what happens if you force NFSv3 by adding "vers=3" to the options list in the mount command?

---

### Post by Sebastiaan_Grob on 2015-02-11
This happens:

```

root@downloadstation:~# mount -vvv -t nfs -o vers=3 niy:/mnt/data/media /mnt/Download/
mount: fstab path: "/etc/fstab"
mount: mtab path:  "/etc/mtab"
mount: lock path:  "/etc/mtab~"
mount: temp path:  "/etc/mtab.tmp"
mount: UID:        0
mount: eUID:       0
mount: spec:  "niy:/mnt/data/media"
mount: node:  "/mnt/Download/"
mount: types: "nfs"
mount: opts:  "vers=3"
mount: external mount: argv[0] = "/sbin/mount.nfs"
mount: external mount: argv[1] = "niy:/mnt/data/media"
mount: external mount: argv[2] = "/mnt/Download/"
mount: external mount: argv[3] = "-v"
mount: external mount: argv[4] = "-o"
mount: external mount: argv[5] = "rw,vers=3"
mount.nfs: timeout set for Wed Feb 11 15:13:47 2015
mount.nfs: trying text-based options 'vers=3,addr={IP NiY}'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: trying {IP NiY} prog 100003 vers 3 prot TCP port 2049
mount.nfs: prog 100005, trying vers=3, prot=17
mount.nfs: trying {IP NiY} prog 100005 vers 3 prot UDP port 999

```

Then almost a minute nothing
....
and it is mounted!!!

Thank you SeijiSensei!!!!!!!!


But, why won't it work using NFSv4?

---

### Post by SeijiSensei on 2015-02-11
I really don't know.  I've had problems with v4 so I fell back to v3.  Since I'm using NFS on my home office network, I only cared that it worked.

---

### Post by Sebastiaan_Grob on 2015-02-11
Lol, fair enough, if it works, it works ;)

Thanks again for your help!

---

