---
title: "How to revert Firefox to its previous version"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by r3cht3r on 2009-06-15
[FONT=Arial]Right after I installed Firefox its current version, I seem [/FONT]can't access sites I regularly visits. I dunno if its something to do with the browser but I am certain that this started when Firefox updated. Now, it always says "Page Load Error. Network Timeout. The server at [www.site.com]("http://www.site.com") is taking too long to respond." 

It would be much appreciated if anybody can point out to me how to revert it to its previous version, then I'll try if the problem still persists. Thank you.

---

### Post by Celauran on 2009-06-15
Are you sure it's Firefox and not the network? Can you ping out?

---

### Post by prvteprts on 2009-06-15
Before reverting to the previous version, why don't you try completely uninstalling and reinstalling Firefox?

---

### Post by superprash2003 on 2009-06-15
its probably your network.. 2 things you could try
1)use opendns servers - 208.67.222.222 and 208.67.220.220 [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)
2)try changing MTU values - [http://www.prash-babu.com/2008/06/how-to-change-mtu-values-in-linux.html](http://www.prash-babu.com/2008/06/how-to-change-mtu-values-in-linux.html)

---

### Post by r3cht3r on 2009-06-18
What happens if you disable ping from performing its regular commands, does your network suffers too? Coz I've disabled it by choice without knowing the consequences (stupid me.:() thinking that its the same as blocking icmp parameters. Please correct me if I am wrong.

---

### Post by LewRockwell on 2009-06-18
> **r3cht3r said:**
> What happens if you disable ping from performing its regular commands, does your network suffers too? Coz I've disabled it by choice without knowing the consequences (stupid me.:() thinking that its the same as blocking icmp parameters. Please correct me if I am wrong.

that selection is just related to pings coming INTO your machine(a stealth machine will totally ignore all incoming pings)

---

