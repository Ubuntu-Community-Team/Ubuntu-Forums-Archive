---
title: "Cannot mount Windows XP folder using server name"
date: 2006-10-21
forum: Networking &amp; Wireless
---

### Post by mike2357 on 2006-10-21
I cannot mount a Windows XP folder from Ubuntu using a Windows server name.  It works fine using a IP address, which is only a temporary solution since my computers get IP addresses using dhcp.

This works fine:
mount -t smbfs //192.168.1.100/SharedDocs /mnt/Directory_Name

This does not:
mount -t smbfs //WINDOWS_SERVER_NAME/SharedDocs /mnt/Directory_Name

I get the following error message:
Error connecting to 209.86.66.90 (Connection refused)
7861: Connection to WINDOWS_SERVER_NAME failed
SMB connection failed

The odd thing is the 209.86.66.90 is my ISP's IP address.  I was expecting my router's IP address.

Any ideas?  This used to work a few months ago, and quit working recently.

Thanks very much.

---

### Post by kidders on 2006-10-21
Hi there,

Something is telling your network that 209.86.66.90 is your Windoze server's IP address. Once you track down what it is, you should be able to educate it. You *could* use your /etc/hosts to override your network's DNS information, but since you mentioned that the correct IP is assigned dynamically, that wouldn't be terribly smart.

Quite often, your /etc/resolv.conf will tell you where the nameserver serving your Ubuntu box is. The problem is most likely on that device.

Hope that helps.

---

### Post by mike2357 on 2006-10-21
No luck -- I looked in /etc and all sub-directories and couldn't find a reference to 209.86.66.90.  Thanks very much for your advice; it's one more thing I can keep looking for.

---

### Post by kidders on 2006-10-21
Hey again,

Sorry for not making myself clear before ... the problem probably isn't your Ubuntu box, unless of course, you're running several DNS servers, or are using a dynamic DNS service, in which case you'd  probably already know how to solve this issue.

The most likely cause is that the DNS server you configured your Ubuntu box to use is explicitly instructing it to associate 209.86.66.90 with your Windoze server. In that case, assuming you're happy with Ubuntu's network configuration, it's doing exactly what it's supposed to :-) If I'm on the right track, you can verify, by pinging your Windows box from somewhere else on your LAN that's also using the same DNS service.

To correct the problem, you need to track down whatever is spreading lies about your network, and go from there.

**Edit:** I forgot to mention that, once you correct your problem, the changes may take some time to spread around your network, depending on your DNS server's TTL settings.

**Edit:** At least your problem does tell you *something* encouraging, which is that your samba is not accepting external connections :-) If it were, you may never even have run into this issue.

---

### Post by mike2357 on 2006-10-21
You are a very smart person.

Earthlink, my ISP, changed its DNS server error page routing.  I won't pretend to know what I'm talking about, but the following article discusses it:

[http://kb.earthlink.net/case.asp?article=187117]("http://kb.earthlink.net/case.asp?article=187117")

I never would have thought this error came from outside my computers or router, but such was the case.  Fortunately, they provide an opt-out service.

Thanks very much.  It goes without saying, but I never would have solved this one had you not pointed the finger at the DNS server.

---

### Post by kidders on 2006-10-21
> You are a very smart person.
Lol... do you mean "smart" as in clever, or "smart" as in smart-*a$$*?! Hehe.

Glad you solved your problem. I presume the solution (at a technical level) was that your ISP's DNS server no longer claims to know addresses for things it has never heard of. Does that sound right? Now that (presumably) it just shrugs its shoulders at requests for stuff that has to do with your private LAN, your Ubuntu box is free to try other ways of figuring out where your Windoze box is.

All the best.

---

### Post by mike2357 on 2006-10-21
There's quite a bit I won't fully understand, the least of which is when I booted my Ubuntu box into Windows (yes, it's a dual-boot machine), all of the computers recognized each other again.  Fortunately, once I switched the DNS server in /etc/resolv.conf, Ubuntu started working one more as well.  Thanks again for your help.

The best explanation I found came from Wikipedia:

"In August 2006 EarthLink teamed up with Yahoo and Barefruit to redirect web browser users accessing nonexistent domains to a page containing sponsored search results, ads, and a Yahoo search form. The DNS protocol requires that a query for a nonexistent domain must return the "NXDOMAIN" error response. Instead of this response, EarthLink's DNS servers return several IP addresses for the HTTP servers that implement their redirection service. While such redirection might be helpful to users of some web browsers, it breaks the functionality of many other internet applications, which assume that the DNS is implemented according to the standard specifications. EarthLink's redirection also prevents the user's web browser from detecting NXDOMAIN errors and handling them according to the user's preference.

Comments left in the official Earthlink blog announcing the feature [1] and news aggregators like Slashdot [2] have been overwhelmingly negative. In 2003, Verisign implemented a similar feature called Site Finder for all .com and .net domains. Verisign ultimately reversed the change after the ensuing controversy and under pressure from ICANN. While Site Finder affected all Internet users, Earthlink's redirection feature is only applicable to Earthlink ISP customers. In contrast with Verisign's policy of not mentioning the effect of Site Finder on non-HTTP-based services, EarthLink says it is trying to minimize the impact on such uses of DNS, which is impossible since a DNS query doesn't contain any information that can be used by the DNS server to determine whether the addresses obtained from the query will be used for HTTP or other traffic.

After about a month of complaints on the blog, EarthLink made available two DNS servers that it says are unaffected by the service and should properly return NXDOMAIN for all 'dead' domain names. [3] These must be manually configured on machines of customers who wish to use them. The company says it will not provide technical support for these alternate servers."

---

### Post by kidders on 2006-10-21
This may be helpful, to complete the picture for you ...

Network devices are capable of resolving hostnames in a number of ways, and may use several, in a predefined order, until they find a useful answer. To find *your* list, type **cat /etc/nsswitch.conf | grep -i ^hosts** Here's mine. It should be noted that this configuration is not necessarily appropriate for anyone else's PC.

```
# cat /etc/nsswitch.conf | grep -i ^hosts
hosts:          files dns mdns
```

This translates into the following, in order:
[LIST=1]
[*]Does /etc/hosts have the answer?
[*]How about the DNS nameserver specified in /etc/resolv.conf?
[*]Is the name registered in multicast DNS?
[/LIST]

Additional methods of resolving hostnames include NetBIOS lookups, often employed by Windoze boxes as a largely unnecessary (and often confusing) alternative to DNS.

In your case, your DNS server was lying about its knowlege of the internet, making the totally idiotic claim that it knew the private address of a computer on your LAN, which is impossible. This was done to cause web browsers to redirect you to an advertisement, whenever you mis-typed a hostname. Now, imagine *Samba* is making the request. A possible event sequence might go a little like this:

Q: Does /etc/hosts have an address for me to try?
A: No, it's dynamically assigned, so it won't have it.

Q: Does my ISP's DNS server know about it?
A: Yes it does, it's @ 209.86.66.9 (which is in fact a lie).

... As a result, the following _won't_ happen ...

Q: How about multicast DNS (sometimes called "Bonjour")?
A: No luck here.

Q: Could it be a NetBIOS name?
A: Yes ... it's at 192.168.1.100.

The changes your ISP made to its DNS service are illegal (in terms of the applicable international standard, not the law), and highly likely to foul up thousands of computers' DNS lookups, which rely on compliance with certain standards to function appropriately.

**Solution #1:** Reorganise the order of your name resolution in /etc/nsswitch.conf so "dns" is last, or even excluded altogether. (Not very good.)

However, the reason your Windows boxes knew how to find eachother was that NetBIOS lookups were probably prioritised ahead of DNS lookups. If you had tried to ping a name that wasn't registered with NetBIOS either, you'd have had the same problem.

**Solution #2:** Switch to a DNS server that won't lie to you. (Excellent.)

This was how *you* chose to fix your Ubuntu box, eliminating the problem altogether. You should do the same on your Windows boxes too.

All operating systems will be affected by this issue, since they all use virtually identical mechanisms for connecting hostnames to their IPs (and vice versa). With any luck, this explanation will clear up the bits you are a bit fuzzy on.

Happy Ubuntu-ing :-)

---

