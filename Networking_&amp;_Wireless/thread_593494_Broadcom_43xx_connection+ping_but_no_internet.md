---
title: "Broadcom 43xx connection+ping but no internet"
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by nise8181 on 2007-10-27
Hello, 
I have just installed a fresh ubuntu 7.10 inclusive the offered broadcast 43xx driver to enable WIFI at my fathers HP Compaq nx9105 laptop. Fortunatly I am now able to establish a wireless connection with WPA but my internet still doesn't work. I realy want to show my father how nice Linux could be but the following barrier hinders me:

- I can ping my router, external ip's and even something like ```
ping google.com
```

- but any connection in firefox or with apt-get get timed out

- also ```
host google.com
``` doesn't work

- my router works fine with a couple of windows and mac os mashines
- i already reset the route to be sure.
- there is no proxy server or firewall inbetween

- trough a wired connection every internet functionality (HTTP, SSH, IMAP) works fine

Do you need more informations?
What could I do to solve the problem?
(I think I read all other 'broadcom'-threads here but they are almost about earlier versions of unbuntu...)

---

### Post by jfrorie on 2007-10-28
> **nise8181 said:**
> Hello, 
I have just installed a fresh ubuntu 7.10 inclusive the offered broadcast 43xx driver to enable WIFI at my fathers HP Compaq nx9105 laptop. Fortunatly I am now able to establish a wireless connection with WPA but my internet still doesn't work. I realy want to show my father how nice Linux could be but the following barrier hinders me:

- I can ping my router, external ip's and even something like ```
ping google.com
```

- but any connection in firefox or with apt-get get timed out

- also ```
host google.com
``` doesn't work

- my router works fine with a couple of windows and mac os mashines
- i already reset the route to be sure.
- there is no proxy server or firewall inbetween

- trough a wired connection every internet functionality (HTTP, SSH, IMAP) works fine

Do you need more informations?
What could I do to solve the problem?
(I think I read all other 'broadcom'-threads here but they are almost about earlier versions of unbuntu...)

It looks like ICMP is working, but TCP/UDP is toast.  

Stab in the dark...Have you tried disabling ipv6?

Jim

---

### Post by nise8181 on 2007-10-28
Thanx for you suggestions Jim,

I followed [http://ubuntuforums.org/showthread.php?t=6841](http://ubuntuforums.org/showthread.php?t=6841) to disable ipv6 but unfortunatly the situation didn't change.

Any TCP/UDP request times out.

Now I have disabled WP2 and any other security options of my router to avoid further conflicts.

What else can I do?

---

### Post by jfrorie on 2007-10-28
> **nise8181 said:**
> Thanx for you suggestions Jim,

I followed [http://ubuntuforums.org/showthread.php?t=6841](http://ubuntuforums.org/showthread.php?t=6841) to disable ipv6 but unfortunatly the situation didn't change.

Any TCP/UDP request times out.

Now I have disabled WP2 and any other security options of my router to avoid further conflicts.

What else can I do?

What kind of response do you get from "telnet pop.gmail.com 995"

---

### Post by nise8181 on 2007-10-28
```
telnet pop.gmail.com 995
```

Response:
```
Trying 209.85.135.109 ...
Unable to connect to remote host: Connection timed out
```

that's it. Nothing happens.

---

### Post by akikos on 2007-10-29
I  have the same laptop and the same problem with you  and i can' t fix it :(. I want to get rid of completely windows but i can not do it for this reason.
 In addition, when i establish a manual connection the problem don' t be solved and  when I try to make  a connection with the  firefox  (with no dhcp) it  writes ' "looking up "website" '  for a long time.

I don't have WPA || WPE password on router. 


:frown:

---

### Post by nise8181 on 2007-10-29
Ok, I found a (hardware) workaround.

I bought a HAMA Wireless LAN USB 2.0 Stick which works out of the box (even on mac os). After wasting endless time 20 Euros were a good investment.

But anyway if there is someone around her could tell me which log file could give me a hint about whats wrong with my Broadcom 43xx card I would really appreaciate it.

---

