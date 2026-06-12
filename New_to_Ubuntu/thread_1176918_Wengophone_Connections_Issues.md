---
title: "Wengophone Connections Issues"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by stoogiebuncho on 2009-06-02
A friend of mine is living on a university campus.  We are trying to connect through Wengophone.  She has used Wengophone from her laptop before without problems.  However, when she is connected to the university's wireless, Wengophone just says "Connecting..." forever and never logs on.

There are no proxy settings or passwords for the university wireless network.  Her laptop (running Xubuntu 8.10, by the way) connected automatically with no help from her.  Skpye works, pidgin works, everything else works.

Does anyone have any ideas?

Thanks.

---

### Post by jonobr on 2009-06-03
Hello


Skype is not a good comparison.
Skype is like a weed in that when its installed on a machine it finds some way to get out of the network and communicate with the outside world.
IT people have a hard time blocking Skype traffic.

Pidgin is also not a good comparison, as it uses ports that are know and allowed by IT people.

SIP (which is what wengophone uses) is probably blocked by your IT>

The question would be , are you able to call, and the phone gets answered , and you hear nothing in one or both directions.
Or, are you not able to call at all.

If the answer is the first one, then the RTP ports are being blocked.
The number of ports used for RTP (this carries your voice) is so large , IT have a problem allowing any number of ports open.

If the call is not going through at all, chances are they are blocking port 5060.

What you could do is install some openvpn program which will tunnel your traffic out of the network.
There are a few vpn clients and tunneling programs out there.
Something like openvpn gives you the client but will put ads in your browser for the privilige

Cheers

---

### Post by stoogiebuncho on 2009-06-03
Thanks for the response - I was wondering if it was something like that.  My friend can't even log in to Wengo, much less make a call, so I'm guessing that they are blocking port 5060.

My friend isn't that computer savy, so she would probably not be interested in installing something like openvpn.  

Would it make any sense to configure Wengo to use a port other than 5060?  I'm pretty sure I could talk her through that.

We can always use Skype if we can't get it to work, but I MUCH prefer Wengophone.  When I use skype on my computer, it takes around 70% of the processor.  Wengo uses 15%.  Plus, Wengo is open source, which is especially important for communication devices.

Thanks for your help.

---

