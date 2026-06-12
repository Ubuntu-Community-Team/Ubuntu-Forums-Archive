---
title: "Simple problem with bash and passing variables ...."
date: 2010-12-27
forum: New to Ubuntu
---

### Post by honeybear on 2010-12-27
Here is the program code:

```

echo "String1"
read STRING1
echo "String2"
read STRING2
for i in *
do j=`echo $i | sed 's/$STRING1/$STRING2/g'`
mv "$i" "$j" 
done
```

this is not working :( somehone knows why?

---

### Post by Crusty Old Fart on 2010-12-27
honeybear:

I can imagine more than one reason why you say it's not working. However, I'm having a hard time trying to figure out what you want it to do. So, I'll take a wild guess.

One problem is that the sed substitution argument was placed in between single quotes ('), which prevented expansion of the variables: $STRING1 and $STRING2. The use of double quotes ("), instead of single quotes, will allow variable expansion to occur in the sed argument. 
```

***[COLOR=Red]~~~ Change this: ~~~[/COLOR]***
do j=`echo $i | sed 's/$STRING1/$STRING2/g'`

***[COLOR=Green]~~~ To this: ~~~[/COLOR]***
do j=`echo $i | sed "s/$STRING1/$STRING2/g"`

```If that doesn't do what you want, please tell us exactly what you're trying to do with this script.

If I was writing this code, I would use $() instead of those annoying, itty-bitty backticks. I hate those little bastards, especially when they are adjacent to single quotes. I would also protect against redefining any internal shell environment variables by not using upper case letters in my variable names. And then, there are my preferences for the code layout:
```

#!/bin/bash

echo "String1"
read -e string1

echo "String2"
read -e string2

for i in *; do
  j=$(echo $i | sed "s/$string1/$string2/g")
  mv "$i" "$j"
done

exit 0

```

---

### Post by Crusty Old Fart on 2010-12-28
Bumped after some fairly significant editing.

---

### Post by mobilediesel on 2010-12-28
I would guess that you're trying to rename files based on a pattern. Rename is better for that:
```
rename -v 's/string1/string2/' *
```
you would just type what strings you want changed from/to
the **-v** makes rename let you know what it changed, if anything. Use **-n** first so it will tell you what it *would* change so you know it's only changing what you want.

---

