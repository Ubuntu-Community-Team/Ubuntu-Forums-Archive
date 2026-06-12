---
title: "etc/networks"
date: 2007-05-27
forum: Networking &amp; Wireless
---

### Post by Scroopy on 2007-05-27
Hello... I can't find the /etc/networks file on my ubuntu machine.  It isn't there.  Anyone know why I don't have this file?

---

### Post by Stephen Howard on 2007-05-27
Hmm, I tried *dpkg -S networks* to see which package provides it, but it isn't listed.  The closest I can get is that there's an identical file placed in */usr/share/base-files* by the *base-files* package.  I have no idea how it then makes its way into /etc - presumably copied via some script.

Here's my /etc/networks file:
> 
# symbolic names for networks, see networks(5) for more information
link-local 169.254.0.0

I can't see how the entry would be correct for my system, as my network is 192.168.1.*.  Doesn't seem to make any difference for me though as my network is running perfectly (as far as I can tell).

Here's the man page in case you don't have that either:

> NAME
       networks - network name information

DESCRIPTION
       The  file  /etc/networks  is  a plain ASCII file that describes known DARPA networks and symbolic names for these
       networks.  Each line represents a network and has the following structure:

              name number aliases ...

       where the fields are delimited by spaces or tabs.  Empty lines are ignored.  If a line contains a hash mark  (#),
       the hash mark and the remaining part of the line are ignored.

       The field descriptions are:

       name   The symbolic name for the network.

       number The official number for this network in dotted-decimal notation.  The trailing ".0" may be omitted.

       aliases
              Optional aliases for the network.

       This  file  is read by route or netstat utilities.  Only Class A, B or C networks are supported, partitioned net&#8208;
       works (i.e. network/26 or network/28) are not supported by this facility.

---

