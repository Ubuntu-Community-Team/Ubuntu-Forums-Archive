---
title: "Why does gnome task manager say programs are using more ram then under totals?"
date: 2011-08-13
forum: New to Ubuntu
---

### Post by cosmoshell on 2011-08-13
[IMG]http://i.imgur.com/1p8o8.png[/IMG]


[IMG]http://imgur.com/lq40O.png[/IMG]

does this have something to do with encrypted home partition?
how can i fix this?

---

### Post by NightwishFan on 2011-08-13
I would shrink the screenshots a bit but I get what is going on. That is virtual memory which is probably the total allocated memory of the process including shared memory and cache. You want memory not virtual memory to get a more human readable view of what programs are using. You can change that under system monitor preferences.

[https://secure.wikimedia.org/wikipedia/en/wiki/Virtual_memory](https://secure.wikimedia.org/wikipedia/en/wiki/Virtual_memory)
[https://secure.wikimedia.org/wikipedia/en/wiki/Cache](https://secure.wikimedia.org/wikipedia/en/wiki/Cache)
[https://secure.wikimedia.org/wikipedia/en/wiki/Shared_memory](https://secure.wikimedia.org/wikipedia/en/wiki/Shared_memory)
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

