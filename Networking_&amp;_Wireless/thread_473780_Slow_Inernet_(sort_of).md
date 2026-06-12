---
title: "Slow Inernet (sort of)"
date: 2007-06-14
forum: Networking &amp; Wireless
---

### Post by humphry on 2007-06-14
It's not that my internet is slow.  It's that whenever I try to load a web page, my browser (currently firefox) sits there with a blank screen for roughly 5-10 seconds before it loads.  Once it gets around to loading, it's very fast.  

The same happens with downloads.  It takes a while to get started, and then goes at 300 kbps or faster.  

The same happens with Update Manager.  For most (small) updates, I sit there waiting for it to think about it longer than it takes to download and install the updates.  

I dual boot with Windows, in which I also use firefox.  I've never had this problem in Windows, and I didn't notice this problem until Fiesty came out.  

I've already tried disabling IPv6, and that didn't help at all.  

Help?

---

### Post by stchman on 2007-06-14
> **humphry said:**
> It's not that my internet is slow.  It's that whenever I try to load a web page, my browser (currently firefox) sits there with a blank screen for roughly 5-10 seconds before it loads.  Once it gets around to loading, it's very fast.  

The same happens with downloads.  It takes a while to get started, and then goes at 300 kbps or faster.  

The same happens with Update Manager.  For most (small) updates, I sit there waiting for it to think about it longer than it takes to download and install the updates.  

I dual boot with Windows, in which I also use firefox.  I've never had this problem in Windows, and I didn't notice this problem until Fiesty came out.  

I've already tried disabling IPv6, and that didn't help at all.  

Help?

Follow my procedures here and your internet should speed up considerably.

[http://www.stchman.com/conf_host.html](http://www.stchman.com/conf_host.html)
[http://www.stchman.com/openDNS.html](http://www.stchman.com/openDNS.html)

This helped me a great deal.

Hope this helps.

---

### Post by humphry on 2007-06-14
I haven't tried either method yet (because I'm away from my laptop at the moment) but I'm not sure it will work.  I'm at college, and they have given me a static IP address and DNS settings.  If I change my IP, the college's routers won't recognize me.  

The other method seems to be about launching applications faster--that might be nice, but won't solve my  main problem.

---

### Post by stchman on 2007-06-14
> **humphry said:**
> I haven't tried either method yet (because I'm away from my laptop at the moment) but I'm not sure it will work.  I'm at college, and they have given me a static IP address and DNS settings.  If I change my IP, the college's routers won't recognize me.  

The other method seems to be about launching applications faster--that might be nice, but won't solve my  main problem.

Just use the first one.  You can still use the hosts configurations and then go to System--->Administration--->Netowrk and specify a static IP.  If you are using wireless then you cannot use network manager and static IP with either WEP or WPA encryption.

---

### Post by voxman69 on 2007-06-14
THANK YOU Stchman!!! This took care of the last annoying item on my list! The slow starts and mysterious pauses seems to be gone! :-)

---

### Post by stchman on 2007-06-14
> **voxman69 said:**
> THANK YOU Stchman!!! This took care of the last annoying item on my list! The slow starts and mysterious pauses seems to be gone! :-)

You are welcome.  I have traced it to a lot of ISPs have really cr@ppy DNSs.  That coupled with the hosts file being over kludged with junk really slows down the system.

---

### Post by lukew on 2007-06-20
Hay Stchman!

Item 1 worked a treat! Tthere was a variable wait on my WPA'd wifi but notw it is gone :)

Thank You so much!

Luke

---

