---
title: "linux server question"
date: 2011-03-22
forum: New to Ubuntu
---

### Post by pyrofreak99 on 2011-03-22
i have an old 32 bit desktop computer that i have lying around and i was wondering if there was a way that icould make it into a server that would be able to scan other computers for viruses.  i dont know if this would make sense but a linux server that can scan for viruses on others computer on the network.

---

### Post by HermanAB on 2011-03-22
Howdy,

The best way to scan a Windows machine is with a Windows bootable CD, for example BartPE, with Spybot S&D, Malwarebytes, ClamWin and other utilities.

You can try it, using SMB and ClamAV, but I have my doubts about how useful it will be.  The problem with trying to remotely scan a Windows machine is that you typically cannot get network access to the areas where the malware is most likely to hide out.

---

### Post by pyrofreak99 on 2011-03-22
ah i see, well thank you good sir for your helpfull information :)

---

### Post by deconstrained on 2011-03-22
Yeah, scan other computers for viruses over the network? I dunno...Maybe if you set up a machine with Norton Enterprise to do security audits...
[http://www.symantec.com/business/support/index?page=content&id=TECH100454&key=51852&actp=LIST](http://www.symantec.com/business/support/index?page=content&id=TECH100454&key=51852&actp=LIST)
That wouldn't allow you to manhandle and cleanse hosts over the LAN though. One would think that in a secure network, how much can be done to each host over a network, and in how many ways, should be minimal.

...Or, maybe if you put a hot swap bay in it you could put the hard drives of affected computers into it and do secure virus scanning that way. But if it's Windows viruses you're after...there's not much Linux has to offer, unless you virtualize a Windows environment (which requires more processing power).

---

### Post by crispy_420 on 2011-03-22
There are some threats that do open certain ports on PCs but then we are talking a port scanner looking for said connections. You could always setup a server for a host based intrusion detection system (IDS) with OSSEC ([http://www.ossec.net/](http://www.ossec.net/)). The linux box would be the "server" and each windows machine would have a client installed and running as a service. 

That is about as close as I can think of until Linux has a AV solution MS Forefront out. That would be nice.

---

