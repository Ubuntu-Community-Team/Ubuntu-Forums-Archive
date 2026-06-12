---
title: "What is the purpose of Netplan?"
date: 2018-05-17
forum: Networking &amp; Wireless
---

### Post by espressobeanie on 2018-05-17
So I crawled out from under my rock today by installing Ubuntu 18.04 and I see that /etc/network/interfaces has been replaced by something called "Netplan". I fail to see how Netplan makes anything better. Is there a simple way to gut Netplan from my Ubuntu install and just stick with "what I know best"?

---

### Post by chili555 on 2018-05-17
It can, with difficulty, be done. These are the steps:

# Install ifupdown with sudo apt install ifupdown
# Purge netplan with sudo apt purge netplan
# Configure /etc/network/interfaces and/or /etc/network/interfaces.d accordingly to your needs (man 5 interfaces can be of some help).
# Restart the networking service with sudo systemctl restart networking; systemctl status networking or sudo /etc/init.d/networking restart; /etc/init.d/networking status

But why? netplan is the way of the future and, eventually, will subsume /etc/network/interfaces entirely. Why not learn and use it now?

Is this a server or a desktop installation? If a desktop, I'd suggest setting your configurations in Network Manager. If a server, it's really not that difficult to set up netplan.

---

### Post by QIII on 2018-05-17
I miss 16 bit operating systems.  Alas, time has moved on.

The Red Hat family is also moving away from /etc/network/interfaces.  Change is inevitable.  Nothing progesses if it stays the same.

I am old enough to remember when *nix user info and home were located in /usr.  /etc was where stuff went when nobody was sure where it should go.  Things have changed since I started with all of this stuff in the 70s.

---

### Post by TheFu on 2018-05-17
> **espressobeanie said:**
> So I crawled out from under my rock today by installing Ubuntu 18.04 and I see that /etc/network/interfaces has been replaced by something called "Netplan". I fail to see how Netplan makes anything better. Is there a simple way to gut Netplan from my Ubuntu install and just stick with "what I know best"?

I feel ya.  I'm less unhappy with netplan than some other changes the last few releases.
The netplan project has tried to answer your questions: [https://netplan.io/faq](https://netplan.io/faq)
Why?
> Using netplan gives a central location to describe simple to complex networking configurations that function from Desktop to Server and from Cloud to IoT. Specifically, for systems with networkd, this relieves the user from having to configure up to three different files per device or configuration.

When I read that, it seems netplan was an attempt to fix the networkd problem.

How to go back to ifupdown?   [https://netplan.io/faq#how-to-go-back-to-ifupdown](https://netplan.io/faq#how-to-go-back-to-ifupdown)

I've seen a few people in these forums having issues that netplan isn't ready to solve, at least that is how it appears.  Mainly  around bridge setups.

I haven't moved any of my systems to 18.04 at this point. Netplan is part of the issues I'm not prepared to tackle.

---

### Post by QIII on 2018-05-17
Sigh.  I'm going to have to get a better handle on it all because I will run into it with my clients.

C'est la Vie!

---

### Post by tburger60 on 2018-05-17
I see I'm not the only old grey-beard sot to immediately run into this same problem.  Seems to me if we're going to replace something that works pretty well and is well understood with something completely new that we could at least provide the same or equivalent functionality.

After spending quite a while this morning researching a similar problem with iptables it appears that the solution is to embrace the "uncomplicated" complication of using the "uncomplicated firewall" instead of the (again well known and understood) iptables. Then enable UFW so it starts at boot; this was done previously with a pre-up command in the interfaces file.

---

### Post by The Cog on 2018-05-17
Ha! Once you have got your head around netplan, you may want to look at nftables. Here are my firewall rules :
```
~$ sudo nft list ruleset
table inet FILTER {
	chain INPUT {
		type filter hook input priority 1; policy drop;
		ct state established,related accept
		ct state invalid drop
		iif "lo" accept
		icmpv6 type { echo-request, nd-router-advert, nd-neighbor-solicit, nd-neighbor-advert } accept
		ip saddr 192.168.0.0/24 accept
		tcp dport 6881 accept
		udp dport 6881 accept
		tcp flags { syn } counter packets 0 bytes 0 reject
	}
}
```
Change is the only constant, as they say.

---

### Post by QIII on 2018-05-17
The gazelle that does not run is a meal for lions.

---

### Post by tburger60 on 2018-05-17
Thanks for that - I will certainly look into nftables.

---

### Post by chili555 on 2018-05-17
With all due respect for my colleagues, few of you have longer, whiter beards than old Chili. I have seen a lot of things change over the many years that I've run Linux. Usually, the choice is to learn it now or learn it later. We can only put off change for so long until it is simply no longer supported, it's a security flaw and/or there is no-one left on the forums that even remembers it.

Not many of us remember how to connect to an 802.11b WEP network purely by command line and I don't have wooden wheels on my sleek silver BMW.

End rant.

---

### Post by espressobeanie on 2018-06-01
> **QIII said:**
> Nothing progesses if it stays the same.

But all your scripts break


> **chili555 said:**
> Not many of us remember how to connect to an 802.11b WEP network purely by command line and I don't have wooden wheels on my sleek silver BMW.

End rant.

Chili, wouldn't connecting to an 802.11b network be the same as connecting to an 802.11g/n/ac network since they run from the same iwconfig or nmtui command? Also, wooden wheels will become the new norm when fashionistas run out of new ideas. I mean, even Hollywood recycles the same garbage in their scripts when they run out of good ideas.

---

### Post by chili555 on 2018-06-01
> Chili, wouldn't connecting to an 802.11b network be the same as connecting to an 802.11g/n/ac network Sure. But back in the day, we didn't have any Network Manager and had to connect by editing an /etc file or else entirely by command line. When Network Manager came along, it was buggy and derided by most and with almost the same language as netplan is today!

In Linux, the only constant is change!

---

### Post by feychart on 2018-10-18
> **chili555 said:**
> With all due respect for my colleagues, few of you have longer, whiter beards than old Chili. I have seen a lot of things change over the many years that I've run Linux. Usually, the choice is to learn it now or learn it later. We can only put off change for so long until it is simply no longer supported, it's a security flaw and/or there is no-one left on the forums that even remembers it.

Not many of us remember how to connect to an 802.11b WEP network purely by command line and I don't have wooden wheels on my sleek silver BMW.

End rant.


It's not false: upstart, unity, mir & ubuntu touch!...

"Oh, Ubuntu, you were my favorite Linux-based operating system"  -- me

---

### Post by karl-childers on 2018-10-20
> **chili555 said:**
>  netplan is the way of the future 

1) Sorry to revive an old post, but I haven't had time to address netplan until now.
2) I *really* want to upgrade to netplan so I can upgrade to 18.04 without too much hassle. I wish there was a way to do-release-upgrade and specify [COLOR=#111111][FONT=&amp]netcfg/do_not_use_netplan=true[/FONT][/COLOR]
3) Netplan doesn't seem mature enough yet: It doesn't seem to support wpa2 enterprise (especially wpa_supplicant hashed passwords in yaml files).  So I guess that means it is still in the future for me (not the present).

Please correct me if I am wrong.  I know a pittance as compared to chili555.

PS: It seems I *finally* get my head around ifupdown and iptables and kaboom!, the rug gets pulled out from under me!  That's life in the fast lane, I guess.

---

### Post by chili555 on 2018-10-20
> 3) Netplan doesn't seem mature enough yet: It doesn't seem to support wpa2 enterprise (especially wpa_supplicant hashed passwords in yaml files). So I guess that means it is still in the future for me (not the present).

Please correct me if I am wrong. Quite correct. Please see: [https://github.com/CanonicalLtd/netplan/pull/29](https://github.com/CanonicalLtd/netplan/pull/29) It is being addressed but not quite done yet.

I think your current options are to upgrade, remove netplan and all its yamls, install ifup/down and continue the method with which you are familiar: or, continue with, I assume 16.04 LTS and keep watching for EAP support. I have no information as to when this may arrive. 

On my own machine, I have installed 18.10 and a review of man netplan suggests that it isn't here yet.

---

### Post by desdan on 2018-10-25
Another non-fan of netplan here. Feels bloated to me. For those of us building machines as appliances it just feels unwieldy!  Also - read a post that said if you get the indentation wrong when you edit the settings then it won't work - this is both stupid and scary. This was built for a gui. Fooey.
So - coming back to edit this a bit...
I wish they had put this in place with transition in mind.  For a company whose product is based on Ubuntu changes like this can make life difficult. We must change working code. Ok - so life moves on, but if they had simply given us a way to link /etc/network/interfaces to netplan for several stable releases then we would have time to gracefully slide over to netplan.  Instead we upgrade (because there are other important aspects of the new version(s)) and discover that something as basic as networking needs to be addresses and learned.  Because we use Ubuntu server we try to abstract the complexity in a web interface and switching to netplan is non-trivial. I estimate my cost to switch to be several thousand dollars ... that kinda hurts.  perhaps there's a package out there that will do interfaces -> netplan for you - if not there may be an opportunity there.  
It seems drastic to just remove netplan altogether.

---

### Post by uufor44400aa12 on 2018-11-03
Chiming in here to agree with everybody else in that the forcing of netplan into 18.04 was a mistake.  As was mentioned before, the fact that netplan .yaml breaks if indentation is wrong goes a long way to describe the maturity state of netplan.  Further, I haven't seen any concrete reasons for why this was forced upon users.  As in, I don't see the problem that needed this as a solution. 

If anything, the ability to decide between netplan and normal /etc/network/interfaces should have been part of the 18.04 install, instead of completely ripping it out.

---

### Post by karl-childers on 2018-11-07
> **chili555 said:**
> Quite correct. Please see: [https://github.com/CanonicalLtd/netplan/pull/29](https://github.com/CanonicalLtd/netplan/pull/29) It is being addressed but not quite done yet.

I think your current options are to upgrade, remove netplan and all its yamls, install ifup/down and continue the method with which you are familiar: or, continue with, I assume 16.04 LTS and keep watching for EAP support.

That's exactly what I did.  Thanks for the info.  
It also seems like a security hole if EAP is not implemented in netplan.  Otherwise, the AP password has to be in the yaml file (or somewhere) plain text.
 
> Insert editorial comment here critical of ubuntu rolling out netplan too soon

PS: I believe you should also disable netplan with grub in kernel args

/etc/default/grub:
```
GRUB_CMDLINE_LINUX="netcfg/do_not_use_netplan=true"
```

---

### Post by emerth on 2019-05-16
> **QIII said:**
> I miss 16 bit operating systems.  Alas, time has moved on.

The Red Hat family is also moving away from /etc/network/interfaces.  Change is inevitable.  Nothing progesses if it stays the same.

I am old enough to remember when *nix user info and home were located in /usr.  /etc was where stuff went when nobody was sure where it should go.  Things have changed since I started with all of this stuff in the 70s.

That's a very condescending response. Not all change is advance. Netplan has fewer abilities than the Olde System.

I am also old enough to remember when "*nix user info and home were located in /usr. /etc was where stuff went when nobody was sure where it should go."

However Netplan still cannot configure anything other than Ethernet AFAICT. I communicated with it's authors a year or so ago and their response to my inquiry about IP over Infiniband was: "What's Infiniband?". 

So Netplan really isn't an advance for everyone, and if you have nothing to contribute to solving the guy's problem perhaps you should not reply, yes?

---

### Post by chili555 on 2019-05-17
> Netplan still cannot configure anything other than Ethernet AFAICT.I disagree. Please see the many templates at /usr/share/doc/netplan/examples. I have helped several posters set up wireless with netplan at askubuntu.com. For example: [https://askubuntu.com/questions/1105069/how-to-enable-wireless-on-ubuntu-server-18-04-via-cli/1107570#1107570](https://askubuntu.com/questions/1105069/how-to-enable-wireless-on-ubuntu-server-18-04-via-cli/1107570#1107570)

---

### Post by TheFu on 2019-05-17
> **chili555 said:**
> Sure. But back in the day, we didn't have any Network Manager and had to connect by editing an /etc file or else entirely by command line. When Network Manager came along, it was buggy and derided by most and with almost the same language as netplan is today!

In Linux, the only constant is change!

I still purge nm-* from all my systems today.

On my laptop, I use wicd-curses to manage wifi connections when travelling. At home, it is wired ethernet and uses dhcp reservations.

I've avoided netplan completely, so far.
Got into a fight with resolvconf and systemd yesterday on a few boxes that had been working over 2 yrs.  Someone changed something somewhere and it wasn't me.  In the end, I just modified the /etc/resolv.conf file and did a **sudo chattr +i** on it.  I'd wasted 20 minutes trying to get either of those tools to work they way they claimed.  None did and my settings for dns-nameservers in the "interfaces" file was being ignored too.

Screw them all, {insert distasteful word}.

I've been working on my neck beard and long hair the last few months. Time for an updated govt ID. ;)

---

### Post by brs-support on 2019-08-09
> **TheFu said:**
> I feel ya. ... I've seen a few people in these forums having issues that netplan isn't ready to solve, at least that is how it appears.  Mainly  around bridge setups.
I haven't moved any of my systems to 18.04 at this point. Netplan is part of the issues I'm not prepared to tackle.



Netplan is exactly the reason I have stayed back from 18 in my dev work, and now I have a catch-22 driving me to use it, since a bug in 16 will never be fixed, and yet we have a bug in the very thing I need the most help with in 18.

Creating a working bridge to route a secondary nic. arggh!

With 18 you get netplan, and pieces of network manager, and pieces of the old "interfaces" file method we all learned before the turn of the century. What a mess!

They do not peacefully co-exist. If you try making a change by other means, netplan will probably have unexpected results at boot, and may well recreate some defaults and muck up the mix again, so it seems we have to use one or the other, but not not both, and certainly not all three.

My plan: Give netplan one more try, by using just netplan files and nothing from the other methods, but if I cannot create a working bridge in netplan, it's back to basics.

In my case, if creating a bridge in yaml and netplan has a bug, using the other methods is the only resolution.

---

### Post by Doug S on 2020-03-26
Does anyone know if netplan is being adopted by other debian based linux distributions? I only know if it being used by Ubuntu/Canonical.

So far, I have stayed with Ubuntu server 16.04, however its time to move on.
Myself, and as much as possible, I would prefer to use the same methods and tools for Ubuntu, Debian, and Raspbian.

I have had a test 20.04 server running for months now, with netplan removed and ifupdown installed.
I also have another 20.04 one running with netplan, but have yet to actually make a useful server out of it.

EDIT: Found a few related things: [[1]]("https://unix.stackexchange.com/questions/438233/netplan-in-debian")[[2]]("https://unix.stackexchange.com/questions/515314/will-netplan-io-be-used-in-debian-buster")[[3]]("https://unix.stackexchange.com/questions/546993/unable-to-find-netplan-directory-in-debian-10")

---

