---
title: "Home network with DNS names?"
date: 2013-10-25
forum: Networking &amp; Wireless
---

### Post by MOGuy78 on 2013-10-25
Hi everyone.  I'm sure this has a very simple answer, but me being a newbie to using Ubuntu Server and
the CLI, I need some help.  I have two media servers set up on my home network.

I already have static IPs set up on my two servers, but is there a way to place a name on these computers?

Here is the "/etc/networking/interfaces" file from one of my servers:

auto eth0
iface eth0 inet static
address 192.168.2.10
netmask 255.255.255.0
gateway 192.168.2.1 

with 192.168.2.10 being set as the static ip for my music server and 192.168.2.1 being the address to my router.


This has been working fine ever since I first set up my file server close to 6 months ago.  What I'd like to
do is set up my server so that my family can get to it easier using a name.

For example, instead of having to type in this long address "\\182.168.2.10" to get to my music server, if my
sister would like to listen to music all she would need to do is type something such as "\\Music".
She will still be in the same house as myself, so I wouldn't think I would need to get a domain name from the internet.

Is there a way to do this?

---

### Post by steeldriver on 2013-10-25
The avahi Zeroconf / mDNS service should do that for you by default - the format is *hostname*.local rather than a FQDN e.g. if your server's unqualified hostname is 'Music' you should be able to access it as 'Music.local'

If typing the *.local* suffix is still too much, you can put each IP address pair and hostname in every computer's /etc/hosts file e.g.

```

$ cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    lap-t61p

# added local hosts IPv4 lookups so I can accesss them without DNS or mDNS/Avahi
[COLOR=#0000ff][B]192.168.1.65    htpc-01
192.168.1.127   nas-01
[/B][/COLOR]
```

---

### Post by Morbius1 on 2013-10-25
Don't get me wrong I believe that mDNS is the 21st Century way to find hosts by name in the home network but I had assumed that the client machines were Windows since all of the slashes are backwards from what they should be ( i.e., "\\182.168.2.10" ). Windows doesn't know nothin' about no mDNS, Avahi, or Bonjour unless you add something to them: [http://support.apple.com/kb/DL999](http://support.apple.com/kb/DL999)

I guess the question I have is if the servers have static ip addresses why aren't they "mapped" in windows?

---

### Post by MOGuy78 on 2013-10-26
Thanks Morbius1!  I was all about trying to do this the hard way and didn't even think of going through Windows.  I didn't even
worry about mapping it, all I did was simply make a shortcut to get to it.

Thanks for all the help guys!

---

