---
title: "Changing DNS permanently or temporarily?"
date: 2018-06-19
forum: Networking &amp; Wireless
---

### Post by Langstracht on 2018-06-19
I am (still) using ubuntu 14.04.

A Firefox extension which I want to use does not work.  The "Owner" claims this is because of "my" DNS setting(s).

I've done a bit of a hunt and have come up with results that I just don't understand.

Supposedly my current DNS is 192.168.0.1.  I thought this was to access my router.

The resolv.conf file contains 127.0.1.1

According to the Active Networks Connections window: 

the IP Address is             192.168.0.105, 
the Broadcast Address is 192.168.0.255, 
the Subnet Mask is          255.255.255.0, 
the Default Route is         192.168.0.1, 
the Primary DNS is          192.168.0.1

So I have three questions:

1 - what will be the result if I edit resolv.conf and add "nameserver xxx.xxx.xxx.xxx".  More specifically will this have any effect on overall internet access.  What, if anything, do I do with "127.0.1.1"?

2 - if I make the change and it causes problems - like no internet access - how do I fix it?  Simply remove the "new" line in resolv.conf?  Or does something else need changing/correcting.

3 - I would just as well do a CLI input when I want to use the extension.  Can I do this?

Thanks in advance for helping this DNS-ignorant, and somewhat paranoid, user out.

---

### Post by TheFu on 2018-06-19
14.04 is a long time ago. The way DNS settings are handled has changed every LTS release since 12.04.

At some point, resolv.conf became managed by a new package, resolvconf. If you manually modify it, within 1-2 minutes, those modifications will be wiped.

127.0.1.1 is another internal IP for localhost. Basically, somewhere along the line, Canonical decided that running a tiny DNS caching server locally would make sense.

I usually remove/purge any of these extra packages since I can manually manage resolv.conf myself.  On a desktop, I don't know what I'd do ... I'm a server guy (no GUI) and run an internal DNS for the LAN, so there isn't any need to have caching on each machine/VM.

I've had terrible slowness in Firefox since around November on my primary desktop.  Everything else works great there.  My desktop is running inside a VM, so it doesn't have a GPU.  On my main laptop, firefox isn't slow. Both are running 16.04/openbox, so not the same desktop as you.

Hopefully, someone who understands the desktop you are running on the OS you are using will respond.

---

### Post by SeijiSensei on 2018-06-20
You cannot solve the issue permanently by editing resolv.conf.  I believe 14.04 used "resolvconf" which rewrites resolv.conf on each boot.

One thing you can try is to see if you have an /etc/resolvconf/resolv.conf.d/ directory on your machine.  In that directory is a file called "head" which provides the header for resolv.conf when it is rewritten.  If you have that file, edit it as root with sudo and add "nameserver 8.8.8.8" (Google's primary DNS) below the comments that appear at the top.  Save the file and reboot.  What nameserver do you have now?

---

### Post by TheFu on 2018-06-20
The resolvconf manpage:```

       Normally  the  resolvconf program is run only by network interface con&#8208;
       figuration  programs  such  as  ifup(8),   ifdown,   NetworkManager(8),
       dhclient(8),  and pppd(8); and by local nameservers such as dnsmasq(8).
       These programs obtain nameserver information from some source and  push
       it to resolvconf.
```

So restarting networking should be sufficient.  I've seen changes happen just because I touched the /etc/resolv.conf file manually and something put it back within a few minutes.  I don't remember the specific Ubuntu release when that happened and I'm only 90% certain it did. Sorry.

---

