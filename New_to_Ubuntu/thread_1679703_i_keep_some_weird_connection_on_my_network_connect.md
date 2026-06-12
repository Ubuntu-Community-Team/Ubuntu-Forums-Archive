---
title: "i keep some weird connection on my network connection"
date: 2011-02-01
forum: New to Ubuntu
---

### Post by werty2010 on 2011-02-01
since a few days ago i've been seeing some ips which are establishing connection to my pc the moment im connecting to the internet...
i tried to look them up in the internet  but i cannot find any info
some of them are:  212.205.126.11   ,   212.205.126.73   ,    212.205.126.50
could someone more experienced tell what these are about?

---

### Post by VorpalBunny on 2011-02-01
Using the "whois" command, it appears that those ip addresses are in the address block that belongs to [akamai]("http://www.akamai.com/html/about/index.html"). I'm not sure what you mean by them establishing a connection to your pc. Is that message in the Firefox status bar, or in the Network Manager or something? If it's in Firefox it just means whatever website you're loading uses some code from Akamai so Firefox needs to connect to the Akamai servers to run those parts.

---

### Post by heron7 on 2011-02-01
gee , i wonder who else' following me :popcorn:.... 
Welcome to the .net freind  :p

---

### Post by werty2010 on 2011-02-01
im using a network tool to check where my pc connects to..
when i turn on the wifi on my laptop,the moment it connects to the internet (without opening any kind of application-just the network tool) i see these connections...

---

### Post by werty2010 on 2011-02-01
> **VorpalBunny said:**
> Using the "whois" command, it appears that those ip addresses are in the address block that belongs to [akamai]("http://www.akamai.com/html/about/index.html"). I'm not sure what you mean by them establishing a connection to your pc. Is that message in the Firefox status bar, or in the Network Manager or something? If it's in Firefox it just means whatever website you're loading uses some code from Akamai so Firefox needs to connect to the Akamai servers to run those parts.

Are you sure its akamai? 
because i've already searched that and nothing came up..

---

### Post by VorpalBunny on 2011-02-01
```

[nfm@claude tmp]$ whois 212.205.126.11
% This is the RIPE Database query service.
% The objects are in RPSL format.
%
% The RIPE Database is subject to Terms and Conditions.
% See http://www.ripe.net/db/support/db-terms-conditions.pdf

% Note: this output has been filtered.
%       To receive output for a database update, use the "-B" flag.

% Information related to '212.205.126.0 - 212.205.126.255'

inetnum:        212.205.126.0 - 212.205.126.255
netname:        AKAMAI
descr:          Betastrasse 10B
descr:          D-85774 Unterfoehring
country:        DE
admin-c:        FL775-RIPE
tech-c:         FL775-RIPE
status:         ASSIGNED PA
mnt-by:         OTE-ADMIN-MNT
source:         RIPE # Filtered

person:         Florence Lavroff
address:        Betastrasse 10B
address:        D-85774 Unterfoehring
phone:          +49(89)94006415
nic-hdl:        FL775-RIPE
source:         RIPE # Filtered

% Information related to '212.205.0.0/16AS6799'

route:        212.205.0.0/16
descr:        OTEnet
origin:       AS6799
remarks:      OTEnet S.A. Multiprotocol Backbone & ISP
mnt-by:       OTENET-GR-MNT
source:       RIPE # Filtered


```

I went off the netname: AKAMAI :-?

You could call Florence Lavroff :P

...who, after a search, appears to be the network strategy manager at Akamai. I think we are getting warmer.

---

### Post by werty2010 on 2011-02-01
ok...i'll pass
i guess i was a little paranoid..but still why my pc connects automatically to akamai without even opening firefox?

---

### Post by VorpalBunny on 2011-02-01
> **werty2010 said:**
> ok...i'll pass
i guess i was a little paranoid..but still why my pc connects automatically to akamai without even opening firefox?

Probably the tool you're using uses one of the services provided by Akamai.

It's ok to be paranoid! For a while I thought about not using the Internet at all, but then I compromised at just not putting anything out there that I didn't want ~6,000,000,000 people to see. :)

---

### Post by werty2010 on 2011-02-01
> **VorpalBunny said:**
> Probably the tool you're using uses one of the services provided by Akamai.

It's ok to be paranoid! For a while I thought about not using the Internet at all, but then I compromised at just not putting anything out there that I didn't want ~6,000,000,000 people to see. :)

agreed
but... wow i managed to suspect myself:lolflag:

---

