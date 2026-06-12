---
title: "Nessus Issues"
date: 2007-01-19
forum: Networking &amp; Wireless
---

### Post by $ark on 2007-01-19
Just a question.

Has anyone been experiencing issues with Nessus on Ubuntu and or Kubuntu?

I ask this question for the following reasons. 

I am a network security consultant. I perform Penetration Tests, and Vulnerability Assessments. I run Kubuntu/Ubuntu on my work laptops for the no head aches it provides. For my Pentesting machines I run Gentoo Linux, and FreeBSD. 

My problem occurred when I was at a clients office and ran a quick Nessus scan over lunch on my Ubuntu laptop. I wanted a quick look at potential vulnerabilities and machines on the network before diving in.

When the scan was done I started to look into the data I noticed some issues with Unix RPC. Nessus was telling me that the machines were Unix and what services were running, however no vulnerabilities where found. From my experience working with this version of Unix and the services running I knew that they had SunRPC vulnerabilities. I did some manual verifications and indeed these machines were vulnerable. 

Concerned that my first scan did not pick up these old vulnerabilities (and yes RPC checkes were enabled). I re-ran the scan from my FreeBSD Pen testing machine with the same configuration. These vulnerabilities were now found. 

This comes to my questions, is this a fluke or are other people running into issues with Nessus and Ubuntu. I do not rely solely on automated tools for vulnerability detection, however Nessus is a trusted software solution for quick remedial checks 

I am running Nessus 3.0.5 on all my machines in this post. I installed them from the Nessus Web site. For Ubuntu I used the Debian package supplied by Nessus. Any thoughts or similar problems would be appreciated. 


Thanks

---

