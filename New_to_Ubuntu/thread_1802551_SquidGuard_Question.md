---
title: "SquidGuard Question"
date: 2011-07-12
forum: New to Ubuntu
---

### Post by NigelAtHome on 2011-07-12
Hello,
 
This is the first time I have ever posted a question on a forum. If this is not the correct forum let me know where I should be asking this question!
 
I am using Ubuntu with Squid as a transparent proxy. Thats working well. I also use SquidGuard to block undesirable content. Thats also working well.
 
I have configured SquidGuard to force all google searches into Safe Mode searches. 
 
I would like to do the same for YouTube searches/Views. Here is the code I used for google. Is there an equivalent for youtube?
 
rewrite google {
s@safe=images@safe=strict@ir
s@safe=off@safe=strict@ir
[email]s@http://froogle.google.com/froogle_advanced_search.*@http://froogle.com[/email]@i
[email]s@(.*.google[/email]..*)(/imghp\?&hl)@imghp?&safe=strict&hl@ir
[email]s@(.*.google..*)(.safe.off[/email])@images?&safe=strict&@ir
[email]s@(.*.google[/email]..*)(/images\?tab)@images?&safe=strict&tab@ir
[email]s@(.*.google[/email]..*)(/images\?q)@images?&safe=strict&q@ir
[email]s@(.*.google[/email]..*)(/images\?as_q)@images?&safe=strict&as_q@ir
[email]s@(.*.google[/email]..*)(/images\?hl)@images?&safe=strict&hl@ir
[email]s@(.*.google[/email]..*)(/search\?hl)@search?&safe=strict&hl@ir
[email]s@(.*.google[/email]..*)(/search\?as_q)@search?&safe=strict&as_q@ir
[email]s@(.*.google[/email]..*)(/news\?t)@news?&safe=strict&t@ir
[email]s@(.*.google[/email]..*)(/news\?hl)@news?&safe=strict&h1@ir
[email]s@(.*.google[/email]..*)(/froogle\?tab)@froogle?&safe=strict&tab@ir
[email]s@(.*.google[/email]..*)(/froogle\?q)@froogle?&safe=strict&q@ir
# log google
}

---

### Post by Vishal Agarwal on 2011-07-16
Can you Pl post your config files. i wanted to do the same; but couldn't.

---

