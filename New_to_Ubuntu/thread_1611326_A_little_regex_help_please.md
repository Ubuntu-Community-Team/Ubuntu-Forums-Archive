---
title: "A little regex help please"
date: 2010-11-01
forum: New to Ubuntu
---

### Post by mistypotato on 2010-11-01
Hi,

I'm trying to get a regex expression that will find the word select, Select or SELECT in a string

This hasn't worked

**^.*\b(select|Select|SELECT)\b.***

Can anyone see why?

thx

---

### Post by kpk09 on 2010-11-01
Your regexp looks right to me, but maybe it does not do what you wish :
```
echo "toto SELECT titi" | perl -ne 'print if /^.*\b(select|Select|SELECT)\b.*/'
echo "toto select titi" | grep -P '^.*\b(select|Select|SELECT)\b.*' 
```
this works perfectly well for me.

But why don't you try something simpler like */select/i* which is a case insensitive search ?
```
echo "toto seleCttiti" | grep -i "select"
echo "toto SELECT titi" | perl -ne 'print if /select/i'
```

Of course, the way you write your regexp (or wrap it up) depends on the program you use, as you can see the difference in my examples between grep and Perl. What you wrote is a Perl regexp, therefore do not forget the "-P" when calling grep.

---

