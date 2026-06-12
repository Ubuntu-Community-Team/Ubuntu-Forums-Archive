---
title: "cannot get internet-access"
date: 2005-08-21
forum: Networking &amp; Wireless
---

### Post by philippjosefrichard on 2005-08-21
I am using Ubuntu 5.04
ISDN-Modem Tango1000 at /dev/ttyS1

I made the internet-Access like I did with Mandrake and Fedora-Core.
But when trying to get internte-access the following ERROR comes:

Aug 18 17:00:57 zentrale pppd[24705]: The remote system is required to authenticate itself
 Aug 18 17:00:57 zentrale pppd[24705]: but I couldn't find any suitable secret (password) for it to use to do so.
 Aug 18 17:00:57 zentrale pppd[24705]: (None of the available passwords would let it use an IP address.)

When I enter for testing purpose my handy number  the handy will ring when I try to get internet access. That means, up to here the system seems to be OK.
After testing I changed back to the provider telefone number, obviasly :-)

When I try to get internet access the green LED of then modem signalize online status OK. BUT, ONLY for short! Than the connection stops with the mentioned Error message.

Is this problem due to a firewall problem? Where can I turn of firewall in ubuntu?
The problem is an authifications problem. How can I deal with that subject in Ubuntu?

Thank you for hints.
philipp

---

### Post by jasmuz on 2005-08-21
Open a terminal, type sudo pppconfig and create a connection.....after you are done, type pon to connect and poff to disconnect....if you get any errors please post.

---

### Post by philippjosefrichard on 2005-08-21
Thanks, meanwile I found the solution, like you told in 
 [http://www.ubuntuguide.org/#skype](http://www.ubuntuguide.org/#skype)
 

 Q: How to configure dialup connections?
 Read General Notes
 To configure dialup 
 sudo pppconfig
 To connect dialup 
 sudo pon provider_name
 To disconnect dialup 
 sudo poff

Ubuntu is getting sympatic :-)

Thanks
philipp

---

