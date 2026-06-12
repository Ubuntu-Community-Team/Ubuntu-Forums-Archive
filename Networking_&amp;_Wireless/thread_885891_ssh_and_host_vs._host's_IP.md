---
title: "ssh and host vs. host's IP"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by nycjeff on 2008-08-10
I'm trying to log into a computer on my network via ssh using keys
so if I do something like:
ssh jeff@jeff-laptop

I get a different response than when I do something like this:
ssh jeff@192.168.1.5   (192.168.1.5 is the IP address where the laptop is).

I guess I'm just wondering why that would be.

---

### Post by SpaceTeddy on 2008-08-11
ssh remembers the distinct names you connect to. Obvisouly, jeff-laptop is a different name as the 192.168.1.5. Even if jeff-laptop resolves to the same ip in the, they are handled different.

While the IP can never be changed if you connect to it directly, the hostname can stay the same while the IP behind it can change. So, if you were to move your laptop to, say 192.168.1.6 the name would still be able to resolve to the new ip, the name would still match, and the hostkey would still be the same - this ssh would not complain, even if your IP changed. 

So, it is quite normal that, if you address the same computer in two differnet ways, that it asks you both times.

The only other reason i could possibly think of is that jeff-laptop does not resolve to 192.168.1.5... which would explain the different response aswell :)

hope it helps :)

---

### Post by nycjeff on 2008-08-17
Thanks SpaceTeddy,
I've been trying to set up BackupPC with my computers and this gave me hours and hours of fun (trouble).
for those interested, I was getting the "unable to read 4 bytes" error message. 
In the end I changed the named version of my server to the IP address of my server on the LAN. 
so I used
192.168.1.5 0 Jeff
in my hosts file. 
that got things working after I replaced the security keys like 5 times. 
I guess when I was doing copying of keys I would use the ip address at the server instead of the name of the server. 
Although I think the reason I was doing that was because it would time out when I used the jeff-laptop name rather than the IP address.
Now that I think of it, would SSH have a way to resolve the name into an IP?
I've read that backuppc/rsync uses nmblookup to resolve that stuff. Will SSH do that automatically or not so much?
Well, Thanks again SpaceTeddy. I eventually stumbled across the answer but your answer makes me feel more secure in what I figured out.

---

### Post by SpaceTeddy on 2008-08-17
ssh uses, as far as i know, only the "normal" way to figure out names. And the normal way is DNS. So, you need an DNS internal dns server that resolves your local computer. If you have an internal dns server running that is paired with your DHCP server (essentially allowing dDNS) ssh would be able to resolve hosts internally. Netbios is NOT featured by ssh as it is an internet protocoll and not only LAN (besides, i don't like netbios anyway... it is too - messy).

i hope that answers your question...

---

### Post by nycjeff on 2008-08-17
I think it does.
Thanks again for the help.

---

