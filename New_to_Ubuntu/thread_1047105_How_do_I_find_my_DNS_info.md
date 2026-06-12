---
title: "How do I find my DNS info?"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by curiousnoob on 2009-01-22
I am trying to add a device (Nintendo Wii) to my Linksys WRT150N Wireless Router and am having trouble.  I believe I can fix it if I could find my Primary and Secondary DNS info.  I have never needed to do this on Ubuntu before. 
On Windows the command would be ipconfig/all.  What is it in Ubuntu?

---

### Post by stefangr1 on 2009-01-22
This depends on your internet provider. You should google a little on therms like dns server <yourprovider> and then you're likely to find the primary and secondary address soon.

However, I find it strange that the autoconfiguration of dns doesn't work. Have you tried to ping ip addresses / browse to ip addresses, and did that work as it should?

---

### Post by robert_pectol on 2009-01-22
```

cat /etc/resolv.conf

```
Should get you what you need.

---

### Post by curiousnoob on 2009-01-22
Thanks, I was able to find the DNS but for some reason it still does not work.  
The Wii can see the Router and I have put in the WEP key and it connects to the router but the router seems to stop it for some reason.  
Not sure what is going on.

---

