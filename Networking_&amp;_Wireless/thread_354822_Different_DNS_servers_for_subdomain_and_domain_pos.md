---
title: "Different DNS servers for subdomain and domain possible?"
date: 2007-02-06
forum: Networking &amp; Wireless
---

### Post by thequestion on 2007-02-06
Hi a friend of mine have a domain and I now wonder if it is possible for me to get a subdomain of his lets say: thequestion.domain.com and to have this on my own dns server. I want to learn how bind works and thought this would be a great opportunity.

He have two dns servers one master and one slave for his top domain: domain.com and I have two computers here at home with public ip, so I wonder can I use those computers with bind to host thequestion.domain.com but not domain.com?

thanks!

---

### Post by koenn on 2007-02-06
yes - i think.
DNS knows the concept of "zones"' - a zone is a collection of hosts (names / addresses) that a DNS server is in charge of (has "authority" for). A zone is not necasarilly the same as a domain. Your subdomain could be a zone by itself, managed by your DNS server, while the parent domain minus your subdomain could be a zone of your friends DNS server(s). 
Or something along those lines - you'd need to read up on DNS a bit, either in DNS in general or in a good 'bind' howto /tutorial to work out the details and find out how to set it up.

---

### Post by bve on 2007-02-06
While I am by no means a Bind or DNS expert, I am fairly certain you are not going to be able to do exactly what you want.

First each domain has an SOA record or Start Of Authority - this record is managed by the Authoritive DNS server for the domain. In the example of your friend's domain this would be his master DNS server, ASFAK his slave simply requests an update from his master to maintain it's records.

You would have to become a slave to his master, and I don't think zone files created on your DNS server would be transfered to him.

You could set up a local DNS server on 1 of your machines to act as a DNS server for your local network, however with only 2 machines on your network this would probably be pointless for any purpose other than your stated desire for learning. Furthermore if your two machines are connected directly to the internet with publicly routable IP's then you don't have a local network so this won't work very well and is a bad idea. On the other hand if you are behind a router using NAT with private IP's then you could set it up with out risk of harm.

As mentioned previously, I am no expert, however I know proper DNS management requires a bit deeper knowledge than what you will get from an answer in a forum posting.

Read the man pages for bind or bind9 (man named) and if they don't lose you in a few lines, then go further by doing a lot of reading as it really is fairly involved and a solid understanding of DNS is a decent pre-requisit IMO.

---

