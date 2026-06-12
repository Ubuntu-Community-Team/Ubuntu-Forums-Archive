---
title: "Is there a way to get a &quot;spoofed&quot; MAC address to PERSIST over reboots?"
date: 2010-10-01
forum: New to Ubuntu
---

### Post by mikodo on 2010-10-01
Hello everyone,

I am a causal user, so I'm not, too enlightened. Is there an easy way, short of changing out the network interface card, to have a "spoofed" MAC address persist over reboots? I use an ethernet wired connection to an ISP's provided modem, with no router.

It is not for anything immoral, illegal or malicious, that I ask.

Thank you,

Mike

---

### Post by mikodo on 2010-10-01
I can only find this [http://www.village-elder.com/blog/archives/6-How-to-spoof-your-MAC-address-under-Linux.html](http://www.village-elder.com/blog/archives/6-How-to-spoof-your-MAC-address-under-Linux.html) while doing a search.

I have no idea on how to follow his advice on how to make the change persistent between reboots by putting these commands in the file:

/etc/rc.local


```
ifdown eth0
 
  ifconfig eth0 hw ether 00:80:FF:FF:98:F5
 
  ifup eth0

```So, I guess I am "spoofed".

Oh well,

Thanks.

---

### Post by canthus13 on 2010-10-02
If your NIC is built into the motherboard, there may be a BIOS setting that you can set the MAC with.  Then you don't have to worry about OS-specific patching.

--Me

---

### Post by mikodo on 2010-10-02
> **canthus13 said:**
> If your NIC is built into the motherboard, there may be a BIOS setting that you can set the MAC with.  Then you don't have to worry about OS-specific patching.

--Me

Thanks for the reply canthus13. I had a go at your suggestion, saw on-line that in some motherboards, one can successfully change the MAC in the BIOS, that the software reads, unfortunately, I cannot. 

One valid suggestion tried,

Thank you.

---

### Post by mikodo on 2010-10-02
Thanks everyone,

When I temporarily spoof my MAC address, my ISP doesn't let me connect to the Internet with it. So, pursing this thread any further is useless, for the reason it was intended for. 

I was trying to get on a message board without them knowing who I was. I was going to re-register with different Email, dynamic IP, and MAC addresses. They use cookies to identify who is registering and I took that as a challenge, to see if I could circumvent their personal data collection, by using different addresses, for them to identify to. One cannot register with them, without allowing them to place 5 identifying cookies, on one's computer.

No joy, so the heck with them!  =;
Mike

---

