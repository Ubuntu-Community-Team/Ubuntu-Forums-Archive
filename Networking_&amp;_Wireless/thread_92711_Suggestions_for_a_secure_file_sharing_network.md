---
title: "Suggestions for a secure file sharing network"
date: 2005-11-20
forum: Networking &amp; Wireless
---

### Post by madtinkerer on 2005-11-20
I'd like to get some peoples' suggestions for a setup I'm considering.  I'm trying to set up a secure file sharing network for myself and the other teachers in my univ dept.  We make a lot of our own materials, including large video and audio files for classes and we want a secure stable way to share them.  When I arrived, the system at the time was windows file and printer sharing.  After some major problems in the last two weeks, I've got them to agree to try an alternative.  Here's what I'm suggesting"

Installing ubuntu on a P4 I've got.  I plan to create a user account with an individual home directory for each user (about 25 users or so).  I'd like to give the home directory of each user write permissions only for the given user, but read permissions by anyone with an account on the box.  Therefore, each user can control the info they want to share, but the information will be accessable by all.  I'm planning to use ssh and scp (through the windows winscp client) to allow access to the box.  I can limit access to the box to ips within the univ domain or I can even bind an user to a static ip address to make it most secure.

I'm sorry if that description is hard to follow.  I'm new at writing this kind of technical description.  Can anyone with experience in this sort of situation give me advice on how to modify the setup?

Thanks

---

### Post by MarcDM on 2005-11-21
Since you won't be adding/removing users alot, you could probably go with a Samba server setup to be a domain controller. 

Additionally, you could run DHCP3-Server on that box, and have it hand out IPs only to specific NICs (specified via MAC-Addresses)

It's pretty easy to setup Samba  once you've apt-gotten it. ([Quick Tutorial]("http://www.samba.netfirms.com/PDC.htm"))

For the DHCP, apt-get install dhcp3-server  and then put something like the following in /etc/dhcp3/dhcpd.conf

```

default-lease-time 600;
max-lease-time 7200;
subnet 10.0.0.0 netmask 255.255.255.224 {
  authoritative;
  range 10.0.0.2 10.0.0.28;
  option routers 10.0.0.1;
  option domain-name "mylocaldomain";
  option subnet-mask 255.255.255.224;
  deny unknown-clients;
  option time-offset -18000;

        # Add An entry like this for each machine :
        host machinename {
                hardware ethernet 00:E0:06:F9:6B:22;
                fixed-address 10.0.0.3;
                }
}


```


I know this is not all the info you need. Because you might need a DNS Server as well. 

Now that I think about it, DNSMasq could also serve your needs as a DHCP/DNS/IPMasquerade service. So install that and samba from the repositories, and have fun.

Hope this helps.

---

### Post by MarcDM on 2005-11-21
[QUOTE=MarcDM]Since you won't be adding/removing users alot, you could probably go with a Samba server[/QUOTE]

I say this to mean Samba with it's default user storage mechanism, as opposed to something more suited for a large user-base like LDAP.

---

