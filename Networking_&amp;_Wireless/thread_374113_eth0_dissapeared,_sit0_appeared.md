---
title: "eth0 dissapeared, sit0 appeared"
date: 2007-03-02
forum: Networking &amp; Wireless
---

### Post by trevorv on 2007-03-02
Hiya,

I'm having some issues with a fairly recent install (which is a server install + Fluxbox).

I have been quite happily connected to my wireless network and the internet via my laptop's eth0 interface, but this suddenly seems to have dissapeared, and I have gained a sit0 interface.

ifconfig -a gives me

```
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:400 (400.0 b)  TX bytes:400 (400.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

The last thing I remember doing beforehand was having to (un/re)install quite a few packages, to sort out dependency issues apt was having, and I thought perhaps I'd installed a new kernel and that was the problem, but I only seem to have the one kernel installed.

So, basically, please help me get eth0 back! And while we're at it, explain to me what sit0 is if you could, I can't see much on the net about it other than it being to do with IPv6.

Thanks, please help, I'm desperate to get off this GNOME live-cd and back to my little Fluxbox install!

---

### Post by trevorv on 2007-03-02
Right, as far as I can see, sit0 is unrelated and purely exists for IPv6 compatibility (although I've no idea why it didn't exist before?)

So, the problem seems to be that eth0 has simply dissapeared, and I have no idea why!

If anyone could suggest anything it'd be vastly appreciated!

---

