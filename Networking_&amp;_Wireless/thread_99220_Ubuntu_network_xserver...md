---
title: "Ubuntu network xserver.."
date: 2005-12-05
forum: Networking &amp; Wireless
---

### Post by adam.tropics on 2005-12-05
Could anyone explain, briefly is good (!) how resources would be used if a laptop were to run an xclient session from a desktop xserver? (Terminology confusing me a tad!) 
I'm interested in which would 'seem' (bit ambiguous) faster, a laptop running Ubuntu, with generally lesser spec, being a laptop. Or an Ubuntu laptop, running an Ubuntu xclient session from a far higher spec Ubuntu desktop!!! If it matters, the network could be either wired or wireless. whatever.

---

### Post by mips on 2005-12-06
I dont have any experience with Linux on this but I do recall exporting a X-session from a HP-UX workstation to a desktop over 10/100Mb ethernet was slow imho.

Hopefully someone here can share their experiences.

---

### Post by curuxz on 2005-12-06
Im currently trying the same thing, running 2 older comps (a desktop and a laptop) as thin clients of my main pc in my office, all over 100mbs network. I'll let you know if I manage it but so far it looks like i will have to use this NX server thing or the slow slow slow VNC.

:) PM me if you want to discuss X modifications for virtual amature mainfraiming, which I believe is what we are both trying...

---

### Post by afhp on 2005-12-06
X is especially confusing, as the server and the client are said to be opposite to what you'd expect...

In any case, you'll need the appropriate X server on your laptop -- that's the part that actually drives your hardware : videocard, mouse etc. Once X is up, everything else (including opening a session) can be done remotely. 

On the remote machine, you'll have to configure X to accept connexions from another machine.

I'll point you to the Linux Terminal Server Project's documentation as a starting point -- it deals with network booting and setting up the terminal as well, but the X part should be of interest. 

[http://www.ltsp.org/documentation/index.php]("http://www.ltsp.org/documentation/index.php")

---

