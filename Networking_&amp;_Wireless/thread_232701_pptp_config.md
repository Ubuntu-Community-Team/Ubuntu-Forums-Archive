---
title: "pptp config"
date: 2006-08-09
forum: Networking &amp; Wireless
---

### Post by Robm on 2006-08-09
I am having difficulty setting up my pptp on vers 6.06, my system tels me that pptp-linux is installed however when giving the following command I get this response.

'sudo apt-get install pptpconfig'
Reading package list...Done
Building dependency tree...Done
E: couldn't find package pptpconfig.

I would be greatfull for anyone who is able to help a complete dumby with some step by step instructions. Thanks  Rob.

---

### Post by ohgod on 2006-08-09
The pptpconfig package is not in any of the normal Ubuntu repositories.  So, you'll need to add another repository for apt to search. Edit your /etc/apt/sources.list file and add the following line:

deb [http://quozl.netrek.org/pptp/pptpconfig](http://quozl.netrek.org/pptp/pptpconfig) ./

Then run 'sudo apt-get install pptpconfig' again and it should work.

---

