---
title: "System crashed sometimes... !? SKB Bug?"
date: 2007-12-14
forum: Networking &amp; Wireless
---

### Post by Chessalex on 2007-12-14
Hi, my system crashed sometimes... it hangs up i doesnt react any more. 
My Configuration: AMD Athlon 3500+, ATI Radeon x850 (installed ATI drivers with envy), MSI K8T Neo2-f (no extra drives) and Linksys WMP54G Wlan card (i installed no drivers - it worked fine after install). i'm using ubuntu 7.10

I checked my ram for 11 hours in Memtest86 - no errors. But i found the following information in my kern.log.0 (dont know if its the same in the english version [perhaps core.log.0??])

> 

Dec 12 21:23:31 alex-desktop kernel: [ 4920.332000] SKB BUG: Invalid truesize (560) len=1396, sizeof(sk_buff)=176
Dec 12 21:23:31 alex-desktop kernel: [ 4920.424000] SKB BUG: Invalid truesize (560) len=1396, sizeof(sk_buff)=176
Dec 12 21:23:31 alex-desktop kernel: [ 4920.444000] SKB BUG: Invalid truesize (560) len=1396, sizeof(sk_buff)=176
Dec 12 21:23:31 alex-desktop kernel: [ 4920.480000] SKB BUG: Invalid truesize (560) len=1396, sizeof(sk_buff)=176
Dec 12 21:23:31 alex-desktop kernel: [ 4920.508000] SKB BUG: Invalid truesize (560) len=1396, sizeof(sk_buff)=176
Dec 12 21:23:31 alex-desktop kernel: [ 4920.536000] SKB BUG: Invalid truesize (560) len=1396, sizeof(sk_buff)=176
Dec 12 21:23:31 alex-desktop kernel: [ 4920.552000] SKB BUG: Invalid truesize (560) len=1396, sizeof(sk_buff)=176
Dec 12 21:23:31 alex-desktop kernel: [ 4921.088000] SKB BUG: Invalid truesize (560) len=1396, sizeof(sk_buff)=176
Dec 12 21:23:31 alex-desktop kernel: [ 4921.088000] SKB BUG: Invalid truesize (560) len=1396, sizeof(sk_buff)=176
Dec 12 21:23:32 alex-desktop kernel: [ 4921.176000] SKB BUG: Invalid truesize (560) len=1396, sizeof(sk_buff)=176
Dec 12 21:23:32 alex-desktop kernel: [ 4921.284000] SKB BUG: Invalid truesize (560) len=1396, sizeof(sk_buff)=176
Dec 12 21:23:32 alex-desktop kernel: [ 4921.488000] SKB BUG: Invalid truesize (560) len=1396, sizeof(sk_buff)=176
Dec 12 21:23:32 alex-desktop kernel: [ 4921.488000] SKB BUG: Invalid truesize (560) len=1396, sizeof(sk_buff)=176
Dec 12 21:23:32 alex-desktop kernel: [ 4921.688000] SKB BUG: Invalid truesize (560) len=1396, sizeof(sk_buff)=176




this error appears a few thousand times!!!

has s.b. a solution for me??

greetings

---

