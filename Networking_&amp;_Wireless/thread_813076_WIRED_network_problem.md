---
title: "WIRED network problem"
date: 2008-05-30
forum: Networking &amp; Wireless
---

### Post by flatlinecoder on 2008-05-30
Hi I new to ubuntu
I have just installed ubuntu 8.04 from a CD and that i burnt only 4 days ago. Everything works grand, expect my internet connection.

When I left click on the network icon it says
"Connect to a 802.1X protected wired network"

It then asks me for a
 -network name
 -EAP method
 -Phase2 Type
 -Identity
 -Password
 -anonymous Identity
 -client cert files
 -CA cert files
 -Private key password

I rang my ISP thinking maybe they had something to do with this protected setting and surprisingly enough I got to talk to some who had used ubuntu personally and he said that it might be something to do with my passwords or authorization settings on ubuntu. That he had tried it himself a while back and it worked fine.

I have been googling all day and been at bugs.lunchpad and found a bug report that seem like my problem here [https://bugs.launchpad.net/ubuntu/+bug/208646]("https://bugs.launchpad.net/ubuntu/+bug/208646")

It seems to be since the update to 8.04 the network thing has gone abit mad or something, from what I am reading around the web. If this problem is fixed how do I download or were can I download the patch for it, as I would have to download it on windows and move it onto my new ubuntu system after and I would be able to use the syn manger obviously.


Kind Regards
Ciaran Mc Cann

---

### Post by flatlinecoder on 2008-05-31
I have tried this command below.
```

ping -c 4 4.2.2.2
ping -c 4 ping.symantec.com

```

and it seem to be able to ping any address, but when I go to firefox it wont work. The ping only works when I setup the network by manual config and setup my ip and subnet and gateway

---

### Post by superprash2003 on 2008-05-31
ok.. leave it to manual config and setup DNS servers [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by coralfreya on 2008-12-14
> **superprash2003 said:**
> ok.. leave it to manual config and setup DNS servers [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)
**[COLOR=darkred]Thank you thank you thank you!!!![/COLOR]**

---

