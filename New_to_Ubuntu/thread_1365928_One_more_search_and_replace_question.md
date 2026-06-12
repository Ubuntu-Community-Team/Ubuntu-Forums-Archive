---
title: "One more search and replace question"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by djbushido on 2009-12-27
I'm trying to do a search and replace (duh) on one file. I'm want to replace all instances of quality="[some multi-digit number]" with quality="1000". Trying to do a s&r with quality="*" isn't working out so well. Any ideas?

---

### Post by mobilediesel on 2009-12-27
> **djbushido said:**
> I'm trying to do a search and replace (duh) on one file. I'm want to replace all instances of quality="[some multi-digit number]" with quality="1000". Trying to do a s&r with quality="*" isn't working out so well. Any ideas?

If you're using sed, this will work:
```
sed 's/\(quality="\)[^"]*/\11000/'
```

---

### Post by djbushido on 2009-12-28
Okay, I can use sed or vim, whatever. The problem is that there is a period (.) in these numbers (forgot to mention that, sorry), so that isn't working correctly. The regex "." matches anything, so not sure how to change the sed command. Thank you so much for the help!

---

### Post by mobilediesel on 2009-12-28
> **djbushido said:**
> Okay, I can use sed or vim, whatever. The problem is that there is a period (.) in these numbers (forgot to mention that, sorry), so that isn't working correctly. The regex "." matches anything, so not sure how to change the sed command. Thank you so much for the help!

```
[COLOR="Blue"]sed 's/[/COLOR][COLOR="Green"]\(quality="\)[/COLOR][COLOR="Red"][[:digit:]|.]\+[/COLOR][COLOR="Blue"]/[/COLOR][COLOR="Green"]\1[/COLOR][COLOR="Red"]1000[/COLOR][COLOR="Blue"]/'[/COLOR]
```


That should do it. I tried to color code it to keep the parts separate.

---

### Post by djbushido on 2009-12-29
Thanks! That fixed it. And I really need to learn regex. And sed.

---

### Post by mobilediesel on 2009-12-29
> **djbushido said:**
> Thanks! That fixed it. And I really need to learn regex. And sed.

When I first looked at regex I thought my brain would melt! Every time I discover something new (to me) in Linux, I wonder why the heck I used Windows for so long. Nearly every time I try to solve some add problem in Linux, I find someone had already done it many years ago.

Here is a good site for more about sed:
[http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html)

---

### Post by djbushido on 2009-12-29
Nice. Appreciate it, but I think that regex with vim will prove a bit more useful later (vim on windows). 
PS: Did somebody say [regular expressions]("http://xkcd.com/208/")?

---

### Post by mobilediesel on 2009-12-29
> **djbushido said:**
> Nice. Appreciate it, but I think that regex with vim will prove a bit more useful later (vim on windows). 
PS: Did somebody say [regular expressions]("http://xkcd.com/208/")?

I haven't really worked with vim. I'll have to go through some tutorials as I still consider myself new to Linux although I installed Ubuntu a year and a half ago.

xkcd has to be my favorite webcomic!

---

