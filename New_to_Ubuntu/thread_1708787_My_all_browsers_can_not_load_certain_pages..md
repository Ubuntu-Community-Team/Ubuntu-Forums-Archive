---
title: "My all browsers can not load certain pages."
date: 2011-03-17
forum: New to Ubuntu
---

### Post by amityadav9314 on 2011-03-17
hi
Recentally I have this weired problem, My all browser including firefox, chrome, opera cannot load certain pages like [www.facebook.com](www.facebook.com), [www.in.yahoo.com](www.in.yahoo.com) etc.
This started all sudden.
Can anyone tell me what might be the problem?

---

### Post by Thund3rstruck on 2011-03-17
> **amityadav9314 said:**
> hi
Recentally I have this weired problem, My all browser including firefox, chrome, opera cannot load certain pages like [www.facebook.com](www.facebook.com), [www.in.yahoo.com](www.in.yahoo.com) etc.
This started all sudden.
Can anyone tell me what might be the problem?

Could be a number of things. If this was windows then I'd say malware for sure. Check your hosts file (/etc/hosts) and be sure you don't have any entries there redirecting you. If that's clean then run a traceroute to these url's and see where the packets are being dropped. Your DNS server might have been poisoned or your cache could be stale.

---

### Post by mimor on 2011-03-17
> **amityadav9314 said:**
> hi
Recentally I have this weired problem, My all browser including firefox, chrome, opera cannot load certain pages like [www.facebook.com](www.facebook.com), [www.in.yahoo.com](www.in.yahoo.com) etc.
This started all sudden.
Can anyone tell me what might be the problem?

What error does it return?
Can you ping the pages?
Open terminal and type:
ping facebook.com
ping yahoo.com

---

### Post by amityadav9314 on 2011-03-17
> **mimor said:**
> What error does it return?
Can you ping the pages?
Open terminal and type:
ping facebook.com
ping yahoo.com

Yes I can Ping these pages and i am getting the reply as well.
Well the main problem is that sometime the pages get loaded and sometimes not.

---

### Post by amityadav9314 on 2011-03-17
> **Thund3rstruck said:**
> Could be a number of things. If this was windows then I'd say malware for sure. Check your hosts file (/etc/hosts) and be sure you don't have any entries there redirecting you. If that's clean then run a traceroute to these url's and see where the packets are being dropped. Your DNS server might have been poisoned or your cache could be stale.

No I am using ubuntu 10.10 not windows.
There is no such problem in windows.
About facebook, it get load sometime while sometime not, after sometimes it shows time out.
But about yahoo, the page does not load at all in chrome, firefox, but get loaded in opera.

---

### Post by mimor on 2011-03-17
So the screen stays emtpy/white? 
Or do you get an error?
Is the 'loading' cursor still displayed?

---

### Post by amityadav9314 on 2011-03-18
> **mimor said:**
> So the screen stays emtpy/white? 
Or do you get an error?
Is the 'loading' cursor still displayed?

Sometime it shows an internal error, saying the request timed out and sometime other error.
Untill then the loading cursor keep on showing that the page is loading.

---

### Post by mimor on 2011-03-18
How are you connected to the internet.
Is there a router or proxy in between your modem and your laptop?

---

### Post by cguy on 2011-03-18
I used to have the same problem on older versions of Ubuntu, but with other pages.

I reinstalled the OS as a solution.

---

