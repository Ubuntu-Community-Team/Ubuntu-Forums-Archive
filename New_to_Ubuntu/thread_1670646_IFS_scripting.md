---
title: "IFS scripting"
date: 2011-01-19
forum: New to Ubuntu
---

### Post by stamoulohta on 2011-01-19
hi to all.

I couldn't, for some reason, post an new thread in the "development" section so i posted it here. feel free to move it around ;)

I'm new to bash scripting but i try, mainly for educational purposes, to make a script for assigning the corrected name of a file (backslashes before spaces) to a variable so it can be fed to a command line argument. 

my code isn't anywhere near working!! so i would like a bit of help!

Method No.1

```
IFS="
"
for space_file in $(find * -type f); do
	cool_file=
	IFS="\*" ### here i know i miss the correct escape char for "every char"

	for char_check in "$space_file"; do
#	echo character "$char_check" # test

		if [ "$char_check" = " " ];  then 
			char_check="\ "
		fi 
		cool_file=$(echo $cool_file$char_check)
	done
	echo $cool_file
done

unset IFS
```

Method No.2

```
IFS="
"
for space_file in $(find * -type f); do
	cool_file=
	unset IFS
	for char_check in "$space_file"; do
		
		cool_file="$cool_file\\$char_check"
# if this worked i know that i will have to "tail" out the last char. 
	done
	echo  $cool_file
done

unset IFS

```

So, is Method No.1 going to work if i set IFS to each and every character and whow do i do that?
and, why Method No.2 just adds a "\" in th beginning of the file???

please please help!
g.

---

### Post by dracayr on 2011-01-19
In method 2, do 
```
for char_check in $space_file; do
		cool_file="$cool_file\\ $char_check"
```
instead of 
```
for char_check in "$space_file"; do
		cool_file="$cool_file\\$char_check"
```
(remove the Quotes)
It will still write the backslash at the beginning of the filename, however. That should be easily removed with sed.

EDIT: dammit, what is it with this double-posting?! Is it because of the site?

---

### Post by dracayr on 2011-01-19
In method 2, do 
```
for char_check in $space_file; do
		cool_file="$cool_file\\ $char_check"
```
instead of 
```
for char_check in "$space_file"; do
		cool_file="$cool_file\\$char_check"
```
(remove the Quotes)
It will still write the backslash at the beginning of the filename, however. That should be easily removed with sed.

---

### Post by dracayr on 2011-01-19
In method 2, do 
```
for char_check in $space_file; do
		cool_file="$cool_file\\ $char_check"
```
instead of 
```
for char_check in "$space_file"; do
		cool_file="$cool_file\\$char_check"
```
(remove the Quotes)
It will still write the backslash at the beginning of the filename, however. That should be easily removed with sed.

---

### Post by sisco311 on 2011-01-19
Check out:
[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)
and
[http://mywiki.wooledge.org/BashFAQ/020](http://mywiki.wooledge.org/BashFAQ/020)

---

### Post by stamoulohta on 2011-01-19
Thank you both for your answers!!

i got it! this is how it looks now:
```
#!/bin/bash

IFS="
"
for space_file in $(find * -type f); do
	cool_file=
	unset IFS
	for char_check in $space_file; do
		
		cool_file="$cool_file\\ $char_check"

	done
	echo  $cool_file | sed 's/\\//'
done

unset IFS

exit

```

I'll mark it as [SOLVED] so others can see but I would like (out of curiosity) Method No.1 corrected by someone if he could, 

and some help for making shed substitute all the occurrences and not just the first one.

example:
```
echo "my name is george" | sed 's/ /\\ /'

my\ name is george
```

but i want
```
echo "my name is george" | sed '??????'

my\ name\ is\ george
```

Thank you all once more.

PS: @dracayr, it is the sites problem... read an announcement somewhere.

---

### Post by stamoulohta on 2011-01-19
Thank you both for your answers!!

i got it! this is how it looks now:
```
#!/bin/bash

IFS="
"
for space_file in $(find * -type f); do
	cool_file=
	unset IFS
	for char_check in $space_file; do
		
		cool_file="$cool_file\\ $char_check"

	done
	echo  $cool_file | sed 's/\\//'
done

unset IFS

exit

```

I'll mark it as [SOLVED] so others can see but I would like (out of curiosity) Method No.1 corrected by someone if he could, 

and some help for making shed substitute all the occurrences and not just the first one.

example:
```
echo "my name is george" | sed 's/ /\\ /'

my\ name is george
```

but i want
```
echo "my name is george" | sed '??????'

my\ name\ is\ george
```

Thank you all once more.

PS: @dracayr, it is the sites problem... read an announcement somewhere.

---

### Post by stamoulohta on 2011-01-19
Thank you both for your answers!!

i got it! this is how it looks now:
```
#!/bin/bash

IFS="
"
for space_file in $(find * -type f); do
	cool_file=
	unset IFS
	for char_check in $space_file; do
		
		cool_file="$cool_file\\ $char_check"

	done
	echo  $cool_file | sed 's/\\//'
done

unset IFS

exit

```

I'll mark it as [SOLVED] so others can see but I would like (out of curiosity) Method No.1 corrected by someone if he could, 

and some help for making shed substitute all the occurrences and not just the first one.

example:
```
echo "my name is george" | sed 's/ /\\ /'

my\ name is george
```

but i want
```
echo "my name is george" | sed '??????'

my\ name\ is\ george
```

Thank you all once more.

PS: @dracayr, it is the sites problem... read an announcement somewhere.

---

