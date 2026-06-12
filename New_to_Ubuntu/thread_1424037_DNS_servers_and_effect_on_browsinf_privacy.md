---
title: "DNS servers and effect on browsinf privacy"
date: 2010-03-07
forum: New to Ubuntu
---

### Post by oingk on 2010-03-07
Hi 

I wanted to ask in regards to third-party DNS servers, like OpenDNS. Apparently, their advantage is that they are safer and faster. Is this true?   

Also I have another question: I know that my internet service provider can track my internet browsing, if they wish to. What if I use third-party DNS? Will my ISP still be able to track my browsing?    

Also, if I use 3rd-party DNS servers will this server be able to track my browsing?

Thanks

---

### Post by MechaMechanism on 2010-03-19
The fastest DNS servers will always be the ones that have the lowest overall latencies and fastest server response.  Generally these will be your ISP servers.  OpenDNS will most likely have a higher latency but faster hardware response to incoming packets.  However the latency will negate the faster hardware response.  Any DNS server can be configure to track their users.  Your ISP will always be able to track you because your on their network.  In short your ISP and any third party DNS can track you.

Best bet is to stay with your ISP DNS servers for lowest latency and fastest response.  I would not worry about tracking.  The only way around that is to encrypt your data stream and connect to an encrypted DNS sever but I personally think that is overboard.  Plus encryption still don't hide your whereabouts, for that you would also need something like TOR.  I hope this answers your questions. :)

---

### Post by ayenack on 2010-03-19
+1 On DNS server.

You can use TOR & Prioxy to make your browsing anonymous. Take a look at this.

[https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor)

It does slow your connection down though.

---

### Post by oingk on 2010-03-25
Thanks very much!

---

