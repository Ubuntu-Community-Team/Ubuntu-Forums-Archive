---
title: "How to configure UFW to allow Samba to talk to network NAS"
date: 2011-03-12
forum: New to Ubuntu
---

### Post by jaycee23 on 2011-03-12
I'm sure this is really simple but how do I configure my standard firewall using UFW to allow samba to communicate with my network hard drive.

If I turn off the firewall the network works just fine.

Sorry for such a dumb question but I just can't work it out.

Many thanks

---

### Post by Paqman on 2011-03-12
From the look of it, getting the Samba client to talk through ufw requires editing a config file:

According to [this bug]("https://bugs.launchpad.net/ubuntu/+source/ufw/+bug/360975") you need to do the following:

Hit Alt-F2 and enter:
```
gksu gedit /etc/default/ufw
```

then add:
```

nf_conntrack_pptp
nf_conntrack_netbios_ns

``` 
to IPT_MODULES

---

### Post by jaycee23 on 2011-03-12
I will try this when I get back home. Looks like it wasn't as simple as I thought. 

No wonder I couldn't get it to work! Thought I was being a bit dense.

---

### Post by coffeecat on 2011-03-12
> **Paqman said:**
> According to [this bug]("https://bugs.launchpad.net/ubuntu/+source/ufw/+bug/360975") you need to do the following:

Thanks for posting that link. I think it's disgraceful that after nearly two years that bug has not been dealt with, or another way found of getting ufw to play nicely with samba shares. 

In Maverick I found that if you install gufw and add the preconfigured inbound and outbound rules for samba, then samba was still blocked! I had to allow all traffic in my local network IP range to get samba past the firewall. Ridiculous. That looks a much better fix. Thanks again.

---

### Post by Paqman on 2011-03-12
> **coffeecat said:**
> 
In Maverick I found that if you install gufw and add the preconfigured inbound and outbound rules for samba, then samba was still blocked!

I believe that's because the Samba profile is designed for a Samba server, not a Samba client.

But yes, not really good enough at all.

---

### Post by ratcheer on 2011-05-28
I have been fighting this problem for three days. I had finally been forced to turn off ufw. Then I started searching for how to fix the combination of ufw and Samba server when I found this thread.

Note that the bug has been open for *two years*! Bleh!

Tim

---

### Post by Karti on 2011-08-03
Many thanks for this post. I thought it was just me. :)

Regards

K
:)

---

