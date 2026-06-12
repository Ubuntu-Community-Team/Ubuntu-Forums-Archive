---
title: "Internet"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by rizon on 2009-02-09
Hello, I am very new to Ubuntu. Everything seemed to be installed fine, I am using wireless internet. The only problem I really seem to be having is that firefox doesn't seem to be working right. I get 100% connectivity to my router and GAIM works fine, but when I open up firefox and try to go to google or some other website, either it will work fine, or it will go really slow, or the page won't load at all. Does anyone know what I can do to fix this? Any help would be appreciated. Thank you.

---

### Post by pmooney78 on 2009-02-09
Can you try connecting to the Internet via a wired connection and see whether the problem still occurs? It would help to narrow down the source of the problem ...

---

### Post by benhur99ph on 2009-02-09
Have you tried using other internet browsers? Install another one like Opera and see if the problem persists.

---

### Post by bgates on 2009-02-10
In FireFox address bar, type about:config.  Click the button promising to be careful.  In the filter box, type ipv6 

It should bring up a configuration network.dns.disableIPv6

If that is set to false, double click to set true.  Restart browser and see if that helps.

---

