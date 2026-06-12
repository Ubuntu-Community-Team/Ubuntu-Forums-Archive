---
title: "Probleme NFS (Hardy/Opensuse10.3)"
date: 2008-10-05
forum: Networking &amp; Wireless
---

### Post by Key-mist on 2008-10-05
Hi all,
i would like to have acess to my files on my second computer.My first computer is on Hardy(ethernet) & my second one on Opensuse 10.3(wifi).I would like to use NFS but i have a problem : 

mount: mount to NFS server '192.168.1.1' failed: System Error:Connection refused.


(on Ubuntu)This is my /etc/exports/ : 

[HTML]   # /etc/exports: the access control list for filesystems which may be exported
    #        to NFS clients.  See exports(5).
    #
    # Example for NFSv2 and NFSv3:
    # /srv/homes      hostname1(rw,sync) hostname2(ro,sync)
    #
    # Example for NFSv4:
    # /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
    # /srv/nfs4/homes  gss/krb5i(rw,sync)
    #
    /home/ch3mist  192.168.1.13(rw)[/HTML]

my /etc/hosts.allow/ :

[HTML]portmap:ALL[/HTML]

my /etc/hots.deny/ :

    [HTML]portmap:192.168.1.10
    nfsd:192.168.1.10
    mountd:192.168.1.10[/HTML]

(on Opensuse) my /etc/fstab/ :

[HTML]192.168.1.1:/home/ch3mist    /media/nfs  nfs    rw    0    0[/HTML]

Someone could help me PLease?Thank You.

---

### Post by nixscripter on 2008-10-06
What's the firewall on the OpenSuSE machine set up to do?

---

