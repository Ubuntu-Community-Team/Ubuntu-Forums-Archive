---
title: "HOWTO get around flaky DNS servers: pointers to some simple methods"
date: 2007-09-05
forum: Networking &amp; Wireless
---

### Post by noob12 on 2007-09-05
A lot of ISPs seem to provide pretty flaky (unreliable) DNS service.  There are two pretty easy ways to get around this:  using OpenDNS servers (or other known reliable accessible servers) and local DNS caching.  Local DNS caching can also provide you considerably faster browsing and internet access.

[SIZE="3"][COLOR="Green"]
The first section of this HOWTO can also be used as a guide for configuring your box to use specified DNS servers, while still using DHCP for address and other configuration parameters.
[/COLOR][/SIZE]

**Using OpenDNS or other reliable servers**

This describes the typical case for DHCP clients.  If you have control over your router or DHCP service, you can get this across your whole LAN more easily by configuring your DHCP service to provide your reliable server addresses as the name server addresses in DHCP responses.

NOTE:  If you are in a corporate or school network where the DHCP service provides you with organizational DNS name servers, you generally do not want to do this, because you will lose the ability to resolve names from the organization's DNS service.  The caching setup referenced in the next section is still safe in this situation.

For the case of a DHCP client that is mobile or where you do not have control over the DHCP service configuration, the procedure is:
```

sudo gedit /etc/dhcp3/dhclient.conf

```
Add a **prepend** line or change the existing one to read:
```
prepend domain-name-servers 208.67.222.222, 208.67.220.220;
```

Reboot the whole machine or restart networking with 
```

sudo /etc/init.d/networking restart

```

The procedure for statically configured clients is to configure the desired reliable nameserver addresses directly by editing the file **/etc/resolv.conf** or by using  **System | Administration | Network | DNS** tab (applies to the standed GNOME edition UI).

**Setting up Local Caching**

An easy way to set up local caching is described in this blog entry
[http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/](http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/)

**Combining the Two**

If you've followed that blog entry to set up  a local cache, and you are using DHCP, you can combine the two by using
```
prepend domain-name-servers 127.0.0.1, 208.67.222.222, 208.67.220.220;
```
in your **/etc/dhcp3/dhclient.conf** file.

For the static case, just list your localhost **127.0.0.1** first in your static nameserver list.

---

### Post by armware on 2007-09-11
Quick question (slightly off topic). regarding the line that says:
```

#reject 192.33.137.209;

```

what does that mean? i figure it rejects that ip, but what is that ip? or is it just an example?

it caught my eye and now i'm curious. google showed nothing of interest.

---

### Post by noob12 on 2007-09-11
That is off-topic.  Whatever you're seeing in the existing file in comments is just what is shipped in the default dhclient.conf.  If you were to uncomment that line, you would be telling your client to reject any DHCP responses from any server that identifies itself with that server identifier.  You'll find the answer to this question and many others by reading **man dhclient.conf** (which is very much on-topic).

---

### Post by buzznot1012 on 2007-09-28
I've just installed Feisty on a Dell Dimension 2400, 2.6 GHz, 1.5 Gig of RAM and a wired DSL connection to the Internet.  I'm new to Ubuntu and so far I think it's great.

I can connect to the Internet, but my connection only seems to last a few minutes.  For some reason, my Gmail account continues to receive e-mail even after I cannot access other pages.

I'm sure I just have some kind of IP filtering running amok.  That's only a guess, though.

I went through the ADSL ethernet configuration without any trouble, but have no idea why my Internet connection is so short-lived.

Any ideas would be great appreciated!

---

