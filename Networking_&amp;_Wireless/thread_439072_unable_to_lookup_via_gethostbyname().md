---
title: "unable to lookup via gethostbyname()"
date: 2007-05-10
forum: Networking &amp; Wireless
---

### Post by irish_flu on 2007-05-10
Hey folks,

when I woke up this morning, my mail server was pretty jacked.  Zimbra isn't running, and I can't SUDO very well (once out of every 20 tries or so, SUDO will work).

(please note, my domain names have been changed to placeholders for posting in this thread)

When I try to SUDO, I get this error:
irish_flu@mail:~$ sudo <any command>
sudo: unable to lookup mail.domain1.com
mail.domain2.com via gethostbyname()

OK, so everything I read says my hostname is screwed up somehow in /etc/hosts.

So, I do this:
cooley@mail:~$ cat /etc/hostname
mail.domain1.com
mail.domain2.com

This server is acting as a mail server for two domains, that's why there are two of them (did I set this up wrong?).

Here is what my hosts file looks like:

127.0.0.1 localhost.localdomain localhost
192.168.10.40 mail.domain1.com mail
192.168.10.44 mail.domain2.com mail

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts




Any ideas what might be going on here?  It would appear my hostname is correct.  What am I missing?

Of course, this is my production mail server and everybody is having a cow....

---

### Post by irish_flu on 2007-05-10
One other thing:

I have BIND running, because I needed (for awhile) some split DNS going on.  So, I had this server use itself for local DNS, and made entries so that the two hosts noted above would return the private addresses instead of the public addresses.

While troubleshooting this issue today, I changed resolv.conf to use outside DNS servers (and thereby return the public addresses) in case that was jacking me up.

It made no difference.

---

