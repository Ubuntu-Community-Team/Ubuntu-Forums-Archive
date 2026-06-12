---
title: "sed or awk?"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by Rayve on 2010-01-30
I had an issue some time ago with a (Windows) word program giving me some fits, and ultimately, it did some strange converting with some of my documents.  There is an extra space *everywhere*, i.e., there is one space between every letter and three spaces between each word... also, the & sign turns up instead of any elipses (...).  I've tried going through and doing it by hand, but when it's pages and pages long, it drives me crazy.  Now that I've discovered Linux, I'm hoping one of the awesome tools can make it easier for me.

I've only started reading about sed and awk and I'm not sure which would be more appropriate.  I'm thinking of something like 
```

sed 's/{ }{3}/{ }{1}/g' < inputfile > outputfile

```

but I think I'm confusing the two programs.

Any clues? :)  Thanks!

---

### Post by gate on 2010-01-30
Close. Here is what I would do:

cat inputfile | sed 's/\([^\s]\)\s/\1/g' > outputfile


the streaming stuff is irrelevant. what you need is the regular expression.

what it does is find any non-whitespace character, followed by a whitespace character and replaces the found item with just the non-whitespace character. 

sed and the like being awesome tools built on the fantastic world of regular expressions, there will be many, many right ways of doing it.

---

### Post by Rayve on 2010-01-30
gate,

The output was darn near perfect.  Thanks!! :)

---

### Post by DaithiF on 2010-01-30
> **gate said:**
> 
cat inputfile | sed 's/\([^\s]\)\s/\1/g' > outputfile

why use cat here?  sed on its own does just fine...
```
sed 's/\([^\s]\)\s/\1/g' inputfile > outputfile
```
or, to make changes in-place to the inputfile
```
sed -i 's/\([^\s]\)\s/\1/g' inputfile
```

---

### Post by gate on 2010-01-30
I use cat simply because most of the time I am not doing one sed manipulation. So it is not uncommon for me to use cat | grep | sed | sed or some bizarre combination thereof. 

Like I said in my earlier post, many right ways.

---

