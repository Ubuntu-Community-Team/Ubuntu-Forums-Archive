---
title: "firefox problem in lucid"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by grobar87 on 2010-05-05
When i run firefox in lucid,it freezing for 10 seconds and then open page.I did fresh install not update.Any idea?
thanks.

---

### Post by GSF1200S on 2010-05-05
> **grobar87 said:**
> When i run firefox in lucid,it freezing for 10 seconds and then open page.I did fresh install not update.Any idea?
thanks.

Do you mean the application itself is taking 10 seconds to load, it freezes for 10 seconds after you load it not allowing you to control it at all, or that it takes 10 seconds to load a webpage? If its the last one, try this:

Type about:config in the address bar, click the "I promise ill be careful" button, and type:
```
ipv
```
in the filter bar. Make sure that:
```
network.dns.disableIPV6
```
is set with a value of true. If not, right click and select 'Toggle'

---

### Post by grobar87 on 2010-05-05
> **GSF1200S said:**
> Do you mean the application itself is taking 10 seconds to load, it freezes for 10 seconds after you load it not allowing you to control it at all, or that it takes 10 seconds to load a webpage? If its the last one, try this:

Type about:config in the address bar, click the "I promise ill be careful" button, and type:
```
ipv
```in the filter bar. Make sure that:
```
network.dns.disableIPV6
```is set with a value of true. If not, right click and select 'Toggle'
 
Can you tell me more scpecific how to do this...i type config,but noting happens,
thanks for help btw.

---

### Post by grobar87 on 2010-05-05
And...firefox starts normal but when i try to open a page it takes about 10 seconds to load...

---

### Post by natravis on 2010-05-05
> **grobar87 said:**
> Can you tell me more scpecific how to do this...i type config,but noting happens,
thanks for help btw.

He stated correctly that you need to type ```
about:config
``` to access the configuration tweaking area of firefox.

---

### Post by GSF1200S on 2010-05-05
> **grobar87 said:**
> Can you tell me more scpecific how to do this...i type config,but noting happens,
thanks for help btw.

Open Firefox. Once open, look to the top where the website address is-
for example, [www.google.com](www.google.com) and highlight whatever web address is there. Then, type:
```
about:config
```
and hit enter. Afterwords, it will tell you that you are accessing important stuff, and you have to click a button right in the middle of the screen saying "Ill be careful, I promise!" Then, go to the filter box and type:
```
Ipv6
```
Ensure that network.dns.disableIpv6 has a value of 'True.' Attached is a screenshot showing you what I mean.

---

### Post by grobar87 on 2010-05-05
Thanks a lottt!!! That's fix the problem! :p

---

