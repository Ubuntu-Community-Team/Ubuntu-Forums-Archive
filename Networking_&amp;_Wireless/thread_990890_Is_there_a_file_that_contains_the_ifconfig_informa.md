---
title: "Is there a file that contains the ifconfig information?"
date: 2008-11-23
forum: Networking &amp; Wireless
---

### Post by lievendp on 2008-11-23
Hi,

I'm trying to figure out if there exists a file that holds the info that ifconfig outputs? I mean: like /proc/net/arp does for arp info and /proc/meminfo does for memory info?

I tried strace ifconfig but did not find what I was looking for. I lack the skills to figure out if it is acutally in there.

Any pointer could be helpfull.

thanks.

---

### Post by amauk on 2008-11-23
the man page tells you where the info comes from
under the "FILES" heading at the bottom

ifconfig gets it's info from these files
/proc/net/socket
/proc/net/dev
/proc/net/if_inet6

---

### Post by kevdog on 2008-11-23
you can always make a file

ifconfig >> <filename>

---

### Post by lievendp on 2008-11-23
Thanks for the answers.

I have looked in the if_inet6 file which I saw in the output of strace but could not make any ipv4 from the info in there. I was hoping that there was a file that contained the ip's (v4) of the interfaces in cleartext|ascii but alas... nothing there.

I know that I can redirect the output to a file but the problem is that I was trying to figure out the ip of a (locked down) ltsp client which I'm trying to get to work. There was however a much easier way: I just looked up the ip in the leases and also it was visible during the boot of the thin client.

It seems out that I was looking in the wrong direction to get the ip address instead of looking in the obvious places. (ifconfig not being an option)

cheers!
Lieven

---

