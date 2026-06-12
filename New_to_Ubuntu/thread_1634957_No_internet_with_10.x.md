---
title: "No internet with 10.x"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by laidback on 2010-12-01
I installed a copy of 10.04LTS but am unable to access the internet (WWW). I can ping, i.e. Google.com, and any other address I want, but I get no response in Firefox, just timed out, with either DHCP or manual settings.

So I also tried 10.10, just the same.

Now this is very worrying as I've been using Ubuntu since V6.x and have always thought it to be wonderful. So what's going wrong?

Strangely I tried Mint v9, which I believe to be based on Ubuntu 10.04LTS, and that works with no problem.

I've even tried the Live CDs on another older pc (different NIC), with the same result, v10.x gives no internet but v9.04 Live CD goes straight on!

So I don't think it's the NIC as they differ between the 2 PCs. It's not my connection as my regular v9.04 is fine, as is PCLinuxOS 2010 and my wife's Windows pc etc.

I'm lost...any suggestions.

Many thanks

Laidback

---

### Post by laidback on 2010-12-02
wojox has sent me the answer:-


In FF
1. Type about:config in the address bar, press Enter.
2. Find network.dns.disableIPv6 in the list.
3. Right-click -> Toggle to set value to True (i.e. disabled)
4. Restart Firefox and try again. 

Worked for DHCP connections although my manual connection still doesn't work.
I also tried it with the Live Cds, it works there too.

---

