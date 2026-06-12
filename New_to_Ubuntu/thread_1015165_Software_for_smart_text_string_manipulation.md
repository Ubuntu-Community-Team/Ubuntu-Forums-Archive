---
title: "Software for smart text string manipulation?"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by persofi on 2008-12-18
Hi,

I would like to know if there is a program under ubuntu that can do the following stuff, or if it is possible to write a script that does it:

Search in a .ltx file for every string where the "§" character is followed by some numbers like "123", then "SPACE" and then not followed by a letter like "S".

It's for a law article I'm writing, where most of stuff should look like "§123 SGB", while §123S GB or §123 GB" are typos.

---

### Post by annda on 2008-12-18
i recommend kate - if what you have is a latex ltx file that can be opened in a text editor.

all you need to do is use regular expressions in the search function. for example, you can hit CTRL+F and enter the following pattern to be found as a regular expression (there is a drop-down list) and check the "highlight all" and "match case" checkboxes - after all, sGB is a typo too and should be caught.

[B]§[ ]?[0-9]+[a-z,A-Z]*\ (?!SGB|BGB)
[/B]
this will highlight all the instances where "**$**" is followed directly or after a space (**[ ]?**) by one or more digits (**[0-9]+**), then by 0 or more letters (**[a-z,A-Z]***), then a space (**\ **), and then finally by something that is not a correct name of any of the law codes that you mention in your paper ( **(?!SGB|BGB)** ). you can use more names separated by "|" if you need to.

take a look here if you want to go deeper:
[http://www.regular-expressions.info/tutorialcnt.html](http://www.regular-expressions.info/tutorialcnt.html)

you will still have to correct the errors by hand (probably too many options for a script), but at least you will be able to find them at a glance.

---

### Post by handydan918 on 2008-12-18
Kind of a learning curve here, but if you have hundreds or thousands of these corrections to make, it may make sense to look at ```
man sed
``` 
```
man grep
```

and 

```
man awk
```

---

### Post by hailukah on 2008-12-18
I second using sed, though it can seem a bit tricky.  Here's a handy list I always use when working with sed.  Almost everything I've needed to do has been possible with these [sed one liners]("http://student.northpark.edu/pemente/sed/sed1line.txt").

---

