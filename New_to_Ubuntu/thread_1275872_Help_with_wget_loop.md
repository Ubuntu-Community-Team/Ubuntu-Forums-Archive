---
title: "Help with wget loop"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by SpinningAround on 2009-09-26
I'm trying to download files from this webpage [http://ia311035.us.archive.org/1/items/MIT18.01JF07/](http://ia311035.us.archive.org/1/items/MIT18.01JF07/) using a loop, the thing is that it looks like there is two problems, first the $i fail (unsure why) also the counting is wrong. I would like it to count 01,02,...,10 but instead does it count 01,2,3,4,...,10.

the loop
```
for ((i=01; i<35 ;i++)) ; do wget http://ia311035.us.archive.org/1/items/MIT18.01JF07/ocw-18.01-f07-lec$i_300k.mp4 ; done

```

what I guess is that wget looks for $i_300k.mp4 instead of only $i, have i done some easy misstake or do I need to download them one by one?

Btw. what is best mp4 or ogv?

---

### Post by lloyd_b on 2009-09-26
> **SpinningAround said:**
> I'm trying to download files from this webpage [http://ia311035.us.archive.org/1/items/MIT18.01JF07/](http://ia311035.us.archive.org/1/items/MIT18.01JF07/) using a loop, the thing is that it looks like there is two problems, first the $i fail (unsure why) also the counting is wrong. I would like it to count 01,02,...,10 but instead does it count 01,2,3,4,...,10.

the loop
```
for ((i=01; i<35 ;i++)) ; do wget http://ia311035.us.archive.org/1/items/MIT18.01JF07/ocw-18.01-f07-lec$i_300k.mp4 ; done

```

what I guess is that wget looks for $i_300k.mp4 instead of only $i, have i done some easy misstake or do I need to download them one by one?

Btw. what is best mp4 or ogv?

First, to get those leading zeroes, use the "printf" shell command.  For example, "i2=$(printf %02d $i)" will take the value of "i", format it as two places with a leading zero if required, and store the result in "i2".

Second, the shell is having a problem interpreting your variable.  Specifically, where you're using "$i", it *thinks* you're referencing a variable named "$i_300k".  You can get around this with some strategic use of quotation marks.

Finally, instead of the loop that you're using, I'd suggest a very simple bash alternate: "for i in {1..35}; do" iterates through the set of integers from 1 to 35.  Your loop will work, but I find the above a lot easier to understand.

Merging all of these:```
for i in {1..35}; do i2=$(printf %02d $i); FILE="http://ia311035.us.archive.org/1/items/MIT18.01JF07/ocw-18.01-f07-lec"$i2"_300k.mp4"; wget $FILE; done
```should give you the results you want.

Lloyd B.

---

### Post by SpinningAround on 2009-09-26
Thanks :D Worked flawlessly

---

