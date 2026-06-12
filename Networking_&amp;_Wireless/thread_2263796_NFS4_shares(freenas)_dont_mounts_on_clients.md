---
title: "NFS4 shares(freenas) dont mounts on clients"
date: 2015-02-03
forum: Networking &amp; Wireless
---

### Post by ilyamaltian on 2015-02-03
[COLOR=#141414][FONT=Georgia]mount.nfs4: mount(2): Permission denied[/FONT][/COLOR]

[COLOR=#141414][FONT=Georgia]on client in syslog[/FONT][/COLOR]

[COLOR=#141414][FONT=Georgia]Feb 3 11:05:40 term-ubnt-12 rpc.idmapd[5780]: New client: d[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]Feb 3 11:05:40 term-ubnt-12 rpc.idmapd[5780]: Stale client: c[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]Feb 3 11:05:40 term-ubnt-12 rpc.idmapd[5780]: #011-> closed /run/rpc_pipefs/nfs/clntc/idmap[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]Feb 3 11:05:40 term-ubnt-12 rpc.idmapd[5780]: Stale client: d[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]Feb 3 11:05:40 term-ubnt-12 rpc.idmapd[5780]: #011-> closed /run/rpc_pipefs/nfs/clntd/idmap[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]Feb 3 11:07:25 term-ubnt-12 rpc.idmapd[5780]: New client: e[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]Feb 3 11:07:25 term-ubnt-12 rpc.idmapd[5780]: Opened /run/rpc_pipefs/nfs/clnte/idmap[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]Feb 3 11:07:25 term-ubnt-12 rpc.idmapd[5780]: New client: f[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]Feb 3 11:07:25 term-ubnt-12 rpc.idmapd[5780]: Stale client: e[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]Feb 3 11:07:25 term-ubnt-12 rpc.idmapd[5780]: #011-> closed /run/rpc_pipefs/nfs/clnte/idmap[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]Feb 3 11:07:25 term-ubnt-12 rpc.idmapd[5780]: Stale client: f[/FONT][/COLOR]

[COLOR=#141414][FONT=Georgia]on server I dont know where logs exist messages is empty about clients mounts[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]My freenas 9.3 is in AD(samba4) domain clients are also in domain

[/FONT][/COLOR][COLOR=#141414][FONT=Georgia]PS 
ALSO in syslog [/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]Success getting keytab entry for 'TERM-UBNT-12$@K-DOM.LOCAL'[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]Feb  3 15:51:41 term-ubnt-12 rpc.gssd[5938]: WARNING: Preauthentication failed while getting initial ticket for principal 'TERM-UBNT-12$@K-DOM.LOCAL' using keytab 'FILE:/etc/krb5.keytab'[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]Feb  3 15:51:41 term-ubnt-12 rpc.gssd[5938]: ERROR: No credentials found for connection to server testnas.k-dom.local[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]Feb  3 15:51:41 term-ubnt-12 rpc.gssd[5938]: doing error downcall[/FONT][/COLOR]

---

### Post by TheFu on 2015-02-03
Did you setup kerberos between the server and clients? Don't think samba has **anything** do to with NFS.

---

### Post by ilyamaltian on 2015-02-03
kerberos is inside samba as I understand. I need to make  some principals in kerberos  like "nfs" but i dnt know where. And freenas  is read only system so  make keytab and move it on freenas manually is not an option

PS all works fine(becide GID in linux but GID in windows works) before I upgrade samba4 from 4.0.6 to 4.1.16
NOW it gets   [COLOR=#383838][FONT=gotham]WARNING: Failed to create krb5 context for user with uid 0 for server
after manualy creating keytab[/FONT][/COLOR]

---

### Post by ilyamaltian on 2015-02-06
I tcpdump freenas and it dont ask  samba kerberos seems it think its kerberos server itself

---

### Post by ilyamaltian on 2015-02-06
after some manipulations they begin ask-fyn and nfs>ha-cluster messaging, but freenas reject with [COLOR=#383838][FONT=gotham] [/FONT][/COLOR][COLOR=#383838][FONT=gotham]Status: NFS4ERR_SERVERFAULT (10006)[/FONT][/COLOR]

---

