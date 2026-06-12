---
title: "XDMCP Gusty-Gusty Why hasn't this been RESOLVED YET???"
date: 2008-02-10
forum: Networking &amp; Wireless
---

### Post by Temp08 on 2008-02-10
I have to say I am appalled that this issue has not been resolved. Remote login is a very necessary function for a lot of linux users, myself included. So far as I have been able to research I cannot find a solid solution for a Gusty-Gusty remote login. This bug has been reported and has been a high priority for nearly 3 months now, what is going on??

---

### Post by Temp08 on 2008-02-25
Wow, okay. After weeks of having this annoying issue unresolved someone was nice enough to post a solution that gets xdmcp working. [http://ubuntuforums.org/showthread.php?t=692931&highlight=xdmcp+gusty+gusty](http://ubuntuforums.org/showthread.php?t=692931&highlight=xdmcp+gusty+gusty)  Thanks to nodanero for finally shedding some light on this thing.

Still unfortunately this doesn't seem to be the perfect xdmcp solution. When I give it a shot the interface seems very laggy and I cannot use anything that is on the desktop, just items from the drop down menu. Hope others have better luck.

---

### Post by dgrafix on 2008-02-28
This did not work for me, I too am desparate to getting this working.

---

### Post by Joeb454 on 2008-02-28
I've never used XDMCP, I've never had to. Though I had to point out a minor point ;)

It's **Gutsy** :lolflag: Sorry, it would've bugged me if I didn't say anything

---

### Post by nodanero on 2008-02-28
Have you checked that ipv6 module is not loaded?

```
lsmod | grep ipv6
```And check that xdmcp is not listening in udp6.

```
netstat -l | xdmcp
```

---

### Post by dgrafix on 2008-02-28
that first one brings up nothing. the second brings up xdmcp - file not found.

---

### Post by nodanero on 2008-02-29
Ups, sorry was my fault, this is the code.

```
netstat -l | grep xdmcp
```

---

### Post by peterl_j on 2008-03-05
Hi

I must also join in, has anyone got it to work, if so how.  I am also tired of "updates" breaking things and being forced to use windows.

Peter L-J

---

