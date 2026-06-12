---
title: "Quick question about wget"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by mathfreak123 on 2009-09-19
Hey, linux newb here! I was looking through the man pages of wget, and I noticed the "--level" option. I think "level" means the number of links to follow in a file I'm downloading with wget to download additionally. e.g. If level is set to 2, and I download a file called example1.html, which has a link to example2.html, would I download example1.html and example2.html?

---

### Post by falconindy on 2009-09-19
Yep, you can shorten that up to just `-l 2` as well. In conjunction with any recursive retrieval options, you need to use -r. Recursion with wget isn't limited to just following links, however. It'll grab almost any reference it finds. Doing a single level depth on [www.google.com]("http://www.google.com") pulls down all the following files:
```
./index.html
./services/index.html
./language_tools?hl=en
./intl/en/about.html
./intl/en/privacy.html
./intl/en/ads/index.html
./intl/en/options/index.html
./intl/en_ALL/images/logo.gif
./prdhp?hl=en&tab=wf
./robots.txt
./accounts/Login?hl=en&continue=http:%2F%2Fwww.google.com%2F
./advanced_search?hl=en
```It is nice enough to form its own directory for this mess, though.

---

### Post by mathfreak123 on 2009-09-19
Ok, thanks for clarifying! Glad to know what level does to recursive downloading.

---

