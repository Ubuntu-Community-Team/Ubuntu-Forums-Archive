---
title: "fish shell - Export &amp; History"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by tomehb on 2008-12-19
Hi Guys,

Within bash i use the following command to download updates via the proxy

*export http_proxy=http://tomb:mypassword@proxy:3128*

Just wondering if i can do this for fish? as the command does not exist?


Also does anyone know how to get a list of history instead of using pageup etc...

Cheers

Tom

---

### Post by tomehb on 2008-12-22
Bump

---

### Post by cronholio on 2009-03-16
Your history is in ~/.config/fish/fish_history and you can use set -x instead of export.

See also: [http://fishshell.org/wiki/moin.cgi/BashToFish](http://fishshell.org/wiki/moin.cgi/BashToFish)

---

