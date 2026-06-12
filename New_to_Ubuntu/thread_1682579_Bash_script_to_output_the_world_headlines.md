---
title: "Bash script to output the world headlines ?"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by honeybear on 2011-02-06
Hello

Would be great to output that. Someone could make such script?


Thank you in advance!
Cheers

---

### Post by Joe of loath on 2011-02-06
[http://fxfeeds.mozilla.com/en-US/firefox/headlines.xml](http://fxfeeds.mozilla.com/en-US/firefox/headlines.xml)

Then find a program/write a script which will output the headlines as text.

---

### Post by honeybear on 2011-02-06
> **Joe of loath said:**
> [http://fxfeeds.mozilla.com/en-US/firefox/headlines.xml](http://fxfeeds.mozilla.com/en-US/firefox/headlines.xml)

Then find a program/write a script which will output the headlines as text.

thanks 

```

 html2text rss.xml\?edition\=int  | grep -v www | grep -v "<?xml version=" | grep -v href | grep -v http | grep -v rss  | grep -v GMT |     head -n 30

```

---

