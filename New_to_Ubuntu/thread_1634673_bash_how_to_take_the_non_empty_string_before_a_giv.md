---
title: "bash: how to take the non empty string before a given string?"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by honeybear on 2010-11-30
Hi, 

here is the issue into the script using cut :( 
```
var="the is a sentence that is variable and the value VARIABLE1 6783458 is passed into the line"
# I want to output 6783458, but it is not working :( 
echo "$var" | cut -d "the value VARIABLE1" -f1
```

Somebody knows how to make it work? The sentence can vary but will always have the structure "the value VARIABLE1" to get the variable value (6783458, not necereally an integer, but it can be another single reference/word )

---

### Post by Brandon Williams on 2010-12-01
```
var="the is a sentence that is variable and the value VARIABLE1 6783458 is passed into the line"
num="${var##* VARIABLE1 }"  # strips the leading part of the string
num="${num%% *}"            # strips the trailing part
```

For more information, 'man bash' and search for the heading "Parameter Expansion".

---

### Post by TSJason on 2010-12-01
I like awk myself

```
echo $var |awk -FVARIABLE1\  '{print $2}' |awk '{print $1}'
```

---

### Post by honeybear on 2010-12-02
thanks a lot

I have to test it if it is too compatible with SH (not bash)

---

### Post by Brandon Williams on 2010-12-02
Both methods are POSIX compatible, and so should work with /bin/sh (a.k.a. dash) as well as bash.

---

### Post by honeybear on 2010-12-05
thanks a lot !

btw

```
var="/home/john/Desktop" ; num="${var##* / }"  ; num="${num%% *}" ; echo $num

```

this solution is visibly not wokring with single chars, no?

---

### Post by DaithiF on 2010-12-05
> **honeybear said:**
> thanks a lot !

btw

```
var="/home/john/Desktop" ; num="${var##* / }"  ; num="${num%% *}" ; echo $num

```this solution is visibly not wokring with single chars, no?

you don't say what you're trying to extract from the variable in this case.  One of the following?

```
$ var="/home/john/Desktop" ; num="${var##*/}"; echo $num
Desktop

$ var="/home/john/Desktop" ; num="${var#/*/}"; num=${num%/*}; echo $num
john

$ var="/home/john/Desktop" ; num="${var#/}"; num=${num%%/*}; echo $num
home

```

---

### Post by honeybear on 2010-12-05
> **DaithiF said:**
> you don't say what you're trying to extract from the variable in this case.  One of the following?

```
$ var="/home/john/Desktop" ; num="${var##*/}"; echo $num
Desktop

$ var="/home/john/Desktop" ; num="${var#/*/}"; num=${num%/*}; echo $num
john

$ var="/home/john/Desktop" ; num="${var#/}"; num=${num%%/*}; echo $num
home

```

wow that's cool. That's really impressive.

---

