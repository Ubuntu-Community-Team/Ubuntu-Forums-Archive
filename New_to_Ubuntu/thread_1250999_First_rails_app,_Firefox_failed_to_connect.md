---
title: "First rails app, Firefox failed to connect"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by modernist on 2009-08-27
Hi all, I am the textbook-case of a newbie: I installed Ubuntu next to Windows in a flash (first time Linux user), then installed Rails (that was a bit trickier but got it right anyway) and then when I started the server (Webrick), I got the error message in Firefox:

Failed to Connect

Firefox can't establish a connection to the server at 127.0.0.1:3000.

Though the site seems valid, the browser was unable to establish a connection.

...

Can anyone help me as to what could be wrong? It is probably some configuration problem, but I cant find any good leads to the solution on Google.

Thanks in advance!!

z

---

### Post by Hospadar on 2009-08-27
Are you sure the server is running and you have the right port?

You might try wget-ing it (wget localhost:3000) and see what you get, maybe it's some weird quirk with firefox.  Also I'm not familiar with webrick, but perhaps you need to set up some content or point yourself at a sub-folder (localhost:3000/index or something).

Alternatively it is possible the server is just not working, I'd go see if they have any tutorials or functional programs (if you haven't done so already) you can grab and try to run to see if it's something wrong with your program or something else.

Furthermore, why aren't you using python?  ;-)

---

### Post by wizard10000 on 2009-08-27
Is the webserver listening on port 3000?

---

