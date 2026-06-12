---
title: "UFW frustrates me. Should I user nftables instead?"
date: 2023-11-16
forum: Networking &amp; Wireless
---

### Post by georgy-trubetkoy-ru74 on 2023-11-16
**Prelude:**
Due the documentation (thanks Canonical). It is really bad in compare to nftables.
I reading it, and, for example, here is no word about the number of rule is it's priority. I find it only on practice. 
And here is many examples (about routing, protocols and etc.).
And list of rules - it is really painful. I had about 30 rules right now in my test environment.
And ufw enable/disable it is additional pain with systemctl and adding new rules.
I also found the article where said the ufw it is utility for nftables (???).

**Questions:**
So, anyone use the UFW in production? And do you think I should start to learn nftables and only it without UFW and firewalld?
Also, which resources can you recommend for study (excluding official docs)?

**Afterword:**
Please, don't think my message is offtop. I hope I also can help the newers who also can't decide which firewall he should start to learn.
Here is many solutions for tasks on Deb/Ubu:
If I need ssh - I will use only openssh,
If I need vpn - I will use only openvpn,
If I need to configure my network - I will use only netplan.
But with firewall here is still some vagueness.

---

### Post by The Cog on 2023-11-17
From the tone of your post, I definitely think you should start using nftables.

In answer to your questions, we use nftables in production where I work, although not many people know that. We have scripts that write iptables rules, but these days iptables commands are implemented by an nft-iptables backwards compatibility utility that accepts iptables user commands and then does nft configuration. I've been using nft at home for a couple of years or so, and I'm happy with it.
nftables is not that well known yet, so I can't recommend any really good resources other than [https://wiki.nftables.org/](https://wiki.nftables.org/) and [https://wiki.debian.org/nftables](https://wiki.debian.org/nftables). 

UFW is a wrapper program that takes less complicated commands, easier for non-networking folk to understand but reduced flexibility of course. It used to issue iptables commands behind the scenes to make things happen, but recently it can detect whether iptables or nftables is present, and use either. Do not try configuring with ufw and then editing the resulting rules with nft. Just use one or the other. 

Don't use nft examine the rules that ufw creates either, unless you are feeling masochistic. ufw creates a laybrinthine set of many many rules and tables to be able to support every possible ufw configuration - most are unused but the framework is all there. The rules ufw creates are not representative of a hand-crafted set of nft rules.

I don't know firewalld very well, but I'd say it's more complex than ufw but less capable than nftables. Like ufw, it creates iptables (or nftables?) rules behind the scenes. I looked at it a long time ago, and thought it better to go straight to iptables.

If you use nftables, don't forget to permit DNS, NTP, ICMP along with any other such basic services. Also allow everything to/from the loopback interface. I think forgetting these is why many people have trouble when they configure their firewall rules. ufw knows this and allows them without being told.

VPN: I strongly prefer wireguard. I don't know your use case, but wireguard is absurdly easy to configure in comparison with OpenVPN. It's also faster, by reports I've read.

---

### Post by ian-weisser on 2023-11-17
> **georgy-trubetkoy-ru74 said:**
> 
Due the documentation (thanks Canonical). It is really bad in compare to nftables.


Thank yourself instead of Canonical.
The [UFW documentation]("https://help.ubuntu.com/community/UFW") is written by the community. Any community member, including you, is welcome to improve it.

You are not a customer of Canonical. They owe you nothing.

---

