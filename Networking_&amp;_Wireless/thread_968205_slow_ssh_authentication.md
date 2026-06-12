---
title: "slow ssh authentication"
date: 2008-11-02
forum: Networking &amp; Wireless
---

### Post by shortridge11 on 2008-11-02
I ssh into my home server a lot.  My home server is on a gig lan, but it's slow for some reason i have yet to figure out.  When i ssh into my server, it takes about 10-18 seconds until it asks me for my password, and after that it's at a good speed.  Is there a way to speed up the time it takes to connect to it?  It takes the same amount of time to connect if i'm outside the network (ssh [www.xxxxxxx.net](www.xxxxxxx.net)) vs being in my house on the network.  If this is normal, please let me know.
Thanks

---

### Post by austin512 on 2008-11-02
Most likely it is doing a reverse DNS lookup, and either you have a slow connection with lots of lag (eg satellite internet), or your DNS is configured incorrectly.

Unless you need it to do reverse DNS lookups, the easiest solution is just to disable it. Add "UseDNS no" to the /etc/sshd_config file, reload your SSH server and the delay should be gone.

Note: it still does DNS lookups, but doesn't require it to be valid to let you log in, so it should prompt for your password right away.

---

### Post by shortridge11 on 2008-11-02
Well, i don't think it's a DNS problem.  If i use a program like putty, it asks for my login after about 2 seconds.  It's the time between me using a user name and it asking for the password that takes forever.  I'm pretty sure that i've got the connection after it asks for my login name, and since i have the same problem when i'm on the same network as the machine, i'm led to believe that it's not a DNS problem.  Any thoughts on this?

---

### Post by maxhax on 2008-11-02
Did you try and edit /etc/ssh/sshd_config?  I've seen this too.  I always add an entry that says UseDNS no and reload ssh.

> sudo /etc/init.d/ssh restart

Even from the inside it's going to do a reverse lookup to log your FQDN.  It populates this information in your $PS1 if it's set to pick it up and stores all this in /var/log/wtmp.

You don't have anything odd in PuTTy like X11 forwarding?

---

### Post by shortridge11 on 2008-11-02
thanks both of you. That fixed it.  I had no idea it did a reverse lookup

---

### Post by shortridge11 on 2008-11-03
can you explain in higher detail why it does the reverse DNS lookup? and what a FQDN is and why it's logged?

---

### Post by maxhax on 2008-11-11
Probably so you don't have to use DNS to resolve IPs when searching through logs...that's a guess, but might make sense in certain cases.  FQDN is a Fully Qualified Domain Name.  aka [www.google.com](www.google.com).  Bascially it's the full name that equals the machine, because aside from enterprise scale issues domain names point to individual hosts.  But like I said, the ballgame changes when you want it to scale.  

-maxhax-

---

### Post by cohawk@yahoo.com on 2008-11-30
Actually UseDNS didn't work for me. Adding the -u0 option to sshd worked though.

For people behind broadband routers that function as DNS servers to internal machines, they would not respond to unknown queries, thereby causing the resolver to 'hang'. Another way is to manually configure a host in /etc/hosts if you are only going to be logging in from one machine.

---

### Post by shaileshjkumar on 2009-05-06
Sorry for cutting into the topic.
 
Is there a way we can do the same for the telnet?

---

### Post by eltreno on 2010-08-02
I have been looking for a solution for this for ages as my host won't change the sshd_config files (shared host)
So UseDNS no isn't an option for me

anyway:

if you add 
hosts_ip_address  your_domain
to your /etc/hosts file the password prompt will display almost straight away

eg
123.123.123.123 example.com

---

### Post by Tweeks_tx on 2012-01-06
The server side thing is not a fix.
The /etc/hosts thing is a hack at best.. a "bad idea"(tm) at worst.

The FIX is to change your client config from:
    GSSAPIAuthentication yes
to

    GSSAPIAuthentication no

This will fix the problem on both Mac and Ubuntu clients.

While you're at it.. if the newer hashed known_hosts thing pisses you off.. that can be fixed with this:
##    HashKnownHosts yes
    HashKnownHosts no

done deal.

Tweeks

---

