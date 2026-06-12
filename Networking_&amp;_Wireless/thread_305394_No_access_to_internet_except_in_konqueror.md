---
title: "No access to internet except in konqueror"
date: 2006-11-23
forum: Networking &amp; Wireless
---

### Post by Tim.R on 2006-11-23
Hi

I'm having this weird problem where I can only access the internet through Konqueror.  Any other applications just time out.  Strangely, though, if I connect to a site in Konqueror (say ubuntuforums.org) I can happily access any page I like in that site after that using any program I'm running.  Pinging the server from a terminal also allows me to access the site using any program.

Also, I found out that when i run apt-get, the IP of the server is given as 1.0.0.0.  But if I ping the server (its domain name, not its numerical IP) and then run apt-get it works normally and lists the correct IP.

I was wondering if anyone else has heard of this problem?  I'm using Kubuntu Edgy, but I had this problem with Dapper as well.

Cheers,
Tim

---

### Post by Tim.R on 2006-11-28
[Edit]
Never mind, I stupidly didn't look that one up myself and figured it out
[/Edit]

It seems I've narrowed the problem down a bit.  I ran about:config in firefox and disabled IPv6.  It now looks up addresses fine.  So, I was wondering how I disable IPv6 globally?

Cheers,
Tim

---

### Post by Tim.R on 2006-11-28
More from me, sorry...

I disabled ipv6 completely (running 'ip a | grep inet6' returns nothing), but still seem to have the same problems.  wget and apt-get still won't resolve addresses unless I visit the site in Konqueror or ping it first.  I'm completely out of ideas.

It would be great if anybody else has even heard of this problem, nobody I've spoken to has...

Cheers,
Tim

---

### Post by stream303 on 2006-12-01
Might be dns issues.  Are you behind a router?  I'd check your /etc/resolv.conf file and make sure that your isp's primary and backup nameservers are at the top of the list.

If not, and you are running static, you can add them manually or in network preferences.

If you are running dhcp, you may want to look at this quickie howto:

[http://www.ubuntuforums.org/showthread.php?t=307758](http://www.ubuntuforums.org/showthread.php?t=307758)

---

### Post by bxlinux on 2006-12-01
how did you disable Ipv6? That may help me resolve my issue.

---

### Post by Tim.R on 2006-12-01
I am currently behind a router.  Changing resolv.conf to my ISP's DNS server worked.  The problem with this, though, is that when I'm at University I need to use the university's DNS server (external traffic needs a proxy log-in and I'm well over my traffic quota), so stopping dhclient from changing the resolv.conf script means I have to manually change it when I go to uni.  Not a major problem, but a bit of a headache.  But thanks for your help.

Also, to disable ipv6:

Edit (as root) /etc/modprobe.d/blacklist  (create it if necessary).  Somewhere in there add the following code:
```

#Disables ipv6
blacklist ipv6

```

Reboot (probably don't have to reboot, could maybe run modprobe and then ifup/ifdown but rebooting is easier) and it should be done.

Thanks,
Tim

---

