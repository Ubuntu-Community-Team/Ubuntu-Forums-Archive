---
title: "How to enter a directory in terminal"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by xenogia on 2009-08-19
Just wondering I would go about getting into a directory with a space in it in terminal

For example TEST DIRECTORY

If you do 

cd TEST DIRECTORY

it doesn't work, how do you go about getting into via terminal

---

### Post by zerhacke on 2009-08-19
You need to escape the space.

Try

cd test\ directory

Note the \.  It makes the next character in the line readable.

---

### Post by scorp123 on 2009-08-19
> **xenogia said:**
> ```
cd TEST DIRECTORY
```
it doesn't work Of course not. Because that looks like two commands. As the previous poster said, you'd need to "escape" the space. This means telling the shell "Naah, you don't need to interpret this, just take it and carry on".

Another easier to remember method would be to simply use quotation marks:
```
cd "TEST DIRECTORY"
```

That one will work too. Or do as I do and avoid using space. I prefer to use underscore _ instead. It's way faster than having to think about escape-backslashes or quotation marks all the time :)

---

### Post by Clorow on 2009-08-19
Yeah, a backslash signals to ignore the special meaning of the next character. In this case, the space has the special meaning of separating two arguments. If you ever need to actually type a backslash (e.g. a directory named with a backslash), then you need to type two backslashes. (confusing enough?)

An alternative way is:
```
cd "TEST DIRECTORY"
```

Double quotes will take everything inside it as one single argument. Single quotes do the same thing, but also block replacement of variables.

Basically:

[LIST]
[*]" blocks only the special meaning of a space
[*]' blocks the special meaning of everything ($, ., etc.)
[/LIST]

---

### Post by PGScooter on 2009-08-19
another commonly used solution:
type "test" and then press the tab, it should finish it for you, unless there are other directories with test at the beginning.

---

### Post by prshah on 2009-08-19
> **PGScooter said:**
> ...unless there are other directories with test at the beginning.

... in which case you can press TAB twice is rapid succession to get a list, then add a few characters and try pressing TAB (once / twice) again.

---

