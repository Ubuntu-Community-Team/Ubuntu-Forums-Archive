---
title: "ubuntu 12.04.4  vs.  Fedora 14 (Laughlin)  TCP wrappers seem to have no effect???"
date: 2014-05-09
forum: Networking &amp; Wireless
---

### Post by FH13 on 2014-05-09
I have a NFS server configured on a ubuntu 12.04.4 machine on which I use tcp wrappers to limit which machines can have access to the NFS shares.  Up until recently I have had no problems w/ this setup, here's an example of some of what is in /etc/hosts.allow (BTW mountd is the only thing protected via hosts.allow)….

# {client 1}
mountd: {IP1} 255.255.255.0 :allow
# {client 2}
mountd: {IP2} 255.255.255.0 :allow


mountd: ALL : deny

On every client machine I have tested it on, the machine is only able to mount the NFS shared dirs if the {IP#} is valid and "allow" is the action.  AKA if the IP isn't in the list the catch all "deny" at the end blocks access.  If I change "allow" to "deny" access is also blocked.  

Enter a new Fedora 14 (Laughlin) machine and everything is out the window…  It doesn't matter if I have this new machine's IP listed or not it can always mount the NFS shares.  I have tried listing it w/ "deny" and that doesn't matter.  I have gone so far as to specifically put it in the /etc/hosts.deny file as

ALL: {FEDORA IP} 255.255.255.0 :deny

and it can still mount the shares.  



One thing I did notice is that when any other machine mounts the shares it connects via the sunrpc port first (this is what I am used to seeing):
11:21:40.882796 IP {IP1}.781 > {NFS SERVER}.sunrpc: UDP, length 56
11:21:40.882932 IP {NFS SERVER}.sunrpc > {IP1}.781: UDP, length 28
11:21:40.883551 IP {IP1}.924 > {NFS SERVER}.nfs: Flags [S], seq 2089780593, win 65535, options [mss 1460,nop,wscale 3,sackOK,TS val 1181477823 ecr 0], length 0
11:21:40.883567 IP {NFS SERVER}.nfs > {IP1}.924: Flags [S.], seq 728385799, ack 2089780594, win 14480, options [mss 1460,sackOK,TS val 153981908 ecr 1181477823,nop,wscale 7], length 0



However the Fedora machine seems to by-pass that and goes directly to nfs:
11:24:26.009968 IP {FEDORA}.35139283 > {NFS SERVER}.nfs: 132 getattr fh 0,0/24
11:24:26.010209 IP {NFS SERVER}.nfs > {FEDORA}.35139283: reply ok 232 getattr NON 3 ids 0/10 sz 0
11:24:26.010367 IP {FEDORA}.809 > {NFS SERVER}.nfs: Flags [.], ack 3494066366, win 54, options [nop,nop,TS val 566501402 ecr 154023190], length 0



I have tried adding in some of the other names/protocols to the hosts.allow file (spelling out rpc.mountd, portmap, etc), but I would have thought the ALL entry in /etc/hosts.deny should have blocked it no matter what.  I haven't used Fedora (or RedHat) that much so is there something I'm missing/don't know about it?  Frankly it's been awhile since I've had to mess around w/ tcpwrappers in general (it's a small shop, configured years ago and up until now has worked fine so I'm haven't given it much thought…) so maybe I'm missing/have forgotten something there too.

One final note is that when other machines mount the NFS shares I get something in the /var/log/syslog file that specifies the mount was successful or an invalid attempt was made.  Nothing shows up in the syslog file wrt the Fedora machine...

Obviously I can switch over to using the f/w on the machine to restrict this.  The tcp wrapper/hosts.allow has worked so well and it is easy/what I'm used to so I would prefer to keep that method.  I'm looking around to see what I can find but no luck so far.  I thought I would check in here to see if anyone had any ideas while I continue searching.

Thanks

---

