---
title: "Network installation of software (remote install)"
date: 2008-03-06
forum: Networking &amp; Wireless
---

### Post by bazzer on 2008-03-06
I need to install a package to 30+ Ubuntu clients on a network. Currently, I'll find the device's IP address and **ssh **to it, then **apt-get install** the software. Since I will be doing this 30 times, naturally, I want to find a better way.

Any ideas?

---

### Post by SpaceTeddy on 2008-03-06
multixterm could be the answer... 

script is found [here]("http://expect.nist.gov/example/multixterm") 
man page is [here]("http://expect.nist.gov/example/multixterm.man.html")

it lets you control multiple xterm sessions at the same time - so just spawn how many logins you need (i really hope you have at least the same password everywhere) and you can controll them with one input...

one application to rule them all :)

---

### Post by bazzer on 2008-03-06
Excellent! Cheers for that!

I actually fiddled around with cluster ssh (cssh) and installed some software just now.

I wonder though, if this is something we may need more of to compete with Microsoft Networks in a corporate environment. I know you can configure Microsoft SMS server to install stuff remotely, among many, many other tasks. I can't see a Linux equivalent. Maybe it's 'easier' on MS because of the MS Domain / Policy thing?

I'd love a 'remote admin' gui with IP addresses and hostnames of all the Linux clients on my network. Big buttons to install software (like synaptic?), shutdown, edit crontabs, start world domination and so on....

---

### Post by bazzer on 2008-03-12
For anyone who cares, I just read the homepage for Canonical and came across [Landscape]("http://www.canonical.com/projects/landscape"). Looks intriguing. And a little costly.

---

