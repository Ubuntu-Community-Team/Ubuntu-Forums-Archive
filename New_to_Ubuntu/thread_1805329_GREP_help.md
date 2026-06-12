---
title: "GREP help"
date: 2011-07-15
forum: New to Ubuntu
---

### Post by Mattlanuze on 2011-07-15
Hi all, first of all i am brand new to Linux so please be gentle :)

I am trying to use grep as a filter on a txt file and need to to somehow randomise the command {N,M}

i have got so far as to filter strings containing 6 digits in a row using ```
grep -Pv '\d{6,}'
``` but like i say i need to search for a digits in a random sequence.

I hope someone can help cos am well sick of google adverts lol

Thanks in advance

---

### Post by papibe on 2011-07-15
Could you give us an example?

For what I understand, this would do it:
```
$ grep -e "[[:digit:]]\+"
```
It matches any line with a sequence of numbers (of at least 1 digit).

Is that what you're looking for?

Regards.

---

### Post by Mattlanuze on 2011-07-15
sorry if i didn't explain correctly

this is what i am trying to do

22232223abcde - no match (contains 8 digits)
223a222b3321a - no match (contains 10 digits)
abc123cba321a - match (contains 6 digits)

as you can see my previous attempt would have not matched on the last example above because the digits are not in sequence, i need a match on any line that contains 6 digits or less regardless of whether they are in sequence

hope that clears things lol

---

### Post by aktiwers on 2011-07-15
Just curious.. what do you need that for Mattlanuze? :)

---

### Post by Mattlanuze on 2011-07-15
Its to attempt to work out (or try to work out) the possible permutations of a given length string (in my case 13) but with added parameters (in my case 6 digits or less). Kind of a weekend project from the office and the winner gets browny points hehe

---

### Post by papibe on 2011-07-16
> **Mattlanuze said:**
> ...the winner gets browny ...
Are those "special" brownies? Can I get some?  ...just kidding :P

I think this would do it:
```
$ grep -w -e "[[:digit:]]\{1,6\}"
```
The expression means a sequence of digits as small as 1 and no longer than 6.
The -w options help your separate the sequence as a word, so it simplifies the expression if the match occurs at the beginning or the end of a line.

BTW: your request looks like a homework, walks like a homework, so it is probably a homework, right? Maybe not, but usually people here in the community try to avoid giving exact answers to this questions.

But since you are new... and I like brownies... there you go.

Regards.

---

### Post by Mattlanuze on 2011-07-16
Hmmm, no brownies for anyone just yet...

i ran what u suggested against the following test lines:

22232223aa
222322bbff
2223aabbff
2aaccebbff

alas, no matches where there should be 2 right?

---

### Post by Vaphell on 2011-07-16
```
test=$'22232223abcde\n223a222b3321a\nabc123cba321a\nabc12abcabcab\na1bcd1ef1fddd'

echo "$test"
22232223abcde
223a222b3321a
abc123cba321a
abc12abcabcab
a1bcd1ef1fddd


echo "$test" | grep -Ew '[^0-9]*([0-9][^0-9]*){1,6}'
abc123cba321a
abc12abcabcab
a1bcd1ef1fddd

```

---

