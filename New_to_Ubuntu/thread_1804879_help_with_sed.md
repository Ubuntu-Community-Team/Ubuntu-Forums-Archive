---
title: "help with sed"
date: 2011-07-15
forum: New to Ubuntu
---

### Post by Avidanborisov on 2011-07-15
I need to use sed to scan the stdout for new lines that start with a number and end with an : and replace them with nothing and then output back to stdout. For example if I have this:
```
TEXT:
{
TEXTTEXT65:
}
TEXT
1:
23:
14:
45:
TEXT("32:",)
998:
ANOTHERTEXT

```
It will replace it with that:
```
TEXT:
{
TEXTTEXT65:
}
TEXT
TEXT("32:",)
ANOTHERTEXT
```

---

### Post by Grenage on 2011-07-15
Like so?

```
sed 's/^[0-9].*:$//g' FILENAME
```

---

### Post by Avidanborisov on 2011-07-15
> **Grenage said:**
> Like so?

```
sed 's/^[0-9].*:$//g' FILENAME
```

The problem is that won't remove the lines with the numbers but will leave them blank.

---

### Post by Grenage on 2011-07-15
> **Avidanborisov said:**
> The problem is that won't remove the lines with the numbers but will leave them blank.

You can delete the lines with '/d' I think:

```
sed '/^[0-9].*:$/d' FILENAME >> OUTPUT
```

---

### Post by gmargo on 2011-07-15
You could also do it easily with **grep(1)**.  Same pattern applies:
```

grep -v '^[0-9].*:$'

```

---

### Post by mikejonesey on 2011-07-15
or you can add `echo "\013"` to your sed search criteria, but i too would use grep on this one :)

---

### Post by Avidanborisov on 2011-07-17
Thanks for all the suggestions! But actually now I see that I need something a bit more complicated. Now I need to use sed to scan the stdout for lines that start with a number and end with an : and if there is something after them (not including spaces or tabs) remove only them, and if there isn't, remove all the line and then send it back to stdout. For example if I have this:

```
TEXT:
{
TEXTTEXT65:
}
TEXT1
1:
23: 
14:TEXT2
45: TEXT3
TEXT("32:",)
998:
ANOTHERTEXT
```
replace it with
```
TEXT:
{
TEXTTEXT65:
}
TEXT1
TEXT2
TEXT3
TEXT("32:",)
ANOTHERTEXT
```
Note that after 23: it has a space but it still should remove the whole line and in 45: it also should remove the space before TEXT3

---

### Post by Avidanborisov on 2011-07-17
actually it doesn't have to be particularly sed, it can also be any other program that you know how to achieve this in it.

---

### Post by mikejonesey on 2011-07-17
```
egrep -v "^([0-9]*):( $|$)" | sed 's/^[0-9]*://; s/^ //'
```or

```
egrep -v "^([0-9]*):( $|$)" | sed -r 's/^[0-9]*:(| )//'
```or

```
grep -E -v "^([0-9]*):( $|$)" | sed -r 's/^[0-9]*:(| )//'
```

depends how you want to do the regular expression, or if you want to simplify just go without the regex n keep pipeing...

code explained;

use grep (-v with regex to remove lines you don't want);

^ = must begin with

([0-9]*)=any number (100,23,15345) for example

: = must have colun sign next

( $|$)= must end after the colon or end after colon space

then to remove the code at front of line without removing the line (sed/awk);

sed with regular expression;

^ = must begin with

[0-9]* = any number

: = colon

(| )= nothing or space

:)

---

### Post by Avidanborisov on 2011-07-17
Thank you very much! worked like charm!

---

