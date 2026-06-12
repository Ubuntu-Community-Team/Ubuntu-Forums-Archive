---
title: "Wireless card needs to WAKEUP!"
date: 2008-11-20
forum: Networking &amp; Wireless
---

### Post by MikelW on 2008-11-20
I have ubuntu 8.1

I am having a problem w/ my wireless card. I get disconnected from my router about once a day (my routers fault, befw11s4=crap). I have to reboot my router to get it going again.

 After i do that all wired stuff starts working. 

In order to get ubuntu (the only wireless i have) to connect wireless i need to goto edit connections, delete my saved network pass, and re-connect, re-typeing the password (this MAY be my routers fault, i'm unusre how wpa2 works exactly, 

either:
A.the wireless card sends password, and the router makes the string that the password really represents and sends it back. If this is true , then i'm sure its my routers fault.

or 

b. ubuntu takes the password and creates the encrypted key from it, and sends the key to the router. If this is the case then it must be ubuntu's fault cause theres no way that my router could know if i delete the connection and re-type it. And that works everytime.

now.. after i do get connected wirelessly i still cannot get online even though i get the right ip (configured in the router)
I cannot ping the router, or anything for that matter.

so what i have to do is ping the router and let it go.. for a bout 10-30 times i get 
ping: sendmsg: operation not permitted

and then after a while it starts workign and i start getting replies.. Once that happens i'm online. 

I've been searching around for a while and the only direction i may be finding is something with IPTABLES, which i don't know much about. However on this machine i do have an xbox masqueraded through its ethernet port, and if i remember right, there was some playing around with the iptables, but it worked right (just not having to ping) for a long time, and just recently started doing this. Only thing i've installed recently was compiz.. but i wouldn't imagine...

So any ideas or leads would be cool, Any files you need or anything just let me know and i'll post em.
Objectives:
 Would like to know why wlan0 is not responding for a while (main)
 Does wpa2 bitstring get generated on the client or server? and does it change without the password changing (could really care less)

---

