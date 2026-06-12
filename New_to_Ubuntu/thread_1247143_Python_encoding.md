---
title: "Python encoding"
date: 2009-08-22
forum: New to Ubuntu
---

### Post by filifunk on 2009-08-22
I'm trying to save my first helloworld.py file and I get this using Kate as a text editor

 p, li { white-space: pre-wrap; }  You are trying to save a python file as non ASCII, without specifiying a correct source encoding line for encoding "utf-8"


when I go back to the save prompt there are a bunch of different choices under "encoding" Am I choosing the wrong one?  utf-8 is default.


I understand that this isn't exactly ubuntu, but it's beginning enough that I think plenty of you might know what is going on?  Thanks

---

### Post by oldfred on 2009-08-22
I think I had the same problem but I use geany. My solution was to add a second line I found in other examples like this:

#!/usr/bin/python
# -*- coding: utf-8 -*-

---

### Post by Penguin Guy on 2009-08-22
Python, unlike other programming languages, detects white space. Make sure that you have indented everything correctly and have not mixed spaces and tabs. Once you've fixed any indent issues, save and run. If it still doesn't work, post back here.

---

### Post by filifunk on 2009-08-22
print "hello world"   <---this is all I have...the prompt does ask me if I want to save nevertheless.

I saved it.  But it isn't working like if I typed it in the terminal and it would actually print "hello world."

---

### Post by oldfred on 2009-08-22
When you save a file you need the first two lines I showed above. I copied this into geany & it ran without problem within geany. I changed to the directory I saved it in and executed >python savedfilename.py

```
#!/usr/bin/python
# -*- coding: utf-8 -*-

print "hello world"
```

---

### Post by donkyhotay on 2009-08-22
> **oldfred said:**
> When you save a file you need the first two lines I showed above. I copied this into geany & it ran without problem within geany. I changed to the directory I saved it in and executed >python savedfilename.py

```
#!/usr/bin/python
# -*- coding: utf-8 -*-

print "hello world"
```

Actually you *can* leave out the 2 lines
```

print "hello world"

```
is a valid python program, you just need to specify python when running it otherwise bash won't recognize it like so
```

python ./nameofprogram.py

```
To make it easier to launch by having bash recognize you want to have
```

#!/usr/bin/python

```
as the first line of your program so that you can run it without specifying python. The 'coding' second line you have there I have never needed with any python program I've ever worked with. Personally if I was making a hello world I would have
```

#!/usr/bin/python

print "hello world"

```

---

