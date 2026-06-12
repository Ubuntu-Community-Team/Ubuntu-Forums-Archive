---
title: "Regular expressions in terminal"
date: 2011-03-31
forum: New to Ubuntu
---

### Post by Dasha21 on 2011-03-31
Hi everyone!

I have a problem trying to use regular expressions in Ubuntu terminal. I need to rename a large group of files with similar names: scan001.bmp, scan002.bmp... etc into 001.bmp, 002.bmp...

everything works fine if I type this 
[COLOR=Navy]mv scan001.bmp 001.bmp[/COLOR]

but it will take half a year to rename all 500 filess, so I want ro do this by one command using reg exp:
[COLOR=Navy] mv &quot;scan&quot;(.*)&quot;.bmp&quot; \1&quot;.bmp&quot;[/COLOR]
but there is an error: 
[COLOR=Navy]bash: syntax error near unexpected token `('[/COLOR]

but regular expressions work normally without brackets, for example if I type 
[COLOR=Navy]mv &quot;scan&quot;*&quot;001.bmp&quot; 001.bmp[/COLOR] 

so, the probem is particularly with brackets.

Does enyone know the solution? Please, help me.

---

### Post by DaithiF on 2011-03-31
do this instead:
```
rename 's/^scan//' scan*.bmp

```

bash doesn't support regular expressions in the way you are expecting ... you can't capture a term in parentheses and resuse it later in your command as \1 in bash ... unlike, (say) python, perl, sed, etc...

---

### Post by Dasha21 on 2011-03-31
> **iamthe1who said:**
> I had a similar problem. Took me a while but got there in the end!
I'll see if I can find the link.

EDIT: Here it is: [http://goo.gl/4rvkT](http://goo.gl/4rvkT)
stop spamming in my thread!

admin, ban him please

---

### Post by Dasha21 on 2011-03-31
> **DaithiF said:**
> do this instead:
```
rename 's/^scan//' scan*.bmp

```bash doesn't support regular expressions in the way you are expecting ... you can't capture a term in parentheses and resuse it later in your command as \1 in bash ... unlike, (say) python, perl, sed, etc...
thanks, Ill try now


fantastic! it worked!!
thank you very much!!

---

### Post by Dasha21 on 2011-03-31
:ks

---

