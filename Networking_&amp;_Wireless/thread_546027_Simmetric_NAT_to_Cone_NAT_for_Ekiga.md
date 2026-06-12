---
title: "Simmetric NAT to Cone NAT for Ekiga"
date: 2007-09-08
forum: Networking &amp; Wireless
---

### Post by Linux_oid on 2007-09-08
When I try to start *Ekiga* it always give me " [...] Simmetric NAT.  [...] change into Cone NAT. [...]"

DI-524 is my wireless router. I opened all  [ports]("http://wiki.ekiga.org/index.php/Internet_ports_used_by_Ekiga") for Ekiga and it still gives me the same answer. 

Anyone?

---

### Post by Linux_oid on 2007-09-09
"Ekiga behind the NAT router" wiki is [here]("http://wiki.ekiga.org/index.php/Ekiga_behind_a_NAT_router#What_iptables_rules_could_I_use_for_GNU.2FLinux.3F")

Unfortunately, the scrip they have there didn't fix my problem as it suggested. My box was disconnected  from internet when I ran script. Setting of my network card wasn't changed but I had to reboot to be able to go internet.

---

### Post by univremonster on 2007-10-27
I'm way confused by this stuff... never worked with a modem or anything before, and now I have to change ports and change something called a NAT from symmetric to a cone... can somebody tell me how to get this program working and, as a bonus, if you could explain to me what is going on I'd be thrilled.  I don't want to go around messing with IPtables and gconf-editor without knowing a little bit about it.

---

### Post by atomic_turtle on 2007-10-28
Hi,

same story here. I tried forwarding Portrange 5000 to 5100 as the Ekiga-Wiki suggests, I ran the script there - after creating two directories it needs to run correctly - but when I press the >Detect NAT< button in the config druid, it still talks about "symmetric NAT" and about forwarding the required ports.
I have an account with ekiga.net and the stun-server entered.
Any ideas? In case I figure it out, of course I'll tell you. I'll edit it into the German UU Wiki if I do, maybe one of you guys wants to edit it into the English one.
Regards,

atomic_turtle

P.S.: A colleague told me there is an echo router on [email]500@ekiga.net[/email]. When I try to reach that, I'm told that there is a connection, but that there is a problem with my soundcard. Problems with my soundcard are my rheumatism - they keep on popping up ;-)

---

### Post by atomic_turtle on 2007-10-28
Hi,

I think now it works for me - at least I'm able to reach the Echo-Server [email]500@ekiga.net[/email] and my Sound is in order, too, after I've activated Full Duplex in the System settings.
Here's what I've done (I'm going to unravel it step by step now to see which steps are really necessary)
- I´ve forwarded Ports 5000-5100 on my Router
- There is a field called >Base Host Port< on my Router. I've set that to 5060 which is the main listening port according to the Ekiga-Wiki
- Also in the Ekiga-Wiki, there is a script which I executed. To do that, I only had to create (by using the "touch" command with sudo) the two files in line 9 and 10 of the script (I got an error message the first time I tried that pointed me there, I didn't adapt anything else).
Funnily, the config Druid in Ekiga still tells me I have symmetric NAT. 
I haven't tried with someone else yet, but if I can reach the echo server, there's no reason why I shouldn't be able to reach another person.
Regards,

atomic_turtle

---

### Post by atomic_turtle on 2007-10-28
Hmm... it seems the Port-Forwarding is not even necessary. So maybe it is enough to execute the script in the Ekiga-Wiki.
The config druid still says "symmetric NAT". Well, that might be why the druids didn't subsist...
But I haven't yet tested it "live" with a collocutor. It might be that I can reach someone (i.e., the echo server) on the internet, but no one can reach me. I hope it will work, though.
Regards,

atomic_turtle

---

