---
title: "Want IPV6 on home desktop"
date: 2016-01-24
forum: Networking &amp; Wireless
---

### Post by jlrubin on 2016-01-24
My internet service provider is Time Warner Cable in New York City. They provide native IPV6. It immediately worked perfectly on my home network, including computers running Windows 7 Professional and Apple OS X.

I just installed ubuntu-14.04.3-desktop-i386.iso (LTS) alongside Windows 7 pro. IPV4 works fine. IPV6 does not.

How do I get dual stack support (IPV6 and IPV4) working in Ubuntu? I want IPV6 to take precedence.

Added 1/24/2016, 4:03 EDT
I have added some dumb questions. The answers might help me ask better questions.

Millions of people use TWC in cities with IPV6 support. Some of them must be trying to run IPV6 on Ubuntu. Where do those people hang out?

My Windows and OS X boxes are getting IPV4 and IPV6 addresses. I can see them in the router and in the clients. I understand DHCP in IPV4.
1. How is Ubuntu supposed to get an IPV6 address?
2. What is required for that to work?
3. What should I be reading?

Edited 1/24/2016 10:42 EDT
One symptom was that IPV6 address was assigned, but no default route.
Problem solved by using the GUI to change the IPV6 connection setting to "Automatic."
I would still like answers to the 3 questions above.

---

