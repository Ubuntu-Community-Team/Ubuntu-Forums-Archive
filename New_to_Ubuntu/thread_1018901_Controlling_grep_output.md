---
title: "Controlling grep output"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by spencewah on 2008-12-22
Not sure if grep is the right tool for this, but here we go:

I have some output like 

A: blah blah blah
B: so and so and so
C: etc etc etc

A: blah blah blah2
B: so and so and so2
C: etc etc etc2

...

and I want to reformat it so that it grabs the values from A and the values from C and prints it nicely on a line, something like this:

blah blah blah: etc etc etc
blah blah blah2: etc etc etc2

...

Can you use grep to do this?  Not really sure where to start.

Thanks!

---

### Post by IamReck on 2008-12-22
I suggest you look at the man pages for grep

just type man grep into terminal, you will find plenty of information.

---

### Post by spencewah on 2008-12-22
So you're confirming that this can all be done in grep?  Or that I should spend an hour scouring the man pages for how to do this only to discover that it can't be done?

---

### Post by IamReck on 2008-12-22
I have no idea if it can be done.  Sound like a homework question to me also so I am suggesting that you look at the man pages, which you should have done before you even came here asking questions.

When you go on the man pages, you will find your answer in the first paragraph.

P.S. I have no idea what program would do this for you.

---

### Post by spencewah on 2008-12-22
Well you've certainly been a treat.

---

### Post by handydan918 on 2008-12-22
Heh. Some folks think any cli question is homework...
I don't know how to do what you want to do, but I know a few of the tools that will do that sort of thing. As you said, grep, as well as sed and awk. 

Man them all.

---

### Post by unutbu on 2008-12-22
If you had to do this with shell commands, also take a look at 'paste'. Or you could do it in python:
[PHP]#!/usr/bin/env python
import sys
contents=sys.stdin.read()
a_list=[line for line in contents.split('\n') if line.startswith('A:')]
c_list=[line for line in contents.split('\n') if line.startswith('C:')]
for a_text,c_text in zip(a_list,c_list):
    print '%s: %s'%(a_text[3:],c_text[3:])
[/PHP]
Make the script executable:
```
chmod +x test.py
```

Call it like this:
```

cat output_file | test.py
```

```

% cat test.in
A: blah blah blah
B: so and so and so
C: etc etc etc

A: blah blah blah2
B: so and so and so2
C: etc etc etc2
% cat test.in | test.py
blah blah blah: etc etc etc
blah blah blah2: etc etc etc2
```

---

