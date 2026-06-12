---
title: "dhclient &amp; remote home dir"
date: 2006-10-23
forum: Networking &amp; Wireless
---

### Post by itv on 2006-10-23
Hi,

I'm having problems that are related to dhclient and remote home directory, I think. The NFS server that hosts my home directory sometimes cannot be reached after the IP address is renewed, and that pretty much freezes the whole computer. If I wait long enough, (15-20 minutes usually), or force a reboot with ctrl+alt+del (doesn't work every time), the connection returns and everything works like a charm.

This problem does not occur very often, maybe once or twice in a week, but  it's quite irritating when it does. Do you guys have any ideas what might be causing this? Could it be that this happens only when the IP address is actually changed at the renewal (i could check this if I knew what the IP was to begin with, but I couldn't find this from log files)? I also have another network interface on the computer that is currently unused, the syslog tells that dhclient regurarly tries to find an address for that interface too (not succeeding, as it is unconnected), could this be causing problems? At least it keeps polluting the log files... 

I'm not sure if this Ubuntu-specific, but anyway, I'm running 6.06 LTS Dapper Drake.
 
Here's the line from the fstab that connects my home dir from the NFS:

[FONT="Fixedsys"]nfsserver:/path/to/myremotehome /home/iiro nfs bg,intr,hard,rsize=8192,wsize=8192 0 0[/FONT]

And here's the relevant(?) lines from the syslog:

[FONT="Fixedsys"]Oct 23 13:25:30 iiro-desktop dhclient: DHCPREQUEST on eth0 to x.x.x.x port 67
Oct 23 13:25:30 iiro-desktop dhclient: DHCPNAK from x.x.x.x
Oct 23 13:25:30 iiro-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Oct 23 13:25:31 iiro-desktop dhclient: DHCPOFFER from x.x.x.x
Oct 23 13:25:31 iiro-desktop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Oct 23 13:25:31 iiro-desktop dhclient: DHCPACK from x.x.x.x
Oct 23 13:25:31 iiro-desktop dhclient: bound to x.x.x.x -- renewal in 2792 seconds.
Oct 23 13:28:42 iiro-desktop kernel: [17193874.452000] nfs: server nfsserver not responding, still trying
Oct 23 13:28:42 iiro-desktop kernel: [17193874.652000] nfs: server nfsserver not responding, still trying
...

[/FONT]

-Iiro

---

