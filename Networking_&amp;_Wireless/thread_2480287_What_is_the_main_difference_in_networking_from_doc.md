---
title: "What is the main difference in networking from docker and VM ubuntu jammy"
date: 2022-10-24
forum: Networking &amp; Wireless
---

### Post by wbgibby on 2022-10-24
Have a selenium hello world type project. This project just does a login to a website that has redirects and identity management system. 
When I run it in an ubuntu virtual machine it works fine. 
When I run it in docker I get the html from the identity management system but nothing from the actual website that I want use selenium on.
I see now error message but in pcap network capture logs I can see the docker container prematurely sending fin packets.

The website is java based sitting on tomcat server.

Anybody run into this issue?

---

