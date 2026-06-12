---
title: "iptables rules not working"
date: 2017-02-15
forum: Networking &amp; Wireless
---

### Post by lance bermudez on 2017-02-15
my set up is dansguardian on port 8080 ==> to squid proxy on port 3128 ==> to privoxy proxy on port 8118

I do not know iptables also my firewall of chose is firewalld. I was told that is need to use iptables because firewalld will not do what i want. I used 
:~$ sudo iptables -F
:~$ sudo iptables -t nat -F
before using the below iptables
This is the code I'm using
```

# Allows root (needed for apt-get &#8230;)
iptables -t nat -A OUTPUT -p tcp --dport 80 -m owner --uid-owner root -j ACCEPT

# Allows privoxy to connect to ports 80 and 443
iptables -A OUTPUT -p tcp -m multiport --dports 80,443 -m owner --uid-owner privoxy -j ACCEPT

# Allows dansguardian to connect to squid.
iptables -A OUTPUT -p tcp --dport 3128 -m owner --uid-owner dansguardian -j ACCEPT

# Allows squid to connect to privoxy.
iptables -A OUTPUT -p tcp --dport 8118 -m owner --uid-owner proxy -j ACCEPT

# redirect anyone trying to directly access squid back to dansguardian.
iptables -t nat -A OUTPUT -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j REDIRECT --to-port 8080

# redirect anyone trying to directly access privoxy back to dansguardian.
iptables -t nat -A OUTPUT -p tcp --dport 8118 -m owner ! --uid-owner dansguardian -j REDIRECT --to-port 8080

# redirect all traffic on ports 80,443 to dansguardian
iptables -t nat -A OUTPUT -p tcp -m multiport --dport 80,443 -m owner ! --uid-owner proxy -j REDIRECT --to-port 8080

```

The above code gives me this error iptables: No chain/target/match by that name.

how do I fix this?

---

### Post by SeijiSensei on 2017-02-16
To use REDIRECT you need to edit the PREROUTING chain, not the OUTPUT chain.  Try
```
iptables -t nat -A PREROUTING -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j REDIRECT --to-port 8080
```

---

