---
title: "Case Statements ???"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by IrishLad on 2010-03-12
Hey guys, this will really show just how noobie I am, I'm trying to figure out the case command, and have been trying to follow a book I have which gives this example

```
#!/bin/sh
echo “Is it morning? Please answer yes or no”
read timeofday
case “$timeofday” in
     yes) echo “Good Morning”;;
     no ) echo “Good Afternoon”;;
     y ) echo “Good Morning”;;
     n ) echo “Good Afternoon”;;
     * ) echo “Sorry, answer not recognized”;;
esac
exit 0

```the bit thats confussing me is 

read timeofday
case “$timeofday” in

what is timeofday? is it a file I have to create for it to read the yes, no etc from or what? I tried fiddlign with it but too no avail it always says in the terminal window "Sorry answer not recognised"

ANy help would be much appreciated.

---

### Post by patchwork on 2010-03-12
timeofday is a variable read from standard input.

---

### Post by IrishLad on 2010-03-12
Sweet the Book was wrong I thought something was going mad there, there was no qoute put around the possible choices of cases, it should have been this 

```
echo “Is it morning? Please answer yes or no”
read timeofday
echo "you answered $timeofday"
case “$timeofday” in
     "yes") echo “Good Morning”;;
     "no" ) echo “Good Afternoon”;;
     "y" ) echo “Good Morning”;;
     "n" ) echo “Good Afternoon”;;
     "*" ) echo “Sorry, answer not recognized”;;
esac
exit 0

```

---

### Post by IrishLad on 2010-03-12
> **patchwork said:**
> timeofday is a variable read from standard input.


Thanks man it starting to come to me now.

I'd give you rep if I knew how LOL

---

### Post by IrishLad on 2010-03-12
> **IrishLad said:**
> Sweet the Book was wrong I thought something was going mad there, there was no qoute put around the possible choices of cases, it should have been this 

```
echo “Is it morning? Please answer yes or no”
read timeofday
echo "you answered $timeofday"
case “$timeofday” in
     "yes") echo “Good Morning”;;
     "no" ) echo “Good Afternoon”;;
     "y" ) echo “Good Morning”;;
     "n" ) echo “Good Afternoon”;;
     "*" ) echo “Sorry, answer not recognized”;;
esac
exit 0

```

I was wrong this will only output whatever I type in, not the case reply :icon_frown:

---

### Post by kellemes on 2010-03-12
> **IrishLad said:**
> I was wrong this will only output whatever I type in, not the case reply :icon_frown:

```
case &#8220;$timeofday&#8221; in
```
should be
```
case "$timeofday" in
```
Check all your quotes..

---

### Post by IrishLad on 2010-03-12
> **kellemes said:**
> ```
case &#8220;$timeofday&#8221; in
```should be
```
case "$timeofday" in
```Check all your quotes..


Your the Man, or Woman depending lol I would never have noticed that cheers. works just fine for me now.

---

### Post by kellemes on 2010-03-12
> **IrishLad said:**
> Your the Man, or Woman depending lol I would never have noticed that cheers. works just fine for me now.

man ;-)

---

