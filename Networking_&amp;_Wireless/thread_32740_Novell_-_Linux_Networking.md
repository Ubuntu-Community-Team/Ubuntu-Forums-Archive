---
title: "Novell - Linux Networking"
date: 2005-05-09
forum: Networking &amp; Wireless
---

### Post by jaclayton on 2005-05-09
Hey!  I know this has been posted elsewhere, but it's the final stumbling block before I can ditch Windows on my works PC.

All the networking hardware is working fine.  I can browse the web, get emails, etc.  Novell have provided a Linux Groupwise client which, although Java, does the job.  But I can't browse the Novell NDS fileservers.

I've configured IPX to use both 802.2 and 802.3 frames, I've rebooted any number of times, but whenever I try something simple like slist I get the following:

```
slist: Server not found (0x8847) in ncp_open
```

And it's starting to melt my brain.

Help!

---

### Post by dataw0lf on 2005-05-10
Can you ping the Novell servers?
Have you done: 
ipx_interface add -p <iface> 802.3
?

---

### Post by OneSeventeen on 2005-11-22
```
#sudo ipx_interface add -p eth0 802.2
ipx_interface: Primary network already selected.
#sudo ipx_interface add -p eth0 802.3
ipx_interface: Primary network already selected.
#slist
slist: Server not found (0x8847) in ncp_open

```

I'd really appreciate a bit of help as well... I really prefer this distro over SUSE, but I've got the Novell Linux Desktop sitting right next to me and it's starting to get a little tempting...  (well, not really... I really like Ubuntu, and can't stand paying for synaptic updates... I mean red carpet)

---

### Post by labrador on 2005-11-25
You need to be logged into the network first.

The command ncplogin will allow this.  In my case I had to specify -A
for the authenticating server by internet hostname, and also -S for
the shorter name that Novell knows the server host by.

Afterwards, you may also find that commands like ncpmount and slist
also need the -A and -S args to know what network you are referring to.

---

