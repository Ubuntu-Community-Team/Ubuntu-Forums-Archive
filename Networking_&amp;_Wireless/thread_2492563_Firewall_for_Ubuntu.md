---
title: "Firewall for Ubuntu"
date: 2023-11-15
forum: Networking &amp; Wireless
---

### Post by georgy-trubetkoy-ru74 on 2023-11-15
Hi all.

1) I know, what UFW is default firewall for Ubuntu, like Firewalld in RHEL, CentOS or Nftables in Debian (latest versions) and etc. 
2) I also know, what I can install any firewall on any distr.

So, can I use in Ubuntu server the Nftables firewall instead of UFW?

Why? I heared nftables is the best firewall in compare ufw and firewalld.

Correct me, if I'm wrong.

---

### Post by ian-weisser on 2023-11-15
> **georgy-trubetkoy-ru74 said:**
> can I use in Ubuntu server the Nftables firewall instead of UFW?

Yes, you can.
Go right ahead.
The "iptables" command switched to using nftables as its backend in Ubuntu 21.10. nftables has been part of every stock Ubuntu install since. 

> **georgy-trubetkoy-ru74 said:**
> I heared nftables is the best firewall in compare ufw and firewalld.

"Best" is a matter of opinion, not of fact.
They all do the same thing, and they all do it in the same ways and using the same tools.
The main difference is in the interface used for the human and machine to discuss the rules, and that's all about the human. Some humans prefer A, some prefer B, some prefer C.

---

### Post by TheFu on 2023-11-15
There's only 1 firewall on Linux.  The things we use are just interfaces into the kernel firewall capabilities.  The distinction may not seem important, but if you need/plan to use multiple interfaces, the order that those interact with their different named tables can matter greatly.  

"Best" is extremely subjective for almost any ranking.  We are all biased. Sometimes that bias is for things we already think we know how to use and sometimes it is for some "new" feature that we didn't know already existed in the older version.

UFW is meant for simple firewall controls. It can do some advanced things, but usually I'll use the iptables interface for anything non-trivial under Linux.  Because my experience with non-Debian distros is 20 yrs out of date, I've only played with firewalld a few times. Seems about halfway between ufw ease and iptables capabilities.  But I'm fairly ignorant on the details.

My normal rule is that for edge computers where I need greater control over the firewall, I'll use iptables.  For desktops or LAN-only servers, I'll use ufw, until my needs outgrow what I know UFW handles easily.

So, it just depends on what you need and what you like, which is "best for you."  Are you a desktop-only user?  I wouldn't bother with the complexities of anything other than UFW/GUFW.  If you are hosting your own VPN server(s) and need fine control over packets, forwarding, and blocking, then I'd pick from either the iptables or nftables interface programs. If I didn't already know a bunch about iptables (and have a great reference guide) already, I'd probably start with nftables today, assuming I'll have 22.04 or later releases only in my systems.

---

### Post by #&amp;thj^% on 2023-11-15
All good information already provided in the top two post here.
I too agree "Best" is a matter of opinion, I picked up firewalld around 5-7 years ago, and have just stuck with it.
```
 firewall-cmd --list-all
block (default, active)
  target: %%REJECT%%
  ingress-priority: 0
  egress-priority: 0
  icmp-block-inversion: no
  interfaces: enx70b3d55c01b3 surfshark_ipv6 surfshark_wg
  sources: 
  services: 
  ports: 
  protocols: 
  forward: yes
  masquerade: no
  forward-ports: 
  source-ports: 
  icmp-blocks: 
  rich rules: 

```
```
 firewall-cmd --get-zones
block dmz drop external home internal libvirt libvirt-routed nm-shared public trusted work

```
There is much to learn, and keep learning with firewalls.

---

### Post by The Cog on 2023-11-15
TheFu is right - there is only one firewall in Linux. It's built into the kernel so it's always there, and always implementing the configured rules, which are to allow anything.
You cannot directly configure this firewall, you need a program to do it for you. There are several.

**iptables** is the "traditional" way to do it. iptables is a command-line program, and in general you enter one command to make one change, like adding or deleting a rule. There are very many guides on the internet for iptables, because it has been around for a long time. iptables is deprecated, in favour of nftables though. You should regard it as obsolete and only receiving maintenance

**nftables** is the new way to do it. nftables is a command-line program, and in general you enter one command to make one change, like adding or deleting a rule. There are not many guides on the internet yet because it's still quite new. It has only become the default firewall in Ubuntu recently. Ubuntu currently ships with iptables-legacy and nft. iptables-legacy accepts iptables-format commands that folk are used to using and translates them into nftables, so you can be using nftables and not even know it.

If you're not already familiar with iptables then I recommend that you don't start using it - use nftables instead. Both can told to load their configuration from a file, though the file formats are quite different.

**ufw** (uncomplicated firewall) is a command-line configuration tool. It can do basic configuration, using commands that are easy to understand but can't configure complicated requirements. Much as TheFu says. I gather it can detect whether you are using iptables or nftables and will automatically use whichever is there. If you only have simple requirements then this may be the one to go for. 

**gufw** is a graphical interface for driving ufw. Again, only for simple-ish configurations because it's using ufw underneath (which uses iptables or nftables underneath). But some folk strongly prefer a GUI. But the layers underneath don't show and it's a pleasingly easy interface to use.

**firewalld** is (I think) Red Hat's command-line firewall utility which (I think) uses iptables underneath. I haven't used it much, but I'd say it falls between iptables and ufw in complexity.

Which is best for you depends on your requirements.

---

### Post by #&amp;thj^% on 2023-11-15
> **The Cog said:**
> 

**firewalld** is (I think) Red Hat's command-line firewall utility which (I think) uses iptables underneath. I haven't used it much, but I'd say it falls between iptables and ufw in complexity.

Which is best for you depends on your requirements.

It uses nftables as a backend: [https://firewalld.org/2018/07/nftables-backend](https://firewalld.org/2018/07/nftables-backend)
nftables
```
nft list tables 
table inet filter

```
```
nft list tables
table inet firewalld
table ip filter
table ip nat
table ip mangle
table ip6 filter
table ip6 nat
table ip6 mangle


```

---

