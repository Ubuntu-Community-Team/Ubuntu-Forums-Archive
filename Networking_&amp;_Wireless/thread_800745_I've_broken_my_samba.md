---
title: "I've broken my samba"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by sipickles on 2008-05-20
Hello,

using Hardy I got Samba working to share with lots of XP and Vista PCs on our network.

Suddenly the share has stopped. I can't see any computers in network. I can ping them tho so I know the network is up.

Could this entry in syslog give any indication why? it is caused when I restart the samba server:

```
May 20 09:18:02 simon-linux nmbd[6467]: [2008/05/20 09:18:02, 0] nmbd/nmbd.c:terminate(58) 
May 20 09:18:02 simon-linux nmbd[6467]:   Got SIGTERM: going down... 
May 20 09:18:05 simon-linux nmbd[6577]: [2008/05/20 09:18:05, 0] nmbd/asyncdns.c:start_async_dns(151) 
May 20 09:18:05 simon-linux nmbd[6577]:   started asyncdns process 6578 
May 20 09:18:05 simon-linux winbindd[5266]: [2008/05/20 09:18:05, 0] nsswitch/winbindd_passdb.c:sid_to_name(130) 
May 20 09:18:05 simon-linux winbindd[5266]:   Possible deadlock: Trying to lookup SID S-1-1-0 with passdb backend 
May 20 09:18:05 simon-linux winbindd[5266]: [2008/05/20 09:18:05, 0] nsswitch/winbindd_passdb.c:sid_to_name(130) 
May 20 09:18:05 simon-linux winbindd[5266]:   Possible deadlock: Trying to lookup SID S-1-5-2 with passdb backend 
```

Thanks

Simon


--- EDIT

New log messages, look good, but still nothing in network:

```

May 20 09:38:24 simon-linux nmbd[6577]: [2008/05/20 09:38:24, 0] nmbd/nmbd_namequery.c:query_name_response(109) 
May 20 09:38:24 simon-linux nmbd[6577]:   query_name_response: Multiple (2) responses received for a query on subnet 192.168.1.2 for name MSHOME<1d>. 
May 20 09:38:24 simon-linux nmbd[6577]:   This response was from IP 192.168.1.36, reporting an IP address of 192.168.1.36.
```

---

### Post by sipickles on 2008-05-20
Strange its now working.

Is this a windows problem?

Thanks

---

