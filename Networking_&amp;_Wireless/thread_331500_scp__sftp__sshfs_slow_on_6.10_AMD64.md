---
title: "scp / sftp / sshfs slow on 6.10 AMD64"
date: 2007-01-04
forum: Networking &amp; Wireless
---

### Post by PgR on 2007-01-04
Using 6.10 on AMD64...

Throughput is very slow when using sshfs or scp or sftp - BUT only when transfering files FROM the box...

If I transfer a file to the problem machine from another machine on the network using any of those protocols I transfer at several M/s. If I transfer from the problem machine then I get all of 15kb/s. Yep, 15 k. It makes no difference whether I'm pulling or pushing the files, so I can't point my finger at either the ssh client or ssh server, as both seem to be affected.

If I use tftp or ftp, then I get several Mb/s. So I think the problem lies with the encryption.

(I know someone will point out I don't really need encryption on local file transfers, but it's obviously the same for traffic to the internet. I know also that encryption has an overhead - but not THAT much - and it's not a problem on another machine also running 6.10)

Bright ideas on a postcard, please...

---

### Post by PgR on 2007-01-05
FWIW it was the card (or driver) ATL1

---

### Post by leshaussebons on 2007-04-12
I experience the same issues with SFTP, on two different boxes ( ubuntu 6.10 and 6.06 ) 
the sending client is under windows , I tryied :

SFTPdrive : upload 250kbyte/s
FilleZilla : 2 kbyte/s
Webdrive : 3000Kbytes/s
WinSCP : 1500kbytes/s

I am on a wired 100Mb/s LAN, when I transfert files to a windows box, the speeds are really higher, how could I fix this ?

---

### Post by viz_e on 2007-04-26
I have the same problem since edgy (now with feisty). I get in both directions at most 2 Mb/s with scp and sftp. With dapper it was around 20 on the same network with the same machine.

---

