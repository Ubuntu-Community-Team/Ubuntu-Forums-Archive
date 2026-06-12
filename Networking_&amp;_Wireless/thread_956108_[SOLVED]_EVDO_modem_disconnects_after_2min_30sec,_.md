---
title: "[SOLVED] EVDO modem disconnects after 2min 30sec, help."
date: 2008-10-22
forum: Networking &amp; Wireless
---

### Post by HarrisonBP on 2008-10-22
I am using an LG phone with Verizon as an EVDO modem.  Gnome PPP automatically disconnects after 2min 30sec.  This is really annoying as I have to Ctrl+tab to Gnome PPP every 2.5 min, and I cannot download anything that takes longer than 2.5 min.  

Phone works fine as modem on Windows.  

I have used almost every setting I can find through GUI.  It's now time to get some help.

Thanks

P.S. I'm using Hardy Heron.

---

### Post by HarrisonBP on 2008-10-23
Same happens with KPPP

---

### Post by HarrisonBP on 2008-10-23
Can anyone help?

---

### Post by HarrisonBP on 2008-10-24
So many views, so few posts...  BUMP!

---

### Post by ModelM on 2008-10-25
I think this might help:

In the file:```
/etc/ppp/options
```change the line```
lcp-echo-failure 4
```to```
#lcp-echo-failure 4
```

---

### Post by HarrisonBP on 2008-10-26
Thanks, I think that worked.  I am only a few months into linux, can you tell me how that worked?

---

### Post by ModelM on 2008-10-26
The PPP protocol by default periodically checks to make sure the other modem can "hear" it by sending a special packet - an LCP echo request - every so often. If nothing is received in response, it is assumed that the link has been broken & PPP disconnects. 

On some PPP links, yours for instance, this doesn't work properly. Not all remote modems will respond to the LCP echo request. We simply told PPP not to worry if these LCP echo requests are not answered.

---

### Post by HarrisonBP on 2008-10-26
cool, thanks again.

---

### Post by nishanthps on 2010-05-12
ModelM you are my saviour,
it worked like a charm

---

