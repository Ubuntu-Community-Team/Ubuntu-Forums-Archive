---
title: "_ in domain"
date: 2007-02-21
forum: Networking &amp; Wireless
---

### Post by involutaryhaxor on 2007-02-21
I was wondering if anyone knows about this aside from the problems that I have been having. I have a greatestjournal and if I want to view my blog, It won't work because I get pointed to __narusegawa__.greatestjournal.com. I have noticed that the reason that firefox "can't find the server" is because of the underscores, I have never had this problem under windows, any ideas?

Thanks

---

### Post by Jussi Kukkonen on 2007-02-21
Could be that Firefox is following the standard: The underscore is not an allowed character in a domain name (at least a non-internationalized one). Only letters, numbers and hyphens are allowed. Additionally, the name must start with a letter.

EDIT: actually the rules I mentioned apply to every "label" (every part separated by a dot) of a domain name

---

### Post by involutaryhaxor on 2007-02-21
im sorry, its --narusegawa--.greatestjournal.com

---

### Post by Jussi Kukkonen on 2007-02-22
Still, a label shouldn't start with a hyphen:> 
The labels must follow the rules for ARPANET host names.  They must
start with a letter, end with a letter or digit, and have as interior
characters only letters, digits, and hyphen.

---

### Post by involutaryhaxor on 2007-02-22
seeing that it works in windows, do you know of any way that I could make it work with ubuntu? Is there maybe something that I could tell firefox or something else to ignore this and make this work?

---

