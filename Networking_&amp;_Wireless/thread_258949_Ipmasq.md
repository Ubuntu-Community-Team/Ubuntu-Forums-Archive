---
title: "Ipmasq"
date: 2006-09-16
forum: Networking &amp; Wireless
---

### Post by bastupungen on 2006-09-16
Hello friends!
I have a question about ipmasq that i use. The problem is that ipmasq stops working after a while. And a /etc/init.d/ipmasq restart seems to do the trick, for a while!

I did some research and found this site:
[http://www.ecst.csuchico.edu/~dranch/LINUX/ipmasq/c-html/masq-stops-working.html](http://www.ecst.csuchico.edu/~dranch/LINUX/ipmasq/c-html/masq-stops-working.html)

If you read it it says something that there is a problem with IPAUTOFW in the kernel. And that I should use IPPORTFW instead

"I bet you are using IPAUTOFW and/or you have it compiled into the kernel huh?? This is a known problem with IPAUTOFW. It is recommend to NOT even configure IPAUTOFW into the Linux kernel and use IPPORTFW option instead"

What does that really mean? I look at the other site that this site was referring to but couldn't really grasp what they were talking about.

I asked a question about ipmasq before on the forum. He then mentioned that i should use 
""#Enable packet forwarding
net.ipv4.ip_forward = 1""
instead.

Will the problem about internet sharing stops working be gone with this option above? and how do i use this in conjunction with firestarter? I could also point out that i use the dnsmasq as an dhcp server, which work fine!

---

