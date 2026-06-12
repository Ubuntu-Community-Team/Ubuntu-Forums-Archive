---
title: "backticks vs parenthasis in shell scripts"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by CharlesA on 2010-10-03
I'm trying to understand what advantage using parenthesis instead of backticks and vice verse are.

I've always used backticks, but I'd like to know if there is any advantage to using parenthesis instead.

Thanks.

[Source]("http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_04.html").

---

### Post by v8YKxgHe on 2010-10-03
Always use $() vs `` if you can. There are many advantages for using $(), one of them being far far easier way to nest them, see [http://mywiki.wooledge.org/CommandSubstitution](http://mywiki.wooledge.org/CommandSubstitution) and [http://mywiki.wooledge.org/BashFAQ/082](http://mywiki.wooledge.org/BashFAQ/082)

That site is great for Bash common pitfalls and references like this. The same goes for always use [[ instead of [ if you can.

---

### Post by CharlesA on 2010-10-03
Thanks! That helps a bit.

---

