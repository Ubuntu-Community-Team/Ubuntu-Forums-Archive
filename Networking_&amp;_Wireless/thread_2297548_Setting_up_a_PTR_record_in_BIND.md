---
title: "Setting up a PTR record in BIND"
date: 2015-10-04
forum: Networking &amp; Wireless
---

### Post by papakota on 2015-10-04
Hello!
                            I run Postfix and I need my server's public IP address to be resolving to mail.mysite.com
                            I know that we have a PTR record for that AKA rDNS.
                            It's all nice, but something confuses me  here. I know that there's a way (somewhat complicated though) to set up a  PTR record in BIND. I think there' s a separate file for that etc. But  that's not my question here. I know that some people apply to their ISP  so that the ISP would set up the correct hostname for the IP that it's  lending to its customer. So that some picky SMTP servers out there will  accept the mail that's being sent to them. 
                            My question is:
                            What's the right way to do it and what's the  difference between setting up a PTR in BIND configuration yourself and  asking your ISP to do it for you. To me it sounds like a contradiction.

---

### Post by SeijiSensei on 2015-10-05
Only your ISP can create reverse DNS entries unless you have "[delegation]("https://www.ietf.org/rfc/rfc2317.txt")" set up which is pretty rare.  The ISP is authoritative for the in-addr.arpa subdomain(s) covering its addresses.

---

### Post by papakota on 2015-10-06
Thanks for your reply!
I used to have an issue with sending e-mail to certain SMTP servers. That's why I raised the topic here. I was thinking of asking my ISP, but strangely enough after me setting up BIND9 the RIGHT way, those SMTP servers have become nice to me. I even cancelled my request for the PTR, as a matter of fact.

---

