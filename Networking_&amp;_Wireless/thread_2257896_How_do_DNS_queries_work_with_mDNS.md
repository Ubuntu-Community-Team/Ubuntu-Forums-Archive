---
title: "How do DNS queries work with mDNS"
date: 2014-12-23
forum: Networking &amp; Wireless
---

### Post by dan148 on 2014-12-23
Normally when I connect to the internet its through my wireless router.  Entering in a website (example.com) in my browser typically starts with a DNS lookup followed by sending out the actual HTTP request, nothing new here.  However when I'm connected to an adhoc network things change.  I understand that adhoc networks use mDNS vs standard unicast DNS. When I try to visit a website in an adhoc network I instantly get 'unknown host'.  I open up wireshark I don't see any reference to the website I'm trying to pull up in the mDNS queries (or at least I don't think there is anything there, I'm still learning wireshark).  The only time websites appear to resolve is if i have an entry for it in /etc/hosts.

So my question is how are non .local TLD handled while I'm connected to a adhoc network?  Should there be any DNS/mDNS lookups when i try to visit example.com?  Is there anyway I could resolve all TLDs locally w/ a DNS server or proxy them to another device on my network?

---

