---
title: "Bypass ISP DNS Interception"
date: 2022-04-29
forum: Networking &amp; Wireless
---

### Post by sulfurman on 2022-04-29
Hello everyone.
I just upgraded from Lubuntu 18.04 to 22.
To bypass the DNS interception and use OpenDNS i used the following:
sudo iptables -t nat -D OUTPUT -p tcp --dport 53 -j DNAT --to 208.67.222.222:5353
sudo iptables -t nat -D OUTPUT -p udp --dport 53 -j DNAT --to 208.67.222.222:5353

and it worked well.

Now, in 22.04 it doesn't work.

Can someone help me to resolve ?
Thank you very much

---

### Post by TheFu on 2022-04-29
The 22.04 release notes [https://discourse.ubuntu.com/t/jammy-jellyfish-release-notes/24668](https://discourse.ubuntu.com/t/jammy-jellyfish-release-notes/24668) say nftables is the firewall backend now. Some problems are expected, since iptables isn't there.

iptables-translate package was already installed on my 22.04 system here. Alas, it refused to provide a translation for the commands above.  [https://wiki.nftables.org/wiki-nftables/index.php/Moving_from_iptables_to_nftables](https://wiki.nftables.org/wiki-nftables/index.php/Moving_from_iptables_to_nftables) has more options.

Maybe a better answer is to use DNSSEC or DNS-over-https instead?  Are those options for your needs?

[https://support.opendns.com/hc/en-us/articles/360038086532-Using-DNS-over-HTTPS-DoH-with-OpenDNS](https://support.opendns.com/hc/en-us/articles/360038086532-Using-DNS-over-HTTPS-DoH-with-OpenDNS) is just for browsers.
[https://www.cyberciti.biz/faq/configure-ubuntu-pi-hole-for-cloudflare-dns-over-https/](https://www.cyberciti.biz/faq/configure-ubuntu-pi-hole-for-cloudflare-dns-over-https/) is for using a pi-hole DNS filter AND DoH for your entire network.

But I can understand just figuring out how to enter the correct nftable command would be preferred.

---

### Post by sulfurman on 2022-04-29
Thank you very much for your quick response.
I didn't read release notes :)
As you said i prefer to find the correct nftable command.
I'll study the manual of this new framework but if someone has already found the solution please let me know.

---

### Post by The Cog on 2022-04-29
I don't understand that. the -D says you're just trying to delete existing rules. I don't see how that (in isolation) could ever have done anything.
Can you explain what was going on?

Incidentally, this will show your nft rules:
```
sudo nft list ruleset
```

---

### Post by sulfurman on 2022-04-29
Sorry. I just copied the command used to remove the rule.
The correct command i used are:
sudo iptables -t nat -A OUTPUT -p tcp --dport 53 -j DNAT --to 208.67.222.222:5353
sudo iptables -t nat -A OUTPUT -p udp --dport 53 -j DNAT --to 208.67.222.222:5353
sudo iptables -t nat -A OUTPUT -p tcp --dport 53 -j DNAT --to 208.67.220.220:5353
sudo iptables -t nat -A OUTPUT -p udp --dport 53 -j DNAT --to 208.67.220.220:5353

---

### Post by TheFu on 2022-04-29
Then **iptables-translate** works.  I just copied the rule provided which made it barf. The rules above are translated to nft. I'll leave the running of that command as a trivial exercise.

---

### Post by sulfurman on 2022-04-30
> **TheFu said:**
> Then **iptables-translate** works.  I just copied the rule provided which made it barf. The rules above are translated to nft. I'll leave the running of that command as a trivial exercise.

Yes! the translation works! :)
But something strange happens.
i try to explain.....

$ iptables-translate -t nat -A OUTPUT -p tcp --dport 53 -j DNAT --to 208.67.222.222:5353
nft add rule ip nat OUTPUT tcp dport 53 counter dnat to 208.67.222.222:5353
$ iptables-translate -t nat -A OUTPUT -p udp --dport 53 -j DNAT --to 208.67.222.222:5353
nft add rule ip nat OUTPUT udp dport 53 counter dnat to 208.67.222.222:5353

[B]Translation ok!
But[/B]
$ sudo nft add rule ip nat OUTPUT tcp dport 53 counter dnat to 208.67.222.222:5353
Error: Could not process rule: No such file or directory
add rule ip nat OUTPUT tcp dport 53 counter dnat to 208.67.222.222:5353
            ^^^
$ sudo nft add rule ip nat OUTPUT udp dport 53 counter dnat to 208.67.222.222:5353
Error: Could not process rule: No such file or directory
add rule ip nat OUTPUT udp dport 53 counter dnat to 208.67.222.222:5353
[B]
If, before the previous commands, i try the following:[/B]
$ sudo iptables -t nat -A OUTPUT -p tcp --dport 53 -j DNAT --to 208.67.222.222:5353
$ sudo iptables -t nat -A OUTPUT -p udp --dport 53 -j DNAT --to 208.67.222.222:5353

**the commands **
$ sudo nft add rule ip nat OUTPUT tcp dport 53 counter dnat to 208.67.222.222:5353 **and**
$ sudo nft add rule ip nat OUTPUT udp dport 53 counter dnat to 208.67.222.222:5353
**are ok! No errors!**

**But **
$ ping dnsleaktest.com
ping: dnsleaktest.com: Temporary failure in name resolution

**This is the ruleset table**
$ sudo nft list rulesettable ip nat {
        chain OUTPUT {
                type nat hook output priority -100; policy accept;
                meta l4proto tcp tcp dport 53 counter packets 0 bytes 0 dnat to 208.67.222.222:5353
                meta l4proto udp udp dport 53 counter packets 120 bytes 9236 dnat to 208.67.222.222:5353
        }
}

**If i flush it**
$ sudo nft flush ruleset

**everything goes well**
$ ping dnsleaktest.com
PING dnsleaktest.com (23.239.16.110) 56(84) bytes of data.
64 bytes from li685-110.members.linode.com (23.239.16.110): icmp_seq=1 ttl=46 time=134 ms

But no interception :(

---

### Post by The Cog on 2022-04-30
I don't see anything like "[FONT=Courier New]nft add table nat[/FONT]" mentioned here, which I would have thought was a prerequisite to adding rules to the table. At least, it is according to this page: [https://wiki.nftables.org/wiki-nftables/index.php/Performing_Network_Address_Translation_(NAT)](https://wiki.nftables.org/wiki-nftables/index.php/Performing_Network_Address_Translation_(NAT))

Try this:
```
nft add table ip nat
nft add chain nat output '{ type nat hook output priority -100; }'
nft add rule nat output udp dport 53 counter dnat to 208.67.222.222:5353
```

which produces this ruleset:
```
table ip nat {
	chain output {
		type nat hook output priority -100; policy accept;
		udp dport 53 counter packets 9 bytes 734 dnat to 208.67.222.222:5353
	}
}
```

I would definitely use tcpdump to verify what is happening on the wire.

I've just been trying it out myself, and the above is what seemed to work.

P.S.
I don't think the wiki I linked says (and I think it should) that it is not possible to perform DNAT from the postrouting hook, and it is not possible to perform SNAT from the prerouting hook.

---

### Post by sulfurman on 2022-05-02
Thank you very much The Cog for your patience.
 I tried the following (that you wrote).
Evething seems ok, the ruleset is like you wrote but the result is the same:

$ ping dnsleaktest.com
$ ping: dnsleaktest.com: Temporary failure in name resolution

I have to study a lot. 
If I'll find it, I'll post the solution.

> **The Cog said:**
> 
```
nft add table ip nat
nft add chain nat output '{ type nat hook output priority -100; }'
nft add rule nat output udp dport 53 counter dnat to 208.67.222.222:5353
```

which produces this ruleset:
```
table ip nat {
    chain output {
        type nat hook output priority -100; policy accept;
        udp dport 53 counter packets 9 bytes 734 dnat to 208.67.222.222:5353
    }
}
```


---

### Post by The Cog on 2022-05-02
If you show the ruleset again, does it show any packet count against the nat rule?
Could you be using tcp? Try adding a tcp rule like the udp one.
Try "host -v google.com" and see where your reply comes from.
Use tcpdump to view the actual packets on the wire (change your interface name to suite):
```
sudo tcpdump -nntl -i eth0
```

---

### Post by sulfurman on 2022-05-02
I think i solved!
just listed /etc/resolv.conf and found this:

nameserver 127.0.0.53
options edns0 trust-ad
search station
:o

I commented these three lines and added opendns nameservers ip:
#nameserver 127.0.0.53
#options edns0 trust-ad
#search station
nameserver 208.67.220.220
nameserver 208.67.222.222

et voilà!
Now it's ok.

I think that DHCP overwrited  /etc/resolv.conf.

---

