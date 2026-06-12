---
title: "NFS and internet?"
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by cenwesi on 2008-07-02
Can someone tell my why NFS on local network works fine but when i try to connect through the internet i get mount.nfs: internal error

ie:

$ mount 192.168.1.xxx:/data/test1 /mnt/test1
   works OK!

$ mount mydomain.homepc.net:/data/test1 /mnt/test1
  does not work and i get  mount.nfs: internal error

thanks.

---

### Post by ilrudie on 2008-07-02
[COLOR=Gray]First of all NFS is not encrypted so you may not want to do it over the internet without an SSH tunnel.  Second internally NFS probably doesn't need to transverse a firewall but going over the internet there may be a firewall problem.  Make sure port 2049 is open on any firewalls you are trying to connect to as that is the normal NFS port.  Once again though NFS is not secured so opening this port is probably not advisable.  Instead you can use the -D or -L command on ssh to make a tunnel and make sure to specify the port in the mount command like 

```
mount -t nfs nfs://localhost:2049/data/test1 /mnt/test1
```This is generally necessary because nfs uses bind or rpc to determine the port and may switch the port on you unless you force it.  Even if you choose not to tunnel it us the above format to force use of that port.  Just replace local host with the remote host since you aren't tunneling.[/COLOR] 

[COLOR=Red]This is probably still good advice so I will leave it so you can read how to tunnel NFS but it looks like this is a bug in hardy that requires UDP traffic to complete a connection which may get blocked somewhere along the way...  [/COLOR][URL="https://bugs.launchpad.net/ubuntu/+bug/213444/comments/23"][COLOR=Red]https://bugs.launchpad.net/ubuntu/+bug/213444/comments/23 [/COLOR]
[/URL]

---

