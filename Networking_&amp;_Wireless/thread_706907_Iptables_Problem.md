---
title: "Iptables Problem"
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by crab_com on 2008-02-24
Hey all,

I've just installed Ubuntu 7.10.

I'm a Fedora enthusiast but had few troubles with fedora things crashing etc. So swapped over to Ubuntu.

My problem currently is that I would like to unblock ssh so i can use it over my network as this machine is a stand alone.

What I have done so far is these commands.

> sudo iptables -A INPUT -p tcp --dport ssh -j ACCEPT

> sudo sh -c "iptables-save > /etc/iptables.rules"

Wondering why can't i get a connection over SSH once this is forwarded, and why when i reboot that the tables clear.

Never really had trouble with iptables like this cause my commands always worked in fedora. Just wondering if someone could point me in the right direction.

Cheers, Crab

---

### Post by crab_com on 2008-02-24
/bump

---

### Post by HermanAB on 2008-02-24
Hmm, change the -A to -I.

Cheers,

Herman

---

### Post by crab_com on 2008-02-25
sorry mate that didn't work

sudo iptables -I INPUT -p tcp --dport ssh -j ACCEPT

any other ideas?

---

### Post by crab_com on 2008-02-25
/bump

---

### Post by SpaceTeddy on 2008-02-25
Pakets on a network flow on two directions... not only one. Allowing the just the INPUT or the OUTPUT of a packet never works. Either you cannot send the request to receive the data, or you can send the request, but cannot receive the response... 

You need at least two rules to do that... i would suggest the following

> iptables -I INPUT -m state --state ESTABLISHED -j ACCEPT
iptables -I OUTPUT -m state --state ESTABLISHED -j ACCEPT

these two rules will accept any paket that is using an established connection, but will not allow any connection to be initiated. These are generic rules and allow you to open a port with only ONE rule... so it a neccessary evil to have two generic ones to be able to open a port with one rule :)

then, to acctually allow ssh, you only need one rule, specified as
> 
iptables -A INPUT -m state --state NEW -p tcp --dport 22 -j ACCEPT

which will allow the initiation of a ssh connection TO the host (note that this does NOT allow an ssh connection FROM the host)

hope that helps...

---

