---
title: "Text file searchin Using Python"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by randika on 2010-10-18
I'm stuck middle of a program.I want to import a text file to a python program and search it like Google search.
Ex : if i type "Ub", I wan to show all possibilities like "Ubuntu","Kubuntu"... which are the words are in side the text file i use.

So far I have imported the text file and tried to use the "re" module but can't find a way to do so.

here is the code i have used so far

import re 

openFile = open ("divx.txt","r")
readFile = openFile.read()

search = raw_input ("What is the name of the movie? ")
pattern = r"b\%s\b" % search
cheack = re.compile (pattern ,re.IGNORECASE)
result = cheack.search(search,readFile)

print result

but this doesn't meat my needs.Please help..
Thank you for your time for reading this.

---

### Post by KIAaze on 2010-10-21
You might want to ask here instead:
[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

And here are a few python regex tutorials:
[http://diveintopython.org/regular_expressions/index.html](http://diveintopython.org/regular_expressions/index.html)
[http://gnosis.cx/publish/programming/regular_expressions.html](http://gnosis.cx/publish/programming/regular_expressions.html)
[http://www.developertutorials.com/tutorials/python/advanced-python-topics-050706-1060/](http://www.developertutorials.com/tutorials/python/advanced-python-topics-050706-1060/)

I fixed your code a little bit, so it works at least.
It will find exact words because of the "\b" you used in the reular expression, i.e. if you search for "hello", it will match "hello", but not "huhello" or "hellohu".

search_example.py:
```
#!/usr/bin/env python
import re

openFile = open ("divx.txt","r")
readFile = openFile.read()

searchstr = raw_input ("What is the name of the movie? ")
pattern = r"\b%s\b" % searchstr
#print "pattern=\n", pattern
check = re.compile (pattern ,re.IGNORECASE)
#print "searchstr=\n",searchstr
#print "readFile=\n",readFile
#print "check=\n", check
result = check.search(readFile)

if result:
        print 'found match:'
        print result.group()
else:
        print 'no match found'
#print result

```

divx.txt:
```
hello world
bye earth
python is here
hello earth
buy more
huhello
hellohu

```

---

### Post by randika on 2010-10-21
Thanks for your help.I'm sorry I posted this in wrong section.I'm new to programing and web.I will not make the same mistake again.Thank you again.

---

