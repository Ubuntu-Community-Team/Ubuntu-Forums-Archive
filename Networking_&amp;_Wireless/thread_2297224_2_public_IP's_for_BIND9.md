---
title: "2 public IP's for BIND9"
date: 2015-10-01
forum: Networking &amp; Wireless
---

### Post by papakota on 2015-10-01
Hello!

                            I wonder if it's really a MUST to have at  least 2 public IP's to successfully install and run BIND9 DNS server on  Ubuntu Linux.
                            Well, my ISP won't let me get 2 IP's. They  say that PPPoE that they use won't allow it. Therefore, I would be  needing two separate servers in two different locations, wouldn't I? 
                            The reason why I'm asking... See, my domain  name's registrar handles for free DNS lookups for my site. Actually,  their DNS service is pretty good (it's GoDaddy). 
                            Let me rephrase my question though... Is  there a sure way to bypass that 2 DNS server limitation? Let's say, I  could add as a secondary DNS server for my domain name my ISP's DNS  server' hostname or even Google's. Or it's gonna fail? 
                            Frankly, maybe I shouldn't even bother  running my own DNS in SOHO environment with just one site. But I kinda  wanted at least to try (out of curiosity, if you will...).

---

### Post by SeijiSensei on 2015-10-01
The Internet standard for DNS requires two servers, preferably geographically and topologically separated, to avoid outages.

If GoDaddy will host the DNS for you, either give it all to them, or have a GoDaddy server set up as a secondary to the primary you maintain.  I have no idea whether they offer a service like this.  I maintain my own DNS servers on Linode virtual machines in New Jersey and California.

---

### Post by papakota on 2015-10-02
Thanks for your reply! I would definitely ask GoDaddy, but let me here ask couple of questions nevertheless:
1) Other than pure curiosity on my part... Is there any real advantage to even bother with my own DNS server at home? I mean, right now seems that my site functions fine DNS-wise. As they say -- Don't fix what's not broken;
2) Why would registrars offer such a service, **especially for free**? Is it their regular practice? Or it's a GoDaddy's sort of unique selling proposition (USP) to attract customers?
3) My question still stands... how come GoDaddy's DNS free service solves a DNS propagation issue within minutes, whereas normally it takes about 24 hrs.? What kind of "magic" do they use?

---

### Post by SeijiSensei on 2015-10-02
Unless you expect to be changing your DNS entries routinely, I'd ship it all to GoDaddy.  I can't comment on their pricing or service policies since I refuse to have anything to do with them given the sexist nature of their advertising.

I use DirectNIC; they also have free hosting, I believe, but since I maintain my own servers I've never really checked.

Propagation depends on a number of things, most especially the time-to-live (TTL) parameters.  Also most email servers check the MX records for a domain pretty much every time they send a message there.  That's not true for normal A records though.

---

### Post by SeijiSensei on 2015-10-02
Unless you expect to be changing your DNS entries routinely, I'd ship it all to GoDaddy.  I can't comment on their pricing or service policies since I refuse to have anything to do with them given the sexist nature of their advertising.

I use DirectNIC; they also have free hosting, I believe, but since I maintain my own servers I've never really checked.

Propagation depends on a number of things, most especially the time-to-live (TTL) parameters.  Also most email servers check the MX records for a domain pretty much every time they send a message there.  That's not true for normal A records though.  Still, I had to make some changes to DNS for a client, and Google's servers saw the changes almost immediately.  We have been using a TTL of 86400 (one hour) though until things settle down.

---

### Post by papakota on 2015-10-02
Okay, thanks for your reply!

---

