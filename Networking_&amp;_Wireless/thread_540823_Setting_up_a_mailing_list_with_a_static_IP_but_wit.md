---
title: "Setting up a mailing list with a static IP but without a domain"
date: 2007-09-02
forum: Networking &amp; Wireless
---

### Post by aneeshm on 2007-09-02
I'm attempting to set up a mailing list using GNU Mailman running on top of Apache2 and Exim4. The configuration was a bit tricky, but manageable. Neither Apache2 nor Exim4 are being used for anything else.

The problem I'm facing is that though I have a static IP address, I don't have a domain name.

In such a case, will it be possible to run a list? Can mail be sent to and from a static IP without a domain? And will an MTA run on such an address, or will it have problems? If, instead of [email]something@somedomain.com[/email], I type something@123.123.123.123, for instance, will it work?

Now, let me confess that I'm a complete newcomer to managing mail services, and I don't fully know how the underlying infrastructure works. So if my questions seem a bit amateurish, please forgive that. I'm reading Wikipedia's explanation of how it works right now, and I've understood the fundamentals, but not nearly well enough. That will probably take time and practice.

The purpose for setting up the list is for college work. I want to demo this as a proof-of-concept to the people at my college, for two lists - the Announce list, for announcements from the staff and faculty to the students, and the Discuss list, for discussions between the students. We already have a Linux server running, so it shouldn't be much of a problem to convince them to add a few more services, given the fact that one of the requirements is that the list be manageable and moderable by the staff concerned, and not just the network administrators. They're looking for a level of control over the Announce list which cannot be had with anything except a full-fledged mailing list software like Mailman.

---

### Post by colo on 2007-09-02
Email does work without DNS, yes.

You might want to get a free static DNS and MX entry at [www.dnynds.org](www.dnynds.org) though. Should make things easier to memorize.

---

