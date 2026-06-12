---
title: "nfs idmapd not working"
date: 2016-02-24
forum: Networking &amp; Wireless
---

### Post by philip10 on 2016-02-24
[COLOR=#ff0000]<unimportant back story>[/COLOR]
Recently I was trying to rush through a short tutorial without reading it which has been one of my biggest mistakes yet :(. Had to rebuild my home mediabox/server for the first time ever in order to fix it. While I was setting it up again I accidentally added the two important users in the wrong order which is another one of those 'argh! take me back in time to reverse this mess' moments. I've spent hours of time I don't have on this and there's probably a simple solution.
[COLOR=#ff0000]</unimportant back story>[/COLOR]

[COLOR=#ff0000]Relevant setup details:
[/COLOR]Server side users with UID
   media 1000
   phil 1001

Client side users with UID
   phil 1000

both phil users have the same password.

rpc.idmapd is running on both the client and server

both the client and server have the same idmapd.conf file
```

[General]

Verbosity = 0
Pipefs-Directory = /run/rpc_pipefs
# set your own domain here, if id differs from FQDN minus hostname
Domain = philnet

[Mapping]

Nobody-User = nobody
Nobody-Group = nogroup


```

server exports file
```
/home/phil/                     192.168.1.0/24(rw,sync,no_subtree_check)
```

client mount command
```
sudo mount 192.168.1.2:/home/phil mount/home/
```

have also tried the nfs4 mount command which gives the same result.

[COLOR=#ff0000]The problem:[/COLOR]
ls -l on the server shows files owned by phil : phil
ls -l on the client shows files owned by 1001 : 1001

So it seems idmapd is not making any attempt to map ids.

it would be good to get id mapping working but I am happy for alternative solutions as well. Samba is good but my only problem is I can't open a terminal and execute things on an smb share. Any advice apreciated :)

---

### Post by SeijiSensei on 2016-02-24
I solve this problem by using the same /etc/passwd and /etc/group on all my devices.

---

