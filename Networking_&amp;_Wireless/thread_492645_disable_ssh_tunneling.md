---
title: "disable ssh tunneling"
date: 2007-07-05
forum: Networking &amp; Wireless
---

### Post by box2 on 2007-07-05
i've set up a chrooted environment with very basic tools for some users.  it has no network devices or any binaries that can be used to connect to the internet or my network (inside of the chroot).  it does however allow them to tunnel through the ssh connection.  for example if they

ssh -l<username> <hostname_of_my_computer> -D <portnumber>

they can then use that portnumber as a socks style proxy.  for example set their web browser to use localhost <portnumber>, it will forward all traffic through there and make connections look like they're coming directly from my computer.

can i disable this from happening?
-a

---

### Post by box2 on 2007-07-05
i've temporarily fixed the problem by blocking all ports outgoing from that computers IP address at my router.  this is ok for now, but it would be better if i could use the internet as a normal user, and the chrooted users get blocked.  especially when i want to install new software or do updates.

does Guarddog have this level of functionality or should i be looking into configuring my iptables by hand?

---

### Post by kevdog on 2007-07-05
Guarddog is just a GUI to manipulate and set rules for the iptables file.  It can block specific ports for specific IP address groups.  I understood your original question, which I dont know how to block port forwarding within the ssh daemon itself, but now Im unsure what exactly you want to do by manipulating the IP tables.

---

### Post by turinglabs on 2007-07-05
Best to do this at the application layer. You can disable forwarding for all users (even the dynamic forwarding with -D ), see sshd_config (5 ), then edit /etc/ssh/sshd_config as needed.

```

AllowTcpForwarding  
              Specifies whether TCP forwarding is permitted.  The default is &#8220;yes&#8221;.  Note that disabling TCP forwarding does not improve security unless users are also denied shell access, as they can always install their own forwarders.

```

You may also want to look at PermitTunnel. 

If you want to disable forwarding for individual users, you have to enforce key-based authentication and use per-key directives in each user's authorized_keys file. See sshd (8 ) in the "AUTHORIZED_KEYS FILE FORMAT" section, specifically the 'no-*' directives. The problem with this is that if you are giving them shell access, they can just edit their authorized_keys file to remove the restrictions. One way around this would be to move each user's authorized_keys file to a central config repository, so they had read-only access to the file. I haven't tested it, try this in sshd_config:

```

AuthorizedKeysFile /etc/ssh/%u/authorized_keys 

```

---

### Post by box2 on 2007-07-07
turinglabs, you're a king among men

---

