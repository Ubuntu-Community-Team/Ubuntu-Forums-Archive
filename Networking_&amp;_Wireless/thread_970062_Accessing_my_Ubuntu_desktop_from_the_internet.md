---
title: "Accessing my Ubuntu desktop from the internet"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by nimsu on 2008-11-03
I'm looking to access my ubuntu desktop from a remote pc on the internet. My goal is that I use my work computer to access ubuntu (and the gui)so I can install and configure the system from work.

Currently I use logmein for my work pc to my home pc. I'd like to do something similar. I've been reading about ssh and it sounds like the way to go, but just wanted to get some advice.

can i use a gui?
i don't have a domain, but my cable modem has a pretty static ip, so i'm comfortable just using the ip
is ssh the easiest way?
honestly don't care how secure it is

---

### Post by pansz on 2008-11-03
If you go ssh way, you can run any GUI applications, but you won't get a gui desktop, instead, you got the remote gui applications running in your local X11 desktop. If that is what you can live with, then ssh is the easist.

Just make sure you are not behind a firewall (if you are behind a firewall please make sure the port 22 are forwarded properly)

Then make sure you had "sudo apt-get install openssh-server" in your home pc.

I assume your work pc is running ubuntu too, then you can use 
```

ssh -X your.ip.address.here

```

to connect to your home pc.

---

