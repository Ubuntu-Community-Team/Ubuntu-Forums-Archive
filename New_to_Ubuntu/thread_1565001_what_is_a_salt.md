---
title: "what is a salt"
date: 2010-08-31
forum: New to Ubuntu
---

### Post by newport_j on 2010-08-31
What is password / hash salt. I thought that I could learn what it is by checking context when it is used. I cannot so what is it?
 
James Yunker

---

### Post by Bachstelze on 2010-08-31
A salt is used to add some randomness the hash. If you don't add some salt, the same password will always hash to the same value, which makes it vulnerable to collision attacks.

---

### Post by Bachstelze on 2010-08-31
Details: [http://en.wikipedia.org/wiki/Salt_%28cryptography%29](http://en.wikipedia.org/wiki/Salt_%28cryptography%29)

---

