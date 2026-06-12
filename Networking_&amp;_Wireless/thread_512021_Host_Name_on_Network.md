---
title: "Host Name on Network"
date: 2007-07-28
forum: Networking &amp; Wireless
---

### Post by manzell on 2007-07-28
I am having a strange issue:

My 6.10 laptop is not identifying its host name on my network. The host name for the laptop is, say, "mycomputer" which is reflected when I look at system->administration->network. I'm directly wired into a WRT54GS router. My other windows machine is connected wirelessly, and it's host name seems to work properly.

When I check the DHCP clients table, I see my ubuntu machine listed, but without a host name. Additionally, my linux machine doesn't seem to recognize my windows machine host name except over smb (ie, smb://myXPbox works, but [http://myXPbox](http://myXPbox) does not, although it's running an apache service)

-

Why is this? I'd like to be able to connect to shares and such from my windows machine by referring to the host name rather than looking up the IP every time.

Thanks for the help?

---

### Post by swampdweller on 2007-07-28
I don't think this remains a problem with Feisty but
you might want to check /etc/dhcp3/dhclient.conf

In at least one earlier version, the hostname was not
sent before the DHCP server was queried for various
things, including the hostname, with the result that
your hostname got cleared at every connect.

If you don't have a line like this

send host-name "<hostname>";

but rather like this

#send host-name "andare.fugue.com";

that might be your problem.

---

### Post by noob12 on 2007-07-28
In order to resolve WINS names from your ubuntu box, you'll need to install the **winbind** package and add wins to the host resolution mechanisms in /etc/nsswitch.conf.

```

sudo aptitude install winbind

```

Then edit **/etc/nsswitch.conf** (as root) and find the line for hosts and add **wins** before **dns**

An example line might look like this:
```

hosts: files mdns4_minimal [NOTFOUND=return] wins dns mdns4

```

---

### Post by swampdweller on 2007-07-29
Ah!  That sounds like much better advice than mine.
Listen to Noob.  I only offered my little notion because
I felt bad that you had zero replies.    :)

---

