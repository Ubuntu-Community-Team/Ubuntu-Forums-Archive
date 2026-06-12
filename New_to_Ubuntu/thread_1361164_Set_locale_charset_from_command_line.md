---
title: "Set locale charset from command line"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by humphreybc on 2009-12-21
Hi,

I'm using AjaXplorer on my Ubuntu server and the diagnostics pass everything EXCEPT for the locale:

"You must set a correct charset encoding in your locale definition in the form: en_us.UTF-8. Please refer to setlocale man page. If your detected locale is C, please check [http://www.ajaxplorer.info/documentation/chapter-8-faq/#c87](http://www.ajaxplorer.info/documentation/chapter-8-faq/#c87). Detected locale: C (using UTF-8)"

The link goes nowhere. Here the man page for setlocale:
[http://manpages.ubuntu.com/manpages/gutsy/man3/setlocale.3.html](http://manpages.ubuntu.com/manpages/gutsy/man3/setlocale.3.html)

But I'm still not sure how to change my system over the en_us.UTF-8

Can someone help?

---

### Post by hugmenot on 2009-12-21
I think you can edit /etc/default/locale. Not sure what the canonical way is.

---

