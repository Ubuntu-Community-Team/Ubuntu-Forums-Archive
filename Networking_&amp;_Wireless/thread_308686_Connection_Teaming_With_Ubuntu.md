---
title: "Connection Teaming With Ubuntu"
date: 2006-11-28
forum: Networking &amp; Wireless
---

### Post by juliuss on 2006-11-28
Hi All,

I have a sort of advanced question.  I figure a complete response might be too much to ask for, so I mainly looking for some helpful links.

I would like to implement "connection teaming" on my ubuntu box.  My network should look something like this:

[FONT="Fixedsys"]
( ==Internet== )
[COLOR="White"] . .[/COLOR]| [COLOR="White"]. . .[/COLOR] |
[COLOR="White"] . [/COLOR]NIC1[COLOR="White"] . .[/COLOR]NIC2
[COLOR="White"] . .[/COLOR]|[COLOR="White"] . . . [/COLOR]|
( ==UbuntuBox= )
[COLOR="White"] . . . .[/COLOR]|
[COLOR="White"] . . .[/COLOR]ROUTER
[COLOR="White"] . .[/COLOR]| | | | |
( ====LAN===== )[/FONT]

Long story short, I'd like to use this ubuntu box to have two different WAN connections, splitting http requests between the two connections.  If one goes down, then it would automatically use the other one.  My reasons for doing this are complicated, but overall, just understand that I have two connections that are neither very reliable.

After that I'm going to set up a third NIC to connect the other computers on my LAN to the internet through the ubuntu box.

My questions are

1) Is connection teaming possible on linux?  (I've seen people say yes, but they haven't given many details.)
2) Are there any resource online that can help me do this?

If not -- then that's ok, I'll just have to keep manually switching when my WAN connection goes down.

Thanks All!

:p

---

### Post by juliuss on 2006-11-29
Hi all,

I found two good resources to get me started on this project:

Routing for multiple uplinks/providers
by Bert Hubert
[http://lartc.org/howto/lartc.rpdb.multiple-links.html](http://lartc.org/howto/lartc.rpdb.multiple-links.html)

Nano-Howto to use more than one independent Internet connection.
by Christoph Simon
[http://www.ssi.bg/~ja/nano.txt](http://www.ssi.bg/~ja/nano.txt)

I'm going to implement this and we'll see how well it works.   :mrgreen:

---

### Post by juliuss on 2006-11-29
I found a few other relevant threads on this message board if anyone is looking to do the same:
[http://www.ubuntuforums.org/showthread.php?t=163453](http://www.ubuntuforums.org/showthread.php?t=163453)
[http://www.ubuntuforums.org/showthread.php?t=99668](http://www.ubuntuforums.org/showthread.php?t=99668)
[http://www.ubuntuforums.org/showthread.php?t=201713](http://www.ubuntuforums.org/showthread.php?t=201713)
[http://www.howtoforge.com/nic_bonding](http://www.howtoforge.com/nic_bonding)

---

### Post by trubblemaker on 2006-11-29
kewl I'm book marking this page thanks! If you so a wireless specific one let me know although I'm sure It's close to the same thing.

---

### Post by weenis on 2008-05-19
Did you ever get it working?

---

