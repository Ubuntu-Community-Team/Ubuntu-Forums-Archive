---
title: "macchnager on boot"
date: 2006-12-30
forum: Networking &amp; Wireless
---

### Post by AndEat on 2006-12-30
I am trying to macchanger to run at boot time, seems a simple task following 

:confused: 

[http://en.wikipedia.org/wiki/MAC_address](http://en.wikipedia.org/wiki/MAC_address)

created a script w/ 

macchanger -a eth* 

made it 755
chown/chgrp root
not sure what to title it: 'mac' for now
dropped it in to /etc/network/if-pre-up.d

expecting: a random generated MAC address on boot 
getting: the same MAC address

i might get it enventually, just throwing this up to get some input, maybe others do this have tried this, maybe others will want to try this.

---

### Post by AndEat on 2007-01-07
Anyone stumbling across this mute thread 

1. [http://ubuntuforums.org/showthread.php?t=316126&highlight=macchanger](http://ubuntuforums.org/showthread.php?t=316126&highlight=macchanger)

2 .man interfaces

](*,)

---

