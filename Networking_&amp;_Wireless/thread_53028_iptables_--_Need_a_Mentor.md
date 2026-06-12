---
title: "iptables -- Need a Mentor"
date: 2005-07-29
forum: Networking &amp; Wireless
---

### Post by SuperMike on 2005-07-29
I need to interact here with someone knowledgable about iptables who is also friendly and appreciative that I am just learning this. I want to post questions and see if this person can give me concrete advice with an example here or there. I hope to learn enough that I can share with others.

I have already built my first firewall and enhanced it by figuring out how lokkit works, and my skill-level is that I'm an ex PHP and Python programmer. (It's a long story -- I used to do PHP programming until the layoff and then rehired me as a Linux sysop.) I have 3 years Linux experience. I'm running Ubuntu 5.04.

**Main Point** -- I want to make my workstation firewall better than it is. The reason is this -- if I'm ever compromised, such as with a malicious package author, every second counts regarding identity theft and I want to lock down well-known stuff from being able to send this kind of junk out. However, that's a lofty goal, so I'm trying to go with the 80/20 rule here.

My home workstation is behind an existing NAT router firewall box on DSL that so far is not penetrable by ShieldsUp. I use a static IP address. I need access for Ubuntu updates, ClamAV updates, IPSEC VPN, web, email, irc chat, AOL chat, ftp, and streaming audio. The only web pages I serve up are on loopback so that I can test out my web development. I do not serve up a website because that violates my DSL-provider's policy. (Besides, it's cheap to use webcomindia.net if you live in the USA.)

I have been told that there are two main pools of thought on building firewalls. 

One is lokkit -- geared for the noob and is like a funnel with tiny little holes at the bottom. This translates to an INPUT ACCEPT policy, then REJECT filters at the bottom of the INPUT policy chain.

The second one is geared for the more advanced user. This one is like squeezing water through a brick. This translates to an INPUT DROP policy with then ACCEPT holes poked through for various kinds of traffic.

Next, others have advised me to not forget about an OUTPUT policy, trapping well-known nasties from getting out once they are in, helping me control that identity theft thing.

Currently, my firewall script looks like this:

```

iptables -F
iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -p tcp -m tcp --dport 500 --syn -j ACCEPT
iptables -A INPUT -p udp -m udp --dport 500 -j ACCEPT
iptables -A INPUT -p udp -m udp -s MyDNS1.net --sport 53 -d 0/0 -j ACCEPT
iptables -A INPUT -p udp -m udp -s MyDNS2.net --sport 53 -d 0/0 -j ACCEPT
iptables -A INPUT -p tcp -m tcp --syn -j REJECT
iptables -A INPUT -p udp -m udp -j REJECT

```

I welcome your advice on how to make this better.

---

### Post by LordHunter317 on 2005-07-29
[QUOTE=SuperMike]I have already built my first firewall and enhanced it by figuring out how lokkit works,[/quote]To be fair, lokkit is a poor example to start from.

> and I want to lock down well-known stuff from being able to send this kind of junk out.On a workstation, this is a near impossible task, using iptables.

Think about it:  You need to be able to access the web.  So based on the headers, how do you tell legtimate web traffic from malicious web traffic? 

The answer is: you can't.  

> However, that's a lofty goal,Rather, it's impossible to do, without a higher level filter.

> One is lokkit -- geared for the noobLokkit isn't really geared for anyone.  

> and is like a funnel with tiny little holes at the bottom. This translates to an INPUT ACCEPT policy, then REJECT filters at the bottom of the INPUT policy chain.When you understand how iptables owrk, you'll understand this is no different from the one below.  The only difference is it doesn't use drop policy.

> The second one is geared for the more advanced user. This one is like squeezing water through a brick. This translates to an INPUT DROP policy with then ACCEPT holes poked through for various kinds of traffic.The problem here is you have to understand the POLICY is applied last: to all traffic that doesn't match any rule.  Even though it's display first, **it is matched last**.
Keep that in mind when design your rules.


> Next, others have advised me to not forget about an OUTPUT policy, trapping well-known nasties from getting out once they are in, helping me control that identity theft thing.As I said above, realistically, you'll have a hard time doing this.

> I welcome your advice on how to make this better.I'm not sure you need one.  It doesn't sound like you serve any traffic to the Internet from this box.  If you don't do that, the odds of being compromised due to anything but user error is low. 

Some more, exact deails on what you're trying to do here would be nice.  You say you want to stop identify theives, but encrypting data of value using GPG or a encrypted filesystem would go further for this than firewall rules.

---

### Post by SuperMike on 2005-07-29
LordHunter317,

This is good advice. I didn't realize this. I'll have to find another forum area to start a thread on installing encrypted file systems in Ubuntu like EncFS and getting it to work properly. (I've only read about that recently.)

I'm also trying to make a Gnome-based control panel that builds an iptables script for most home users in similar state to me, with the ability to poke extra holes through as necessary. It was going to be an improvement on lokkit. It was going to use the INPUT DROP strategy instead of the INPUT ACCEPT strategy, and was going to try to add some stuff to the OUTPUT chain so that I can satisfy some die-hard firewall fans. I got this to work and at least copy the functionality of lokkit, but not do the INPUT DROP strategy and OUTPUT chain stuff that lokkit doesn't do. That's where I think I need help. The end goal with this control panel is to offer it up on SourceForge.net for others to improve upon. The intended audience for it would either be admittedly paranoid folks like myself, or people who get on the Internet without a firewall and need at least a local one. I was thinking more along the lines of new users wanting something fairly basic, but slightly more powerful than lokkit.

I was trying to avoid other packages like firestarter because I like going out on my own and have had lots of trouble with other packages.

---

### Post by skyboy on 2005-07-30
Just a little thing though. Your "firewall" script isn't really cool because it won't allow you to legitimate allowed connection YOU make from your box to the world (chat, web browsing ....)
I have one script too, it doesn't pretend to be the best solution at all but anyway, it's good to share things :D and maybe somebody else can improve it a bit!

#allow connection I start
sudo iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
#ssh connection
sudo iptables -A INPUT -p tcp --dport ssh -j ACCEPT
#remote desktop control
#sudo iptables -A INPUT -p tcp --dport 5900 -j ACCEPT  
# web server
#sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT
#files sharing tcp, udp
sudo iptables -A INPUT -p tcp -m multiport --destination-ports 445,135,136,137,138,139 -j ACCEPT 
sudo iptables -A OUTPUT -p tcp -m multiport --destination-ports 445,135,136,137,138,139 -j ACCEPT 
sudo iptables -A INPUT -p udp -m multiport --destination-ports 445,135,136,137,138,139 -j ACCEPT
sudo iptables -A OUTPUT -p udp -m multiport --destination-ports  445,135,136,137,138,139 -j ACCEPT
#local accept everything
sudo iptables -A INPUT -i lo -j ACCEPT
#everything else DROP
sudo iptables -A INPUT -j DROP

---

### Post by frobroj on 2005-10-21
This little diddie works great in Fedora but not in ubuntu(I think because the 'recent' module is not compiled with their version of iptables). I actually have another thread opened to find out if there are any packages from ubuntu that will enable the 'recent' module... But no answers as of yet...

#iptables -A INPUT -m state --state NEW -m tcp -p tcp --dport 22 -m recent --rcheck --name SSH -j ACCEPT
#iptables -A INPUT -m state --state NEW -m tcp -p tcp --dport 4062 -m recent --name SSH --remove -j DROP
#iptables -A INPUT -m state --state NEW -m tcp -p tcp --dport 4063 -m recent --name SSH --set -j DROP
#iptables -A INPUT -m state --state NEW -m tcp -p tcp --dport 4064 -m recent --name SSH --remove -j DROP

It opens a port(ssh in the example) for a specific IP address after that source ip telnets to a specified port(4063 in the example). It is portknocking at its simplist level but it adds a huge layer of security. If you get it working just remember what your mom said "Were you born in a barn?". Remember to telnet to either of the close ports(4062 or 4064 in the example) when your done.

If you know anything about the 'recent' package I would love to hear about it...

---

