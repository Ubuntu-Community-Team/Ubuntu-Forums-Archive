---
title: "NFS Client won't mount drive"
date: 2007-08-09
forum: Networking &amp; Wireless
---

### Post by ncwalker on 2007-08-09
I am trying to set-up a NFS on a P3.  I am using Ubuntu 7.04 Server on the server and Ubuntu 7.04 Desktop  on the Desktop.  Using the instructions at [HTML]https://help.ubuntu.com/community/SettingUpNFSHowTo[/HTML]
I have a few questions

Question 1:   The HOw To guide  says:

> Host Names (optional if using DNS )

Add any client name and IP addresses to /etc/hosts.”

I have one Ubuntu 7.04 Desktop out there and potentially two XP's  What should I put here?  Anything?
As it stands the /etc/hosts file says:
```
192.168.0.100 localhost
192.168.0.100 bluescreen
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Question 2: I like the idea of Portmap Lockdown (At least I think I like it).  I have no /etc/hosts.deny or /etc/hosts.allow file so do I just create them with the one line mentioned in the tutorial?

Question 3:  How do I list IP addresses?  I have a router (192.168.0.1 ), a server (192.168.0.100) and  then the printer is 192.168.0.4, the Ubuntu Desktop downstairs is 192.168.0.5.  How should I list these?  Is this useful or important?

I followed the instructions and changed my  /etc/exports .  It now reads as follows

```
# /etc/exports: the access control list for filesystems which may be exported
#        to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)

/home 192.168.0.0/255.255.255.0(rw,sync)
/usr/local 192.168.0.0/255.255.255.0(rw,sync) 
```

When I export the shares the terminal responds like this: 

exportfs: /etc/exports [2]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.0.0/255.255.255.0:/home".
  Assuming default behaviour ('subtree_check'). 
  NOTE: this default will change with nfs-utils version 1.1.0
exportfs: /etc/exports [3]: Neither 'subtree_check' or 'no_subtree_check' specified for export " 192.168.0.0/255.255.255.0:/usr/local".
  Assuming default behaviour ('subtree_check').
  NOTE: this default will change with nfs-utils version 1.1.0

Is this O.K.?

When I go to the client machine I installed portmap without incident by typing 
```

sudo apt-get install portmap nfs-common 
```

but when I typed 
```

 sudo mount 192.168.0.100:/home /home/ncwalker/networkh
```

the terminal appears to get stuck.

What can I do to make it work?  Many thanks!

---

### Post by ncwalker on 2007-08-09
I've got it.

A friend asked me to check the firewall settings on the server and sure enough I am blocking myself.

O.K. new question.

I am running webmin ver. 1.350 and the firewall options are as follows: 

Allow all traffic
Do network address translation on external interface eth0
Block all incoming connections on external interface eth0
Block all except SSH and IDENT on external interface eth0
Block all except SSH and IDENT ping and high ports on interface eth0

which one should I choose?

Thanks for the help!

---

