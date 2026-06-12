---
title: "A secure, fast and scalable alternative to NFS for WAN?"
date: 2007-01-08
forum: Networking &amp; Wireless
---

### Post by charming-butcher on 2007-01-08
I have heard that NFS is quite good suitable for LAN environments but not that good suitable for WAN due to security reasons. So NFS need three open ports: rpcbind/111, nfs/2049 and 739/unknown. Not really "KISS"...

There are also two cluster file systems as GFS2 and OCFS2 but they will not fulfill my needs because they split a file system over several remote partitions and are mainly used for creating LVM over a network(?).

I do not look for exotic alternatives to NFS but for a reliable and easy to manage (as NFS?) and approved system. Links about how I can make my NFS4 WAN-proofed and suitable are also appreciated!

---

### Post by netztier on 2007-01-08
> **charming-butcher said:**
> WAN due to security reasons. So NFS need three open ports: rpcbind/111, nfs/2049 and 739/unknown. Not really "KISS"...


What figures are you talking about when asking for "fast" and "scalable"? Dozens of MBytes/sec? Hundreds of clients, dozens of servers?

Well, if the WAN in question is a private E3 or LAN service link, there's no issues with "security" - you'd rather have to think about delay, throughput and packet loss. If you are talking about a public network such as the Internet, of course security is a topic to be considered additionally. If NFS is your protocol of choice for file services, you might consider running it through a **site-to-site VPN** tunnel? 

Tunneling NFS through **SSH** might also be an option - depending on how you intent to use it (i.e. at which time during the boot process you want to mount the remote ressources). I haven't done this myself yet - I am just tossing around a thought here.

With Gnome on the client, you can mount a remote folder over SSH, directly in the GUI (Menu: "Places" -> "Connect to Server"), if the remote system runs the sftp subsystem on the SSH deamon. Probably, KDE has this option also. It is also called "**SSH folders**"

On the other hand, **CIFS** (provided by samba v3) *might* be an alternative - It runs on tcp/445, and relies on "normal" host-to-name resolution mechanisms (hosts file, DNS, nis, etc.), so no more broadcasting on udp/137+138 or the dreaded WINS servers are needed. If I am not mistaken, it's also possible to have some form of encryption (at least for the user credentials).

It performs sufficiently well. With a single client system accessing a share, my P-III 500 with Ubuntu 6.06 LTS reaches 11MByte/sec with NFS. With CIFS, it does ~7-8MByte/sec, at higher CPU load. Multiple CIFS clients can actually fill the 100Mbps pipe. Not a big runner, but it gets the job done. If you have a heterogenous set of client OSs (Windoze, MacOS X, Linuces etc) randomly and spuriously connecting, and probably not even integrated in your local authentication environment, it might even be easier to set up and maintain (no UID/GIDs that need to match, etc).

best regards

Marc

---

