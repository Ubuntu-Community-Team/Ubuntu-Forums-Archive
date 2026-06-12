---
title: "Hosts file getting rewritten"
date: 2007-11-26
forum: Networking &amp; Wireless
---

### Post by gnosis-wi on 2007-11-26
Hello all,
I'm new to Ubuntu (but not linux) and I'm having a problem with entries in my hosts file.  The file appears to be rewritten on reboot.

I need to be able to access testing domains on local servers and the way I generally do this is to simply put an entry in the hosts file such as 

192.168.0.111 whatever.stage

This works fine on my Ubuntu box (7.10), but any entries I make disappear after reboot.  Perhaps Ubuntu wants me to put these somewhere else rather than edit the hosts file directly?

Thanks for any thoughts.
-Gnosis

---

### Post by gnosis-wi on 2007-11-27
Just thought I'd mention that, yes, this is a full install - not a live cd ;)

I've never heard of a process that would overwrite the hosts file.  But clearly something is doing it.  I added some entries today at work but when I got home and booted the laptop up again they're gone!

In case it makes any difference, here's what remains in there every time this happens:

```

127.0.0.1 localhost
127.0.1.1 Glottis



# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by wayward on 2008-02-11
Hi Gnosis,

the /etc/hosts file is being rewritten by network-admin tool every time you change your location from there.  The hosts are location-local, that is, network-admin will remember hosts you entered on the Hosts tab and reapply them when you change the location by rewriting the /etc/hosts.  So, the way to go would be to enter the hosts in the network-admin tool itself (the one that gets launched from System > Administration > Network or via Manual Configuration... from the nm-applet), and don't forget to save the changes after you make them! :)

I agree that this is a bother, since for most people there will be some overlap between the configurations, and you'll have to enter the same hosts for each location.  Oh well.

---

