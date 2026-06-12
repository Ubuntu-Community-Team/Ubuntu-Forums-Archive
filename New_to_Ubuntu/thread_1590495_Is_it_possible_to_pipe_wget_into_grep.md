---
title: "Is it possible to pipe wget into grep?"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by bubbla on 2010-10-07
I'm back, still trying to navigate the mystical world of the command terminal.  I am trying to count the number of times the word Philippines appears on the Wikipedia page for it.  I tried:

```
wget -q -O- http://en.wikipedia.org/wiki/Philippines | 
grep -c 'Philippines' http://en.wikipedia.org/wiki/Philippines 
```I just get the response ```
grep: [http://en.wikipedia.org/wiki/](http://en.wikipedia.org/wiki/)Philippines : Input/output error
```Why oh why?

---

### Post by alphacrucis2 on 2010-10-08
> **bubbla said:**
> I'm back, still trying to navigate the mystical world of the command terminal.  I am trying to count the number of times the word Philippines appears on the Wikipedia page for it.  I tried:

```
wget -q -O- http://en.wikipedia.org/wiki/Philippines | 
grep -c 'Philippines' http://en.wikipedia.org/wiki/Philippines 
```I just get the response ```
grep: [http://en.wikipedia.org/wiki/](http://en.wikipedia.org/wiki/)Philippines : Input/output error
```Why oh why?


Shouldn't it just be:

```
wget -q -O- http://en.wikipedia.org/wiki/Philippines | 
grep -c Philippines

```


Edit: When I do that it tells me that Philippines occurs 409 times on the page

---

### Post by bubbla on 2010-10-08
Thank you, that works perfectly!  The only odd thing is that I got 352.  Why would we get different numbers?  :???:

---

### Post by LinksPatrocinados on 2010-10-08
Thanks, i has the same problem, and this solution worked as a charm!

---

### Post by alphacrucis2 on 2010-10-08
> **bubbla said:**
> Thank you, that works perfectly!  The only odd thing is that I got 352.  Why would we get different numbers?  :???:

The difference is because I cheated:). I just typed Philipp. The word Philippine without the s occurs many times on that page. When I add the letters ines to the grep search string I get 352.

---

### Post by bubbla on 2010-10-08
> **alphacrucis2 said:**
> The difference is because I cheated:). I just typed Philipp. The word Philippine without the s occurs many times on that page. When I add the letters es to the grep search string I get 352.Ah, that makes sense then. ;)


However, while I was googling around trying to figure out why we would get different results, I discovered that -c is no good because it only counts *how many lines* have the word Phillipines.  To count how many times the word occurs (including when it occurs more than once on the same line), I changed it to

```
wget -q -O- http://en.wikipedia.org/wiki/Philippines |  grep -o Philippines | wc -l
```which returns 881.

But I wouldn't have got the syntax for the piping without you, alpha, so thank you!

---

