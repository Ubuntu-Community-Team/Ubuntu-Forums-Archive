---
title: "Only Ubuntu does not see Samba shares"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by Arestes on 2008-11-10
Hi,

I have a problem accessing the samba shares on my home server ("peter-server", running kubuntu 8.04). The weird thing is this, if I try to connect using my eee pc, running ubuntu 8.04, I cannot see the shares. But I do see the shares using the GF's MacBook without any problems.

So, I reached the conclusion the server works, but there is something wrong with the ubuntu samba en networking setup.

my /etc/samba/smb.conf file:

# Global parameters
[global]
workgroup = WORKGROUP
server string = Ubuntu
security = SHARE
WINS support = yes
encrypt passwords = Yes
update encrypted = Yes

and smbtree output:

WORKGROUP
	\\PETER-SERVER   		peter-server server (Samba, Ubuntu)
timeout connecting to 208.69.34.132:445
timeout connecting to 208.69.34.132:139
Error connecting to 208.69.34.132 (Operation already in progress)
cli_start_connection: failed to connect to PETER-SERVER<20> (208.69.34.132). Error NT_STATUS_ACCESS_DENIED
	\\LILIPUTER      		Ubuntu
failed tcon_X with NT_STATUS_NO_SUCH_USER

The weird thing is samba looking for the shares at some outside IP address. Any ideas on this?

Thanks in advance,

Peter

---

### Post by Coreigh on 2008-11-10
Several questions that might lead you in the right direction. 

The outside IP is for OpenDNS. Are you trying this on a local network or over internet? Do you regularly connect to your home server from the internet? It appears that you eee thinks it can find the server via OpenDNS have you tried connection using IP address instead of hostname? Are the server and the eee on the same WORKGROUP?

---

### Post by jimv on 2008-11-10
It's not a configuration problem, it's an issue with Nautilus.  I'm too lazy to look up the bug report, but last time I checked there was no fix yet.

EDIT:  I decided not to be lazy :)

[http://bugzilla.gnome.org/show_bug.cgi?id=524485](http://bugzilla.gnome.org/show_bug.cgi?id=524485)

---

### Post by Arestes on 2008-11-11
Thanks for the helpful replies.

@ Coreigh, the IP is indeed openDNS, well spotted :) I have that set as my WAN DNS in the router. 

So it is a bug. Is there a workaround? Would it help to set up a wins server? I'll give a try using konqueror this evening.

Thanks again!

Peter

---

