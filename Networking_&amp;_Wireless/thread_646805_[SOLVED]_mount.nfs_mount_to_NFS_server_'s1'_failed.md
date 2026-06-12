---
title: "[SOLVED] mount.nfs: mount to NFS server 's1' failed: timed out, retrying"
date: 2007-12-21
forum: Networking &amp; Wireless
---

### Post by Archmage on 2007-12-21
I can ping my server, I can ssh my server, but I can't access the NFS shares. Please help me.

Server: (192.168.0.200)
/etc/exports
```
/home/hanss/Test 192.168.0.210

```

Client: (192.168.0.210)
/etc/hosts
```
127.0.0.1 localhost
192.168.0.200 s1
```

```
sudo mount -t nfs s1:Test /home/hansc/Test
mount.nfs: mount to NFS server 's1' failed: timed out, retrying
mount.nfs: mount to NFS server 's1' failed: timed out, retrying
mount.nfs: mount to NFS server 's1' failed: timed out, retrying
mount.nfs: mount to NFS server 's1' failed: timed out, giving up
```

---

### Post by banewman on 2007-12-21
This guide got my nfs server working  - 
[http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html)
Hope it helps :)

---

### Post by Archmage on 2007-12-22
Thanks for your reply. But I found out that this was a firewall problem.

I need to open the port 32771 beside 111 and 2049.

I'm pretty disapointed that there was no information out there that was pointing this out.

---

### Post by smyrman on 2008-03-03
Same problem here...
```

mount.nfs: mount to NFS server '192.196.1.3' failed: timed out, retrying
mount.nfs: mount to NFS server '192.196.1.3' failed: timed out, retrying 
mount.nfs: mount to NFS server '192.196.1.3' failed: timed out, retrying 
mount.nfs: mount to NFS server '192.196.1.3' failed: timed out, give up. 
 
```
What did you do to open this port?

---

### Post by Archmage on 2008-03-06
> **smyrman said:**
> What did you do to open this port?

I did use Firestarter as my firewall-program. You should find out what firewall you are using and than open the port.

---

### Post by ganjuror on 2008-03-10
Hi,

I am having the same timeout problem, even though I have verified all necessary ports are open (by the way does anyone know if 32771 is TCP or UDP?). 

What's really strange is that NFS _was_ working previously (even before I'd opened 32771) but NIS was not, and therefore I had strange ownerships in mounted shares due to UID/GID missmatch. I normalized the 2 users on my client machine by hand to have the same UID/GID's as on the server, and suddenly NIS started working! Unfortunately, now I get this timeout error when trying to mount the remote shares. WEIRD!!I I am STUMPED and this is seriously compromising my productivity, and I have put in a ridiculous amount of time on this already. :( 

Can anyone point me in a new direction to continue my attempts at troubleshooting this?

Thanks In Advance!
River Hume

---

### Post by springbokmarine on 2008-03-20
I'm getting the same problem. My mount nfs server is Mac OS X 10.4.11. When I try to mount a share in ubuntu, I get:

sudo mount 10.0.1.16:/Volumes/lacie.music.iii/ /vol/lacie.music.iii/
mount.nfs: mount to NFS server '10.0.1.16' failed: timed out, retrying
mount.nfs: mount to NFS server '10.0.1.16' failed: timed out, retrying
mount.nfs: mount to NFS server '10.0.1.16' failed: timed out, retrying
mount.nfs: mount to NFS server '10.0.1.16' failed: timed out, retrying
mount.nfs: mount to NFS server '10.0.1.16' failed: timed out, retrying
mount.nfs: mount to NFS server '10.0.1.16' failed: timed out, giving up

I disabled [for testing only] all firewalls, allowed everyone access this share, chowned and chdmodded the directories to 777, yet, nada...


HELP!!

---

### Post by Eiríkr on 2008-03-20
To begin ruling out other connectivity possibilities, can your Ubuntu machine ping your Mac machine?  Can you ssh from one to the other?

---

### Post by ganjuror on 2008-03-20
I too have tried disabling all firewalls, and can ping, ssh, smb, sftp, and connect via every other protocol I can think of, but I get this timeout error still.

---

### Post by Eiríkr on 2008-03-20
Okay then, let's try this.  Restart your NFS server:
```
sudo /etc/init.d/nfs-kernel-server restart
```

Now open your syslog and look for any NFS server messages:
```
less /var/log/syslog | grep -i nfs
```

Let us know what you find.  Chances are something's not right in your [font=courier]/etc/exports[/font] file.  It'd be great if you could post that as well.

Cheers,

Eiríkr

---

### Post by ganjuror on 2008-03-20
ganjuror@hum:~$ sudo /etc/init.d/nfs-kernel-server restart
[sudo] password for ganjuror:
 * Stopping NFS kernel daemon                                            [ OK ]
 * Unexporting directories for NFS kernel daemon...                      [ OK ]
 * Exporting directories for NFS kernel daemon...                        [ OK ]
 * Starting NFS kernel daemon                                            [ OK ]
ganjuror@hum:~$ less /var/log/syslog | grep -i nfs
Mar 20 16:32:21 hum kernel: [2074385.060000] nfsd: last server has exited
Mar 20 16:32:21 hum kernel: [2074385.060000] nfsd: unexporting all filesystems
Mar 20 16:32:22 hum kernel: [2074386.724000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Mar 20 16:32:22 hum kernel: [2074386.732000] NFSD: starting 90-second grace period
ganjuror@hum:~$

/etc/exports :

/arcs          @nettrippers(rw,sync,no_subtree_check)
/media         @nettrippers(rw,sync,no_subtree_check)
/home          @nettrippers(rw,sync,no_subtree_check)
/home/ganjuror 192.168.15.42(rw,sync,no_subtree_check)

note ganjuror is in nettrippers NIS group, and is also a local user on client machine with same UID on both server and client. I had the same error when I was exporting like this:
/home/ganjuror @nettrippers(rw,sync,no_subtree_check)

I currently get the timeout trying both the following:
sudo mount 192.168.15.21:/home /home/ganjuror/docs
sudo mount 192.168.15.21:/home/ganjuror /home/ganjuror/docs

Note as I posted previously, the mounts were working fine, and were loading automatically from  /etc/fstab on startup, except that my permissions were messed up due to NIS not working. I manually synced the UID's of the 2 native users on the client machine, and then NIS worked fine, but NFS mounts have all timed out ever since.

---

### Post by Eiríkr on 2008-03-20
Ahah, NIS.  That changes the picture a bit.  I've personally had no luck getting NIS to work, though admittedly I haven't spent oodles of time on it, and in my case I'm dealing with Ubuntu on one side and Mac on the other.  

Anyway, since the NFS connectivity problem only appeared once you got NIS running, and since your NFS exports file seems fine, it looks highly probable that NIS is the culprit here.  Do NIS commands like [font=courier]ypwhich[/font] and [font=courier]ypcat[/font] produce the expected results?  And when you say you "synced the UIDs of the 2 native users on the client machine", what do you mean by "native users"?

Cheers,

Eiríkr

---

### Post by ganjuror on 2008-03-21
YEEEEEEEEEEEEEEEHAAAAAAAAAAAAW!!!!!!!!!!

Thank you for pointing me BACK at NIS! I thought I had finally gotten that sorted out, since it SEEMED to be working (I saw all the server's users listed in the client's login window) but the NIS server itself was actually not in it's own  /etc/ypserv.securenets file, so was not able to bind to itself, even though it was successfully starting services and offering them to the client, who _was_ defined in the file. I added the actual NIS server's IP address to the list, restarted NIS, and VOILA!

BTW: by 'native users' I meant ones that were actually instantiated directly on the client machine rather than just on server and available on client through NIS only.

---

### Post by Eiríkr on 2008-03-21
Brilliant then, glad you've gotten it working!  :D  If that fixes your concerns as far as this thread goes, then please also remember to mark the thread as SOLVED in the Thread Tools dropdown towards the top of the page.  :)

Cheers,

Eiríkr

---

### Post by ganjuror on 2008-03-22
Well, solved for me, but I wasn't the original poster. There were others having the timeout problem.

Loox like springbokmarine is the only one who has yet to fix _and_ akcnowledge...

Any luck Springbok?

---

