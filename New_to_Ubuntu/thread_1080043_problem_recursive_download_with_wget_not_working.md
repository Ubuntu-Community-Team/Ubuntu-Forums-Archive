---
title: "problem: recursive download with wget not working"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by jmd9qs on 2009-02-25
hi all,

i have been trying to download this website: [http://www.linux.org/lessons/interm/index.html](http://www.linux.org/lessons/interm/index.html). it is a intermediate "course" on linux, if any are interested... i've found it to be pretty cool, so i wanted to wget it for offline viewing. here's the code i tried:

```
wget -r http://www.linux.org/lessons/interm/index.html 
```

and the response:

```
--2009-02-24 22:52:13--  http://www.linux.org/lessons/interm/index.html
Resolving www.linux.org... 198.182.196.56
Connecting to www.linux.org|198.182.196.56|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `www.linux.org/lessons/interm/index.html'

    [ <=>                                   ] 15,047      75.5K/s   in 0.2s    

2009-02-24 22:52:13 (75.5 KB/s) - `www.linux.org/lessons/interm/index.html' saved [15047]

Loading robots.txt; please ignore errors.
--2009-02-24 22:52:13--  http://www.linux.org/robots.txt
Connecting to www.linux.org|198.182.196.56|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `www.linux.org/robots.txt'

    [ <=>                                   ] 885         --.-K/s   in 0s      

2009-02-24 22:52:14 (61.7 MB/s) - `www.linux.org/robots.txt' saved [885]

FINISHED --2009-02-24 22:52:14--
Downloaded: 2 files, 16K in 0.2s (80.0 KB/s)

```

i thought that was WAAAY to fast, so i checked the output file... sure enough, it was only the index.html.

i've used wget for this before, and it worked perfectly... why isn't this working right? any ideas?

---

### Post by x33a on 2009-02-25
> **jmd9qs said:**
> `[www.linux.org/robots.txt](www.linux.org/robots.txt)' saved [885]

FINISHED --2009-02-24 22:52:14--
Downloaded: 2 files, 16K in 0.2s (80.0 KB/s)

linux.org doesn't allow it's content to be downloaded. see the contents of the file robots.txt.

[http://en.wikipedia.org/wiki/Robots_Exclusion_Standard](http://en.wikipedia.org/wiki/Robots_Exclusion_Standard)

---

### Post by jmd9qs on 2009-02-25
well... guess that clears that question up! thank you x33a for your quick answer.

i guess i'll just e-mail them and beg for a copy!


THREAD SOLVED

---

### Post by x33a on 2009-02-25
if you do get a copy, please share it with me. i also learnt about their download policy the hard way :D

---

### Post by jmd9qs on 2009-02-25
will do bro... keep an eye on this thread for a few days. i just sent them and e-mail. hopefully they'll help me out!

either way, i'll let you know. thanks again for the help.

jmd9qs

---

