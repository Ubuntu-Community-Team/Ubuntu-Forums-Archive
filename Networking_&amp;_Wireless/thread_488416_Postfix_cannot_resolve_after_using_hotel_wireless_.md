---
title: "Postfix cannot resolve after using hotel wireless network"
date: 2007-06-30
forum: Networking &amp; Wireless
---

### Post by adrian.colyer on 2007-06-30
I'm using ubuntu feisty with postfix for delivering outgoing messages. Two weeks ago I traveled on business to Belgium and connected to a wireless network there. All the time I was in Antwerp my email messages were happily sent out by postfix. Upon returning home however, postfix stopped being able to send out any messages, with repeated entries in the log of the form:

" Mail service error for name=mail.xxx.com type=MX: Host not found, try again" 

I discovered this just before a second business trip last week (my email had all been backing up on my local machine). I arrived on business in Spain and connected to the hotel wireless network (via one of those browser-redirect screens). Suddenly all my mail started flowing again. 

Now I'm back home, and once more my postfix has stopped being able to send messages. I've rebooted, checked /etc/resolv.conf and the postfix jail version, added an explicit entry for my mail server into /etc/hosts, run postfix reload, start, stop, flush etc. but all to no avail.  

At home I'm successfully networked via both eth0 (wired) and eth1 (wireless) and can reach the mailserver very happily via ping etc.. It is just postfix that seems to be broken.

What is it that connecting to the hotel network can have done to my configuration and how do I undo it please?

---

### Post by TuxRacer321 on 2008-01-03
I've seen a similar problem which I can trigger by using a vpn connection.

I can ping my mail relay host, but the resolv.conf in the postfix directory doesn't have the vpn dns server entry.

After the vpn sw has modified the /etc/resolv.conf   then this fixes it:
 cp /etc/resolv.conf /var/spool/postfix/etc/resolv.conf

This is a brain dead work around :-(

I think the bit-rot is caused by the resolvconf program which I've just disabled (see below).  See here: [http://ubuntuforums.org/showthread.php?t=651585&highlight=postfix+resolv.conf](http://ubuntuforums.org/showthread.php?t=651585&highlight=postfix+resolv.conf)

My  /var/spool/postfix/etc/hosts
has the correct entry for the relay host.
My  /var/spool/postfix/etc/nsswitch.conf has the default
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

So I shouldn't even need a valid resolv.conf  with the correct nameserver.  
But the mail does not go through!

You can check the postfix setup with 
 postfix check

This is a bad sign, but fixable with brain-dead-workaround above:
postfix/postfix-script: warning: /var/spool/postfix/etc/resolv.conf and /etc/resolv.conf differ
--------------------------------------------------------------------
root@merlin:/etc/resolvconf/update-libc.d# cat postfix 
#!/bin/sh -e

# modified to try to stop the bit rot that breaks sending mail
exit

# make sure we're still here...
[ -x /usr/sbin/postconf ] || exit 0

cp /etc/resolv.conf $(/usr/sbin/postconf -h queue_directory)/etc/resolv.conf
/etc/init.d/postfix reload >/dev/null 2>&1 || exit 0

exit 0
--------------------------------------------------------

---

