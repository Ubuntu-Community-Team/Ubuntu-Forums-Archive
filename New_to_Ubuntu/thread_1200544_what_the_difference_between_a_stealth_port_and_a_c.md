---
title: "what the difference between a stealth port and a closed port?"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by heyyy on 2009-06-30
simple question simple answer

---

### Post by philinux on 2009-06-30
Really simple answer.

[http://www.google.co.uk/search?q=what+the+difference+between+a+stealth+port+and+a+closed+port%3F&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.co.uk/search?q=what+the+difference+between+a+stealth+port+and+a+closed+port%3F&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by k3lt01 on 2009-06-30
Stealth ports are hidden so they appear to not even exist because they are hidden from the outside world.

Closed ports are just that, closed. Nothing gets in, nothing gets out. They aren't hidden from the outside world but being closed stops traffic from coming or going.

---

### Post by heyyy on 2009-06-30
> **k3lt01 said:**
> Stealth ports are hidden so they appear to not even exist because they are hidden from the outside world.

Closed ports are just that, closed. Nothing gets in, nothing gets out. They aren't hidden from the outside world but being closed stops traffic from coming or going.

so how do the stealth ports react on traffic?
is it like neither comes in  nor goes out?

---

### Post by philinux on 2009-06-30
[http://www.grc.com/faq-shieldsup.htm#STEALTH](http://www.grc.com/faq-shieldsup.htm#STEALTH)

---

### Post by Mornedhel on 2009-06-30
When traffic hits a closed port, the source is made aware that the reason the packet didn't make it to the destination is because the destination has closed this port.

When traffic hits a stealthed port, the destination just discards the packets and the source never even knows the packets made it to the port (and no further). This can be useful to hide machines : if you just close all ports, the source still knows you're there.

---

### Post by k3lt01 on 2009-07-01
> **Mornedhel said:**
> When traffic hits a closed port, the source is made aware that the reason the packet didn't make it to the destination is because the destination has closed this port.

When traffic hits a stealthed port, the destination just discards the packets and the source never even knows the packets made it to the port (and no further). This can be useful to hide machines : if you just close all ports, the source still knows you're there.
With regards to stealthing ports there is much debate over its effectiveness to really make the computer "invisible" to the outside world.

Google stealth vs closed or something similar and you will see how the debate rages. There has been a bit of discussion on this forum about it as well.

---

### Post by k3lt01 on 2009-07-01
> **heyyy said:**
> so how do the stealth ports react on traffic?
is it like neither comes in  nor goes out?Its supposedly ignored which is a problem in itself because if a port didn't exist the machine searching for it would theoretically get a message saying it doesn't exist. Stealthed ports don't react at all so no message saying "yay" or "nay" with regards to the ports existence goes back to the originating machine so automatically the originating machine theoretically knows the port exists but it is hidden.

Hope that makes sense.

---

### Post by Mornedhel on 2009-07-01
> **k3lt01 said:**
> With regards to stealthing ports there is much debate over its effectiveness to really make the computer "invisible" to the outside world.

Google stealth vs closed or something similar and you will see how the debate rages. There has been a bit of discussion on this forum about it as well.

Yes, I was just outlining the idea behind closed ports and stealthed ports.

---

