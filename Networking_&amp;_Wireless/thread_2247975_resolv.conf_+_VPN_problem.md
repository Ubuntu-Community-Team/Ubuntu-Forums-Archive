---
title: "resolv.conf + VPN problem"
date: 2014-10-11
forum: Networking &amp; Wireless
---

### Post by hipogrito2 on 2014-10-11
Hi,

Ubuntu 14.04 upgraded from 12.04

I have another variation of the resolv.conf issues that many people are posting.


Problem: I can only connect to the Internet if I'm through VPN to my company.


PAST: In 12.04. Every time I connected to my company via VPN DNS stuff was added to my resolv.conf automatically. DNS stuff related to my company servers. I don't know what system added that stuff, but I guess it had to be something within the VPN system. If then, I disconnected from VPN I could not connect to the Internet.

The solution was: Edit resolv.conf delete the 2 or so new lines that were added, leave that file completely empty, and then I could connect to the Internet without a problem.


NOW: in 14.04. I connect via VPN. I can browse the Internet. I disconnect the VPN. I can't browse anymore. The difference here is that if I open resolv.conf it's EMPTY already, so I can't use the same solution I used for 12.04.


Question: Does somebody know where might those 2 DNS lines that the VPN system (or whoever) are being added? Clearly not in resolv.conf....


Thanks!

Regards,
Hipo

---

### Post by hipogrito2 on 2014-10-14
Hi,

A little update.

Now I can't even connect to VPN! It seems I can't get pass the router.... but I can connect to the router without a problem... if I put 192.168.1.1 in a browser I get into my Verizon router log in.

So, the network is fine but I can't get to the Internet...

Yes I have rebooted the router.

Any suggestion of what to look for in a situation like this?

Note, this is a desktop and it does not have Wireless, just the wired connection, so, right now, that machine can't connect to the Internet. But I have a laptop so, in case I need to download stuff to upgrade things I can do it...

Thanks!!!

---

### Post by papibe on 2014-10-14
Hi hipogrito2. Welcome to the forum ):P

Make sure the resolv.conf file is a symbolic link:
```
$ ls -l /etc/resolv.conf 
lrwxrwxrwx 1 root root 29 May 19 13:38 /etc/resolv.conf -> ../run/resolvconf/resolv.conf
```
That way, when the networking stack is re initialized, you get new settings on the resolv.conf

The problem regarding the loose connectivity after you logout of your VPN, it may be solve running:
```
sudo service network-manager restart
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by hipogrito2 on 2014-10-14
Hi,

Mr. Papibe... the symbolic link was it! I wonder why it was missing in the first place but, it's working now! Thanks a lot!!!!

Just for the non initiated, this is how you create it:

First delete current resolv.conf
```

sudo rm /etc/resolv.conf

```

Then create the link

```

sudo ln -s /run/resolvconf/resolv.conf /etc/resolv.conf

```

And this is why this forum is so great :-)

Thanks,

Regards,
Hipo

---

