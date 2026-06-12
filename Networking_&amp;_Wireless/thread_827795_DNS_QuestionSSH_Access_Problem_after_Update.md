---
title: "DNS Question/SSH Access Problem after Update"
date: 2008-06-13
forum: Networking &amp; Wireless
---

### Post by matey3 on 2008-06-13
Hello All:

Ever since I apt-get the new updates for security I cannot ssh as root to any of my servers (which had updates applied) So I made me another user (other than root) but once I get in (by ssh) I cannot su or sudo. It asks for the password then says sorry! permission denied??!!
I found out that there was a problem with ssh key etc.
If you are having the same problem you can look here for possible solution;

[http://www.debian.org/security/2008/dsa-1576](http://www.debian.org/security/2008/dsa-1576)

Any way I also have a question about DNS.
Whenever I setup a new machine (Ubuntu/Linux machines) They do not register with DNS.

I looked for other machines names (which have been registered already) by using grep and I did find some but they were already in this BINARY file (which I dont think u can/should edit) Under /etc/bind/ and the server's name.
I found another file with the name like "zones".suffix of our domain which I edited and manually put the names and IP addresses of those machines in it and it kind of works!
lol @ Kinda..I mean I can ssh to them now but if I ping 1 it shows me a generic name like h-20-1.domain.com! And that is after I re-ran the named + the zones file (thinking I was re-compiling/updating the names in DNS)?

If any one can shed some light or give me a link I'd appreciate it. There are so many files and so many commands and I have tried many like host/hosts/bind (which makes some of my letters disappear from my keyboard??) and many other commands , but I'd like to learn the right way of registering the names of computers with our DNS (we have real IP addresses here and over 20 servers).

Thanks a lot!

---

