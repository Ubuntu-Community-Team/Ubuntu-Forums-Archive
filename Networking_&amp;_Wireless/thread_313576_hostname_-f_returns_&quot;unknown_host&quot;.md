---
title: "hostname -f returns &quot;unknown host&quot;"
date: 2006-12-06
forum: Networking &amp; Wireless
---

### Post by Vermyndax on 2006-12-06
Greetings...

I've been in the throes of setting up dynamic DNS and DHCP3 on a Dapper server.  It's working well for Mac and Windows clients... but the lone Edgy desktop I have isn't working out too well.

The main problem is that despite what is set up in /etc/hosts (which is the FQDN of the machine as well as "localhost"), the Edgy machine seems to refuse to acknowledge the existence of the domain name setting.

For example, "hostname" outputs:

"raven"

Which is the hostname of the machine.  "hostname -f" says:

hostname: unknown host

Huh?  Why is that?  This seems to be hindering this machine's ability to register DNS records as well, because this is the only machine that no records will be registered for when assigned an ip address.  That means name resolution to this machine won't work.

Any ideas on how to get this machine to recognize its FQDN?  I've tried setting it up in /etc/hosts, setting it in the GUI, and all kinds of fun things.  Sometimes the setting in the GUI just plain disappears too.

At wit's end.  Help!

---

### Post by vairoj on 2007-02-12
Did you manage to fix this problem since am I currently encounter the same problem as you.

---

### Post by Vermyndax on 2007-02-12
I did manage to resolve it, but I'm not 100% sure what the fix is (isn't that great?)

It seems to be based around having a localhost entry in /etc/hosts... which in this install of Edgy, appears to work fine.  I'm not having the issue any longer.

Put in your hosts:

127.0.0.1          <hostname> <FQDN>

Try that.

---

### Post by vairoj on 2007-02-12
Yes, editing /etc/hosts does fix the problem!

---

### Post by 5of0 on 2007-08-24
Aha!  Thanks a lot!  I was trying to figure this out so I could join to an AD domain, and changing my hosts file to
127.0.0.1 machinename.domain.local machinename
Worked like a charm.  Localhost evidently screws things up.

---

### Post by moe_syzlak on 2007-11-30
i also confirm that this fix works.

here is my '/etc/hosts' file

|---------------begin file----------------------------------------------------|
127.0.0.1	tj-linux-on-acer.domain.local tj-linux-on-acer 
#127.0.0.1	localhost localhost.localdomain tj-linux-on-acer
#127.0.0.1	tj-linux-on-acer
#127.0.1.1	tj-linux-on-acer.cfl.rr.com tj-linux-on-acer
# The following lines are desirable for IPv6 capable hosts
#::1     ip6-localhost ip6-loopback
#fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters
#ff02::3 ip6-allhosts
|------------------end file------------------------------------|

---

### Post by dsplabs on 2007-12-17
Same here, it worked for me too. I wrote a detailed walk-through for those who would like step by step instructions: [http://linux.dsplabs.com.au/?p=52](http://linux.dsplabs.com.au/?p=52).

---

